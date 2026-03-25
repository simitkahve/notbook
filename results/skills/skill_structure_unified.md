# Unified Skill Format

Based on research from OpenAI, Anthropic, Google, and Go frameworks.

## Recommended Structure

```yaml
---
name: skill_name
description: What this skill does (1-2 lines)
version: 1.0.0
author: Your name
license: MIT
compatibility:
  - openai
  - anthropic
  - google
  - go
metadata:
  tags: [marketing, mobile, launch]
  complexity: intermediate
allowed-tools:
  - read
  - write
  - exec
---
```

## Core Sections

### 1. Overview
- What the skill does
- When to use it
- Target users

### 2. Key Facts
- Quick reference table
- Numbers, dates, metrics

### 3. The Process
- Step-by-step workflow
- Clear "When X → do Y" structure
- Numbered steps

### 4. Tools & Resources
- Links, tools, references

### 5. Examples
- Real-world scenarios
- Sample inputs/outputs

## Best Practices

| Practice | Source |
|----------|--------|
| **Positive instructions** over prohibitions | OpenAI |
| **Concise** descriptions | Anthropic |
| **Degrees of freedom** - don't over-constrain | Anthropic |
| **Few-shot examples** | Google |
| **Critical constraints at start** | Google |
| **Workflow graphs** for fixed paths | Go |
| **Provider abstraction** | Go |

## File Organization

```
skill_name/
├── SKILL.md           # Main skill file
├── scripts/           # Optional helper scripts
├── references/        # Detailed references
├── assets/            # Images, diagrams
└── examples/          # Example inputs/outputs
```

## Guidelines

1. **Keep SKILL.md under 500 lines** - move details to references
2. **One skill = one job** - focused, not monolithic
3. **Test with all models** - don't assume it works everywhere
4. **Progressive disclosure** - metadata at startup, full details on use
5. **Dynamic context injection** - use string substitutions for context

## References

- skill_structure_openai.md
- skill_structure_anthropic.md
- skill_structure_google.md
- skill_structure_go.md