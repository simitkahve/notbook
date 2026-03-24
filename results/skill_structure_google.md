# Google Gemini/Gemma Skill Structure & Prompting Guide

Research findings on how Google structures their Gemini/Gemma skills and prompts.

---

## 1. Gemini's Skill Definition Format

### Agent Skills (Open Standard)

Gemini CLI uses the **Agent Skills** open standard for defining skills. A skill is a **self-contained directory** that packages instructions and assets.

### Directory Structure

```
my-skill/
├── SKILL.md       (Required) Instructions and metadata
├── scripts/       (Optional) Executable scripts
├── references/    (Optional) Static documentation
└── assets/        (Optional) Templates and other resources
```

### SKILL.md Format

The core file uses **YAML frontmatter** for metadata + **Markdown** for instructions:

```markdown
---
name: code-reviewer
description:
  Use this skill to review code. It supports both local changes and remote Pull
  Requests.
---

# Code Reviewer

This skill guides the agent in conducting thorough code reviews.

## Workflow

### 1. Determine Review Target
- **Remote PR**: If the user gives a PR number or URL, target that remote PR.
- **Local Changes**: If changes are local...
```

**Metadata Fields:**
- `name`: Unique identifier (should match directory name)
- `description`: When to use this skill and what it does
- **Body**: Markdown instructions that guide agent behavior

### Discovery Tiers

Skills are discovered from:
1. **Workspace Skills**: `.gemini/skills/` or `.agents/skills/`
2. **User Skills**: `~/.gemini/skills/` or `~/.agents/skills/`
3. **Extension Skills**: Bundled within installed extensions

### Activation Flow

1. **Discovery**: At session start, skill name + description injected into system prompt
2. **Activation**: When task matches skill description, agent calls `activate_skill` tool
3. **Consent**: User approves skill activation
4. **Injection**: SKILL.md body + directory added to context
5. **Execution**: Skill guidance prioritized for session duration

---

## 2. Google's Agent Prompting Approach

### Gemma Formatting (Control Tokens)

Gemma uses specific **control tokens** for role delineation:

| Token | Purpose |
|-------|---------|
| `<start_of_turn>user` | Indicates user turn |
| `<start_of_turn>model` | Indicates model turn |
| `<end_of_turn>` | End of dialogue turn |
| `\n` | Turn separator |

**Example:**
```
<start_of_turn>user
What is Cramer's Rule?<end_of_turn>
<start_of_turn>model
```

### System Instructions (Gemma-specific)

Gemma IT models **do not support** a separate system role. Instead, embed system-level instructions in the initial user prompt:

```
<start_of_turn>user
Only reply like a pirate.

What is the answer to life the universe and everything?<end_of_turn>
<start_of_turn>model
Arrr, 'tis 42,<end_of_turn>
```

### Gemini 3 Core Prompting Principles

- **Be precise and direct**: State goal clearly, avoid overly persuasive language
- **Use consistent structure**: Use XML-style tags (`<instructions>`, `<context>`) or Markdown headings
- **Define parameters**: Explicitly explain ambiguous terms
- **Control output verbosity**: Default is direct/efficient; specify if you need more detail
- **Prioritize critical instructions**: Place behavioral constraints in System Instruction or beginning of user prompt
- **Structure for long contexts**: Supply context first, instructions at the end
- **Anchor context**: Use transition phrases like "Based on the information above..."

### ReAct Prompting (for Gemma Agents)

For agentic workflows, Google uses **ReAct (Reasoning and Acting)** prompting:

```
Thought: I need to do something...
Action: I should use the tool `tool_name` with input `tool_input`

Wait user to get the result of the tool is `tool_output`

And finally answer...
```

**Progression:**
- **Zero-shot**: No examples
- **One-shot**: Single demonstration example
- **Few-shot**: 2-5 examples showing desired pattern

---

## 3. Best Practices for Gemini Agents

### Prompt Design Strategies

#### Clear & Specific Instructions
- Use question, step-by-step tasks, or complex user experience mapping
- Provide constraints (e.g., "Summarize in one sentence")
- Specify response format (table, bullet list, JSON, etc.)

