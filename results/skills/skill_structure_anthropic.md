# Anthropic Claude Code & MCP Skill Structure Research

This document describes how Anthropic structures their Claude Code skills and the Model Context Protocol (MCP).

---

## 1. Claude's Skill Definition Format

Skills are defined using a `SKILL.md` file with YAML frontmatter. The format is consistent across Claude Code, Claude API, and the Agent SDK.

### File Structure

```text
my-skill/
├── SKILL.md           # Main instructions (required)
├── template.md        # Template for Claude to fill in
├── examples/
│   └── sample.md      # Example output showing expected format
└── scripts/
    └── validate.sh    # Script Claude can execute
```

### SKILL.md Format

```yaml
---
name: skill-name
description: Brief description of what this Skill does and when to use it
---

# Your Skill Name

## Instructions
[Clear, step-by-step guidance for Claude to follow]

## Examples
[Concrete examples of using this Skill]
```

### Frontmatter Fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | No | Display name (max 64 chars, lowercase letters, numbers, hyphens only) |
| `description` | Recommended | What the skill does and when to use it |
| `argument-hint` | No | Hint for autocomplete |
| `disable-model-invocation` | No | Set to `true` to prevent auto-loading (manual invocation only) |
| `user-invocable` | No | Set to `false` to hide from `/` menu |
| `allowed-tools` | No | Tools Claude can use without permission |
| `model` | No | Model to use when skill is active |
| `context` | No | Set to `fork` for subagent execution |
| `agent` | No | Subagent type (Explore, Plan, general-purpose) |

### String Substitutions

| Variable | Description |
|----------|-------------|
| `$ARGUMENTS` | All arguments passed when invoking the skill |
| `$ARGUMENTS[N]` | Access specific argument by index |
| `$N` | Shorthand for `$ARGUMENTS[N]` |
| `${CLAUDE_SESSION_ID}` | Current session ID |
| `${CLAUDE_SKILL_DIR}` | Directory containing the skill |

### Dynamic Context Injection

Use `!`command`` syntax to run shell commands before skill content is sent:

```yaml
---
name: pr-summary
description: Summarize changes in a pull request
context: fork
agent: Explore
allowed-tools: Bash(gh *)
---

## Pull request context
- PR diff: !`gh pr diff`
- PR comments: !`gh pr view --comments`
- Changed files: !`gh pr diff --name-only`
```

---

## 2. MCP (Model Context Protocol) Structure

MCP is an open protocol for connecting AI assistants to external data sources and tools.

### Architecture

MCP uses JSON-RPC 2.0 messages to establish communication between:

- **Hosts**: LLM applications that initiate connections
- **Clients**: Connectors within the host application
- **Servers**: Services that provide context and capabilities

### Core Features

**Servers can offer:**
- **Resources**: Context and data for the AI model
- **Prompts**: Templated messages and workflows
- **Tools**: Functions for the AI model to execute

**Clients can offer:**
- **Sampling**: Server-initiated agentic behaviors
- **Roots**: Filesystem/URI boundary inquiries
- **Elicitation**: Requests for additional user information

### Security Principles

1. **User Consent and Control**: Users must explicitly consent to data access
2. **Data Privacy**: Hosts must obtain consent before exposing user data
3. **Tool Safety**: Tool descriptions are untrusted unless from a trusted server
4. **LLM Sampling Controls**: Users must approve any LLM sampling requests

### Implementation Guidelines

- Build robust consent and authorization flows
- Provide clear documentation of security implications
- Implement appropriate access controls
- Follow security best practices in integrations

---

## 3. Best Practices for Claude Agent Instructions

### Core Principles

1. **Concise is Key**
   - Only add context Claude doesn't already have
   - Challenge each piece of information
   - Keep SKILL.md under 500 lines

2. **Set Appropriate Degrees of Freedom**
   - **High freedom** (text-based): When multiple approaches are valid
   - **Medium freedom** (pseudocode/scripts): When a preferred pattern exists
   - **Low freedom** (specific scripts): When operations are fragile

3. **Test with All Models**
   - What works for Opus might need more detail for Haiku
   - Test with Haiku, Sonnet, and Opus

### Writing Effective Descriptions

- **Always write in third person** (injected into system prompt)
- Include both what the skill does AND when to use it
- Include specific trigger keywords

```yaml
# Good
description: Extract text and tables from PDF files, fill forms, merge documents. Use when working with PDF files or when the user mentions PDFs, forms, or document extraction.

# Bad
description: Helps with documents
```

### Progressive Disclosure Patterns

1. **High-level guide with references**: SKILL.md points to detailed files
2. **Domain-specific organization**: Separate files by domain
3. **Conditional details**: Show basic content, link to advanced

### Common Patterns

**Template Pattern:**
```markdown
## Report structure
ALWAYS use this exact template structure:
```markdown
# [Analysis Title]
## Executive summary
[One-paragraph overview]
...
```

**Examples Pattern:**
```markdown
## Commit message format
**Example 1:**
Input: Added user authentication
Output:
```
feat(auth): implement JWT-based authentication
```
```

**Workflow Pattern:**
```markdown
## Document modification workflow
1. Determine modification type:
   **Creating new content?** → Follow "Creation workflow"
   **Editing existing content?** → Follow "Editing workflow"
```

### Anti-Patterns to Avoid

- **Windows-style paths**: Use forward slashes (`scripts/helper.py`)
- **Too many options**: Provide a default with escape hatch
- **Time-sensitive info**: Use "Old patterns" section for deprecated info
- **Voodoo constants**: Justify all values in code

### Evaluation-Driven Development

1. Identify gaps: Run Claude without a Skill, document failures
2. Create evaluations: Build 3+ test scenarios
3. Establish baseline: Measure without the Skill
4. Write minimal instructions: Address only the gaps
5. Iterate: Test, compare, refine

---

## Summary

| Aspect | Format |
|--------|--------|
| **Skill Definition** | `SKILL.md` with YAML frontmatter |
| **Naming** | lowercase with hyphens (max 64 chars) |
| **Description** | Third person, specific triggers (max 1024 chars) |
| **File Loading** | Progressive disclosure (metadata → instructions → resources) |
| **MCP** | JSON-RPC 2.0 with servers providing tools/resources/prompts |
| **Best Practices** | Concise, test with all models, use workflows, avoid anti-patterns |

---

## References

- [Claude Code Skills Documentation](https://docs.anthropic.com/en/docs/claude-code/skills)
- [Agent Skills Overview](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview)
- [Skill Authoring Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices.md)
- [MCP Specification](https://modelcontextprotocol.io/specification/latest/)