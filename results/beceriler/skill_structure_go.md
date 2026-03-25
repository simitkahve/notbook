# Go (Golang) AI Agents: Structure, Frameworks, and Best Practices

A comprehensive research document on building AI agents in Go.

---

## 1. Go-Based AI Agent Frameworks

The Go ecosystem has matured significantly for building AI agents. Here's a curated list of the most relevant frameworks:

### 1.1 LangChainGo (`tmc/langchaingo`)

The most popular Go port of LangChain. Provides comprehensive LLM integrations and agent building blocks.

```bash
go get github.com/tmc/langchaingo
go get github.com/tmc/langchaingo/llms/openai
go get github.com/tmc/langchaingo/llms/anthropic
```

**Key Features:**
- 10+ LLM providers (OpenAI, Anthropic, Google, AWS, Ollama, etc.)
- Composable chain architecture
- Vector store integrations (Pinecone, MongoDB, Weaviate, Chroma, Qdrant)
- Memory management (buffer, summary, entity memory)
- Autonomous agents with ReAct pattern

### 1.2 LangGraphGo (`smallnest/langgraphgo`)

Builds on langchaingo to provide graph-based workflow orchestration. Includes 85+ examples.

```bash
go get github.com/smallnest/langgraphgo/prebuilt
```

**Key Features:**
- StateGraph for building agent workflows
- Tool execution with schema support
- Streaming support for real-time feedback
- Listeners for observability
- Pre-built agent patterns

### 1.3 Google ADK (`google/adk-go`)

Enterprise-grade toolkit for building multi-agent systems.

```bash
go get github.com/google/adk-go
```

**Key Features:**
- Multi-agent orchestration with hierarchical delegation
- Agent2Agent (A2A) protocol for agent communication
- MCP (Model Context Protocol) toolbox integration
- Google Cloud native (Vertex AI, Cloud Run)
- Production-grade concurrency

### 1.4 Firebase Genkit

Rapid prototyping framework with production-ready AI features.

```bash
go get github.com/firebase/genkit-go
go get github.com/firebase/genkit-go/plugins/googleai
```

**Key Features:**
- Unified generation API across providers
- Native vector database support
- Structured output & function calling
- Hot-reload development server
- One-command deployment to Cloud Run

### 1.5 Eino (`cloudwego/eino`)

ByteDance's high-scale production framework.

```bash
go get github.com/cloudwego/eino
```

**Key Features:**
- ReAct agents with built-in error handling
- Circuit breakers and retry policies
- 10,000+ requests/second throughput
- CloudWeGo ecosystem integration (Hertz, Kitex)

### 1.6 Jetify AI SDK

Multi-provider abstraction with automatic failover.

```bash
go get github.com/jetify-com/ai
go get github.com/jetify-com/ai/providers/openai
```

**Key Features:**
- Unified interface across providers
- Automatic failover and health checking
- Type-safe request/response
- Idiomatic Go design

---

## 2. Agent Prompting Patterns in Go

### 2.1 Basic LLM Call

The foundation — simple prompt/response:

```go
llm, err := openai.New(
    openai.WithBaseURL("https://api.deepseek.com"),
    openai.WithToken(os.Getenv("API_KEY")),
    openai.WithModel("deepseek-chat"),
)

resp, err := llm.Call(ctx, "Your prompt here")
```

### 2.2 Structured Output

Return parseable JSON using `ResponseFormatJSON` and JSON Schema:

```go
// Set JSON response format
llm, _ := openai.New(
    openai.WithResponseFormat(openai.ResponseFormatJSON),
)

// Generate schema from Go struct
reflector := jsonschema.Reflector{DoNotReference: true}
schema := reflector.Reflect(&MyStruct{})
schemaString, _ := json.Marshal(schema)

// Include schema in prompt
promptTemplate := prompts.NewPromptTemplate(
    "{{.input}}\nReturn JSON matching: {{.schema}}",
    []string{"input", "schema"},
)
prompt, _ := promptTemplate.Format(map[string]any{
    "input":  "Process this data",
    "schema": schemaString,
})

resp, _ := llm.Call(ctx, prompt)
var result MyStruct
json.Unmarshal([]byte(resp), &result)
```