#### Zero-shot vs Few-shot
- **Always prefer few-shot**: Prompts with examples are more effective
- Use specific, varied examples to narrow focus
- Ensure consistent formatting across examples (XML tags, whitespace, newlines)
- Avoid overfitting with too many examples

#### Add Context
- Include required information instead of assuming model knows it
- Reference external documents, code, or data explicitly

#### Break Down Complex Prompts
- **Sequential chaining**: Each step → next prompt's input
- **Aggregation**: Parallel tasks on different data portions

### Gemini 3 System Instruction Template

```markdown
You are Gemini 3, a specialized assistant for [Domain].
You are precise, analytical, and persistent.

# Process
1. **Plan**: Analyze task, create step-by-step plan
2. **Execute**: Carry out the plan
3. **Validate**: Review output against constraints
4. **Format**: Present in requested structure

# Constraints
- Verbosity: [Low/Medium/High]
- Tone: [Formal/Casual/Technical]

<output_format>
Structure your response as follows:
1. **Executive Summary**: [Short overview]
2. **Detailed Response**: [Main content]
</output_format>
```

### Agentic Workflow Configuration

When designing agent prompts, configure these dimensions:

**Reasoning & Strategy:**
- Logical decomposition depth
- Problem diagnosis depth (abductive reasoning)
- Information exhaustiveness

**Execution & Reliability:**
- Adaptability (strict vs. pivot on new data)
- Persistence (self-correction attempts)
- Risk assessment (reads vs. writes)

**Interaction & Output:**
- Ambiguity handling (assume vs. ask)
- Verbosity level
- Precision/completeness requirements

### Advanced System Instruction (for Complex Agents)

```markdown
You are a very strong reasoner and planner. Use these critical instructions:

Before taking any action, proactively, methodically, and independently plan:

1. **Logical Dependencies**: Analyze action against policy rules, prerequisites, order of operations
2. **Risk Assessment**: What are consequences? Will new state cause future issues?
3. **Abductive Reasoning**: Identify most logical reason for problems. Look beyond obvious causes
4. **Outcome Evaluation**: Does observation require plan changes?
5. **Information Availability**: Use all sources (tools, policies, history, user)
6. **Precision**: Verify claims by quoting exact applicable information
7. **Completeness**: Exhaustively incorporate all requirements
8. **Persistence**: Don't give up unless reasoning is exhausted
```

### Model Parameters

| Parameter | Guidance |
|-----------|----------|
| **Temperature** | Default 1.0 for Gemini 3 (changing may cause looping) |
| **Max Output** | ~60-80 words per 100 tokens |
| **topK** | Higher = more diverse, lower = more deterministic |
| **topP** | Default 0.95 |
| **Stop Sequences** | Use to halt generation at specific character sequences |

---

## Key Takeaways

1. **Skills = Directories with SKILL.md**: YAML frontmatter + Markdown body
2. **Gemma uses control tokens**: No system role; embed in initial user prompt
3. **Prefer few-shot**: Always include examples for better performance
4. **Use structured formats**: XML tags or Markdown for clear instruction/context separation
5. **ReAct for agents**: Thought → Action → Observation cycles
6. **Prioritize instructions**: Place critical constraints at the start
7. **Be precise**: Direct language, explicit parameters, clear goals

---

## References

- [Gemma formatting and system instructions](https://ai.google.dev/gemma/docs/core/prompt-structure)
- [Agent Skills | Gemini CLI](https://geminicli.com/docs/cli/skills)
- [Creating Agent Skills](https://geminicli.com/docs/cli/creating-skills/)
- [Prompt design strategies | Gemini API](https://ai.google.dev/gemini-api/docs/prompting-strategies)
- [Beyond the Chatbot: Agentic AI with Gemma](https://developers.googleblog.com/en/beyond-the-chatbot-agentic-ai-with-gemma)
- [Agent Skills Codelab](https://codelabs.developers.google.com/gemini-cli/how-to-create-agent-skills-for-gemini-cli)
- [Agent Skills Open Standard](https://agentskills.io/)