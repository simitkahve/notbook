# OpenAI GPT Skill Structure Research

Research findings on how OpenAI structures GPTs, skills, and prompts.

---

## 1. GPT Configuration (ChatGPT Builder)

OpenAI's GPT Builder uses these main configuration fields:

### Core Fields

| Field | Purpose |
|-------|---------|
| **Name** | Title displayed in search results, GPT Store, and chat header |
| **Description** | Short summary explaining purpose, target users, and capabilities |
| **Conversation Starters** | Example prompts shown when opening the GPT |
| **Instructions** | Defines behavior, tone, structure, and decision-making rules |

### Instructions Best Practices (from OpenAI)

- Use explicit step structure: `"When X happens → do Y"`
- Separate sections with clear delimiters
- Prefer positive instructions (`"Do X"`) over prohibitions (`"Don't do Y"`)
- Include brief examples for specific outputs
- Use headings and lists for visual distinction
- Keep rules in instructions, reference material in Knowledge

### Additional Features

- **Knowledge**: Upload up to 20 files (512MB each) for reference material
- **Capabilities**: Web search, image generation, Canvas, Code Interpreter, Apps
- **Actions**: Connect to external APIs

---

## 2. Agent Skills (OpenAI API & Codex)

OpenAI's Agent Skills follow the **open Agent Skills standard** (originally from Anthropic, now multi-ecosystem).

### Directory Structure

```
skill-name/
├── SKILL.md          # Required: metadata + instructions
├── scripts/          # Optional: executable code
├── references/      # Optional: documentation
├── assets/          # Optional: templates, resources
└── agents/
    └── openai.yaml  # Optional: UI metadata & configuration
```

### SKILL.md Format

**Frontmatter (YAML) + Markdown body**

```markdown
---
name: skill-name
description: Explain exactly when this skill should and should not trigger.
license: Apache-2.0
metadata:
  author: example-org
  version: "1.0"
---

Skill instructions here...
```

### Required Frontmatter Fields

| Field | Constraints |
|-------|-------------|
| `name` | Max 64 chars, lowercase letters + hyphens only, no leading/trailing hyphens |
| `description` | Max 1024 chars, describe what it does AND when to use it |

### Optional Frontmatter Fields

- `license`: License name or reference to bundled license file
- `compatibility`: Environment requirements (e.g., "Requires Python 3.14+ and uv")
- `metadata`: Arbitrary key-value mapping
- `allowed-tools`: Space-delimited list of pre-approved tools

### Progressive Disclosure

OpenAI uses a 3-tier loading strategy for efficiency:

1. **Metadata** (~100 tokens): `name` + `description` loaded at startup
2. **Instructions** (< 5000 tokens recommended): Full `SKILL.md` body when skill activates
3. **Resources**: Files in `scripts/`, `references/`, `assets/` loaded only when needed

---

## 3. Codex-Specific Configuration

### agents/openai.yaml (Optional)

```yaml
interface:
  display_name: "Optional user-facing name"
  short_description: "Optional user-facing description"
  icon_small: "./assets/small-logo.svg"
  icon_large: "./assets/large-logo.png"
  brand_color: "#3B82F6"
  default_prompt: "Optional surrounding prompt"

policy:
  allow_implicit_invocation: false  # default: true

dependencies:
  tools:
    - type: "mcp"
      value: "openaiDeveloperDocs"
      description: "OpenAI Docs MCP server"
```

### Skill Invocation in Codex

- **Explicit**: Include skill in prompt, or use `$skill-name` / `/skills` command
- **Implicit**: Codex auto-invokes based on `description` matching the task

### Skill Locations

| Scope | Location | Use Case |
|-------|----------|----------|
| REPO | `.agents/skills` in CWD or repo root | Team-specific skills |
| USER | `$HOME/.agents/skills` | Personal skills across repos |
| ADMIN | `/etc/codex/skills` | Machine-wide default skills |
| SYSTEM | Built-in with Codex | Default skills (e.g., skill-creator) |

---

## 4. Best Practices for AI Agent Instructions

### From OpenAI's Documentation

1. **Be specific and concrete** — avoid vague instructions
2. **Use step-by-step structures** — especially for multi-step workflows
3. **Positive framing** — "Do X" over "Don't do Y"
4. **Include examples** — especially for classification or specific outputs
5. **Visual hierarchy** — use headings, lists, delimiters
6. **Separate concerns** — behavior in Instructions, reference in Knowledge

### From Codex Best Practices

1. Keep each skill focused on one job
2. Prefer instructions over scripts unless deterministic behavior needed
3. Write imperative steps with explicit inputs and outputs
4. Test prompts against descriptions to confirm trigger behavior
5. Keep main `SKILL.md` under 500 lines
6. Move detailed reference material to separate files

### Security Considerations

- Treat skills as privileged code — review before use
- Don't expose open skill repositories to end-users
- Integrate skills at developer level, not user-facing catalogs
- Require approval for sensitive/write actions

---

## 5. Summary: Key Fields & Structure

### GPT (ChatGPT Builder)
- Name, Description, Conversation Starters
- Instructions (behavioral rules)
- Knowledge (reference files)
- Capabilities (web search, code interpreter, etc.)
- Actions (API integrations)

### Agent Skill (SKILL.md)
- **Required**: `name`, `description`
- **Optional**: `license`, `compatibility`, `metadata`, `allowed-tools`
- **Body**: Markdown with instructions, examples, edge cases
- **Supporting dirs**: `scripts/`, `references/`, `assets/`

### Codex Optional Config
- `agents/openai.yaml` for UI metadata, invocation policy, tool dependencies

---

## References

- [OpenAI GPT Builder Help](https://help.openai.com/en/articles/8770868-gpt-builder)
- [OpenAI Skills API Docs](https://platform.openai.com/docs/guides/tools-skills)
- [Codex Agent Skills](https://developers.openai.com/codex/skills/create-skill)
- [Agent Skills Specification](https://agentskills.io/specification)
- [OpenAI Skills Repository](https://github.com/openai/skills)