### 2.3 Defining Tools with Custom Schemas

The `ToolWithSchema` interface enables structured tool input:

```go
// Input struct with JSON schema tags
type TodoItem struct {
    Title       string           `json:"title"`
    Description string           `json:"description,omitempty"`
    Priority    TodoItemPriority `json:"priority" jsonschema:"enum=low,enum=normal,enum=high,default=normal"`
    DueDate     *time.Time       `json:"due_date,omitempty" jsonschema:"description=Due date in ISO 8601"`
}

// Tool implementation
type SaveTodoItemsTool struct{}

func (t *SaveTodoItemsTool) Name() string        { return "save_todo_items" }
func (t *SaveTodoItemsTool) Description() string { return "Save todo items to database" }

func (t *SaveTodoItemsTool) Schema() map[string]any {
    r := &jsonschema.Reflector{ExpandedStruct: true}
    schema := r.Reflect(&SaveTodoItemsInput{})
    data, _ := json.Marshal(schema)
    var schemaMap map[string]any
    json.Unmarshal(data, &schemaMap)
    return schemaMap
}

func (t *SaveTodoItemsTool) Call(ctx context.Context, input string) (string, error) {
    var req SaveTodoItemsInput
    if err := json.Unmarshal([]byte(input), &req); err != nil {
        return "", err
    }
    // Process items...
    return "Saved successfully", nil
}
```

**Critical:** Always use `ExpandedStruct: true` when generating tool schemas. Without it, the reflector produces `$ref`-based schemas that LLM APIs don't understand.

### 2.4 System Messages for Agent Behavior

Guide agent behavior with system messages:

```go
runnable, _ := prebuilt.CreateAgentMap(llm, tools, 10,
    prebuilt.WithSystemMessage(
        "You must call get_current_date_time first to get the current date, "+
        "then extract todo items and save them.",
    ),
)
```

### 2.5 ReAct Agent Pattern

Reasoning + Acting — agents that think before acting:

```go
agent := flow.NewReActAgent(
    flow.WithModel(model.NewChatModel("gpt-4")),
    flow.WithTools(
        tool.NewSearchTool(),
        tool.NewCalculatorTool(),
    ),
    flow.WithMaxIterations(10),
    flow.WithRetryPolicy(flow.ExponentialBackoff),
)

result, err := agent.Execute(ctx, flow.Request{Input: "Your task"})
```

---

## 3. Best Practices for Go AI Skills

### 3.1 Schema Generation

Use `invopop/jsonschema` for generating JSON schemas from Go structs:

```go
import "github.com/invopop/jsonschema"

reflector := jsonschema.Reflector{
    DoNotReference: true,    // Inline types instead of $ref
    ExpandedStruct: true,    // Root must be "type": "object"
}
schema := reflector.Reflect(&MyStruct{})
```

**Useful jsonschema tags:**

| Tag | Effect | Example |
|-----|--------|---------|
| `enum=a,enum=b` | Restricts values | `jsonschema:"enum=low,enum=high"` |
| `default=x` | Sets default | `jsonschema:"default=normal"` |
| `description=...` | Field description | `jsonschema:"description=ISO 8601 date"` |

### 3.2 Workflow vs. Agent: When to Use Which

| Approach | Use When |
|----------|----------|
| **Workflow (Graph)** | Steps are known and fixed; you need explicit control over execution path; want observability per step |
| **Agent** | Execution path is dynamic; you want LLM to reason about what to do; task is open-ended |

**Workflow example:**
```go
g := graph.NewListenableStateGraph[map[string]any]

g.AddNode("summarize", "Summarize email", summarizeNode)
g.AddNode("extract", "Extract todo items", extractNode)

g.AddEdge("summarize", "extract")
g.AddEdge("extract", graph.END)
g.SetEntryPoint("summarize")

runnable, _ := g.CompileListenable()
result, _ := runnable.Invoke(ctx, initialState)
```

