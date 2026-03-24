# Claude Apps Distribution & Integration Guide

## Overview

This document covers how to build extensions for Anthropic's Claude, get featured/distributed, and integrate with the Claude API.

---

## 1. How to Build a Claude Extension/App

### Plugin System (Claude Code)

Claude Code uses a plugin-based architecture. Plugins can include:

- **Skills** — Task-specific instructions activated dynamically
- **MCP Connectors** — Connections to external tools/data sources
- **Slash Commands** — User-invoked commands for workflows
- **Sub-agents** — Custom agent definitions for complex tasks

### Creating a Plugin

```bash
# 1. Create plugin directory
mkdir my-first-plugin

# 2. Create manifest at .claude-plugin/plugin.json
{
  "name": "my-first-plugin",
  "description": "A greeting plugin",
  "version": "1.0.0",
  "author": { "name": "Your Name" }
}

# 3. Add skills in skills/ directory
mkdir -p my-first-plugin/skills/hello
# Create SKILL.md with frontmatter
```

### Plugin Structure

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   └── skill-name/
│       └── SKILL.md
├── commands/
├── agents/
├── hooks/
│   └── hooks.json
├── .mcp.json
└── .lsp.json
```

### Testing Plugins

```bash
claude --plugin-dir ./my-first-plugin
# Use /reload-plugins to reload without restart
```

### Resources

- [Create plugins documentation](https://docs.anthropic.com/en/docs/claude-code/plugins)
- [Plugins reference](https://docs.anthropic.com/en/docs/claude-code/plugins-reference)

---

## 2. Getting Featured / Distribution

### Plugin Directory Submission

Submit your plugin to the official directory (available in both Claude.ai and Claude Code):

**Submission URLs:**
- Claude.ai: https://claude.ai/settings/plugins/submit
- Console: https://platform.claude.com/plugins/submit

### Marketplace Options

#### Option A: Official Plugin Directory
- Submit to the community directory
- Basic automated review before listing
- "Anthropic Verified" badge available (additional review)
- Available to all Claude users automatically

#### Option B: Custom Marketplace
- Create your own plugin marketplace
- Host on GitHub, GitLab, or any git service
- Users add with: `/plugin marketplace add owner/repo`
- Full control over plugins and distribution

**Marketplace structure:**
```json
{
  "name": "my-plugins",
  "owner": { "name": "Your Name" },
  "plugins": [
    {
      "name": "my-plugin",
      "source": { "source": "github", "repo": "owner/repo" },
      "description": "Plugin description"
    }
  ]
}
```

### Claude Builder Program

Anthropic's builder program for EMEA-based developers:

- **Benefits:** 3 months of Claude Max ($600 value), mentorship, technical deep-dives, VC connections
- **Selection:** Based on shipped products, commercial potential, and builder ecosystem connections
- **Cohort:** 25 builders per cohort, 12-week program
- **Apply:** https://claude.com/programs/builder

### Note on "Claude AI Clinic"

No specific "Claude AI Clinic" program was found in current Anthropic documentation. The closest equivalents are:
- **Claude Builder Program** — mentorship and acceleration
- **Development Partner Program** — optional data sharing for model improvement
- **Anthropic Academy** — learning resources at anthropic.com/learn

---

## 3. Claude API Integration

### Agent SDK (Recommended for Apps)

Build autonomous AI agents with built-in tools:

**Installation:**
```bash
# TypeScript
npm install @anthropic-ai/claude-agent-sdk

# Python
pip install claude-agent-sdk
```

**Basic Usage:**
```python
import asyncio
from claude_agent_sdk import query, ClaudeAgentOptions

async def main():
    async for message in query(
        prompt="Find and fix the bug in auth.py",
        options=ClaudeAgentOptions(allowed_tools=["Read", "Edit", "Bash"]),
    ):
        print(message)
```

### Client SDKs

For direct API access (implement your own tool loop):

- **Python, TypeScript, Java, Go, Ruby, C#, PHP** — Official SDKs available
- **Docs:** https://docs.anthropic.com/en/api/client-sdks

### API Authentication

```bash
export ANTHROPIC_API_KEY=your-api-key
```

Also supports:
- Amazon Bedrock (`CLAUDE_CODE_USE_BEDROCK=1`)
- Google Vertex AI (`CLAUDE_CODE_USE_VERTEX=1`)
- Microsoft Azure (`CLAUDE_CODE_USE_FOUNDRY=1`)

### Agent SDK Capabilities

| Feature | Description |
|---------|-------------|
| Built-in tools | Read, Write, Edit, Bash, Glob, Grep, WebSearch, WebFetch |
| Hooks | PreToolUse, PostToolUse, Stop, SessionStart/End, etc. |
| Sub-agents | Spawn specialized agents for focused tasks |
| MCP | Connect to external systems (databases, browsers, APIs) |
| Sessions | Maintain context, resume sessions, fork for exploration |
| Permissions | Control which tools the agent can use |

### Branding Guidelines

When integrating Claude in your product:
- ✅ Use "Claude Agent" or "Claude"
- ✅ "{YourAgentName} Powered by Claude"
- ❌ Don't use "Claude Code" or mimic Claude Code branding

---

## 4. Additional Resources

- **Claude Platform:** https://www.anthropic.com/api
- **Developer Docs:** https://docs.anthropic.com/en/docs/claude-code
- **Anthropic Academy:** https://www.anthropic.com/learn/build-with-claude
- **Marketplace Docs:** https://docs.anthropic.com/en/docs/claude-code/plugin-marketplaces
- **Console:** https://platform.claude.com/

---

*Last updated: March 2026*