**Agent example:**
```go
runnable, _ := prebuilt.CreateAgentMap(llm, tools, 10,
    prebuilt.WithSystemMessage("Instructions for the agent"),
)
state := map[string]any{
    "messages": []llms.MessageContent{
        llms.TextParts(llms.ChatMessageTypeHuman, "User request"),
    },
}
resp, _ := runnable.Invoke(ctx, state)
```

### 3.3 Defensive Type Handling

LLMs produce sloppy output. Build defensive parsing:

```go
type FlexibleDate time.Time

func (f *FlexibleDate) UnmarshalJSON(b []byte) error {
    var s string
    if err := json.Unmarshal(b, &s); err != nil {
        return err
    }
    for _, layout := range []string{
        time.RFC3339,
        "2006-01-02T15:04:05Z",
        "2006-01-02T15:04:05",
        "2006-01-02",
    } {
        if t, err := time.Parse(layout, s); err == nil {
            *f = FlexibleDate(t)
            return nil
        }
    }
    return fmt.Errorf("invalid date: %q", s)
}
```

### 3.4 Provider Abstraction

Use OpenAI-compatible interfaces for flexibility:

```go
// The openai package works with any OpenAI-compatible API
llm, _ := openai.New(
    openai.WithBaseURL("https://api.deepseek.com"),  // or Ollama, Azure, etc.
    openai.WithToken(os.Getenv("API_KEY")),
    openai.WithModel("deepseek-chat"),
)
```

### 3.5 Error Handling

Follow Go conventions with proper error wrapping:

```go
response, err := client.Chat(ctx, request)
if err != nil {
    return fmt.Errorf("chat failed: %w", err)
}
```

### 3.6 Observability

Use listeners and streaming for debugging:

```go
// Streaming events
runnable, _ := g.CompileListenable()
events := runnable.Stream(ctx, initialState)
for event := range events {
    fmt.Printf("Event: %v\n", event)
}

// Listeners
g.AddGlobalListener(&EventLogger{})
```

### 3.7 Multi-Provider Failover

For production reliability:

```go
client := ai.NewClient(
    ai.WithProviders(
        providers.OpenAI("gpt-4"),      // Primary
        providers.Anthropic("claude-3"), // Fallback
    ),
    ai.WithAutoFailover(true),
    ai.WithHealthCheck(30),
)
```

---

## 4. Quick Reference Cheat Sheet

### Install Popular Frameworks

```bash
# LangChainGo
go get github.com/tmc/langchaingo

# LangGraphGo
go get github.com/smallnest/langgraphgo/prebuilt

# Google ADK
go get github.com/google/adk-go

# Firebase Genkit
go get github.com/firebase/genkit-go

# Jetify AI SDK
go get github.com/jetify-com/ai

# Schema generation
go get github.com/invopop/jsonschema
```

### Basic Patterns Summary

| Pattern | Key Code |
|---------|----------|
| LLM Call | `llm.Call(ctx, prompt)` |
| Structured Output | `openai.WithResponseFormatJSON` + schema in prompt |
| Simple Tool | Implement `Name()`, `Description()`, `Call()` |
| Tool with Schema | Add `Schema()` method with `jsonschema.Reflector` |
| Create Agent | `prebuilt.CreateAgentMap(llm, tools, maxIterations)` |
| Workflow Graph | `graph.NewListenableStateGraph`, `AddNode`, `AddEdge` |

---

## 5. Resources

- [LangChainGo GitHub](https://github.com/tmc/langchaingo)
- [LangGraphGo Examples](https://github.com/smallnest/langgraphgo)
- [Google ADK](https://github.com/google/adk-go)
- [Firebase Genkit](https://firebase.google.com/docs/genkit)
- [Eino](https://github.com/cloudwego/eino)
- [invopop/jsonschema](https://github.com/invopop/jsonschema)

---

*Generated: 2026-03-25*
