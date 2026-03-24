# LLM + GitHub Integration Research Summary

## 1. GitHub Actions with AI/LLM

### GitHub Models
- **GitHub Models** provides AI inference API using GitHub credentials
- Available models include OpenAI, Meta, DeepSeek
- Directly integrated with GitHub Actions via `actions/ai-inference` action
- Use case: Triage, summarize, automate code review within CI/CD

### GitHub Agentic Workflows
- New framework for repository automation with AI coding agents
- Strong guardrails in GitHub Actions
- Supports multiple AI engines (coding agents)
- Quick start CLI available

### Popular GitHub Actions for AI
- **actions/ai-inference** (456 stars) - Call AI models with GitHub Models
- Build custom code review bots using Claude API, Gemini, or other LLMs

---

## 2. GitHub Copilot Alternatives

| Tool | Type | Key Features |
|------|------|--------------|
| **Tabby** | Open source, self-hosted | AI coding assistant, cloud or on-premises |
| **Codeium** | Free tier available | Solid autocomplete, no credit card needed |
| **Kilo** | Open source | VS Code, JetBrains, CLI support |
| **Reflyx** | Privacy-first | Local AI models, optional cloud |
| **OpenCode** | Open source | Terminal-native AI coding agent |
| **Claude Code** | Anthropic | CLI-based coding agent |
| **Continue** | Open source | VS Code extension with Ollama/local LLMs |

---

## 3. GitHub API + AI Integration

### Code Review Bots
- Build with **Claude API** + GitHub Actions
- Detect bugs, security issues, style violations
- Run on every PR automatically

### Integration Options
- **GitHub API** → Send to LLM → Post results as PR comments
- **GitHub Webhooks** → Trigger AI workflows
- **Claude Plugin** for GitHub - Anthropic's official integration

### Automation Examples
- Auto-triage issues
- Summarize PRs
- Generate changelogs
- Write unit tests

---

## 4. Open Source Alternatives

### Self-Hosted Coding Assistants
- **Tabby** - Most popular self-hosted AI coding assistant
- **OpenCode** - Terminal-native, open source
- **Continue** - VS Code + local Ollama integration
- **TalkCody** - Open source AI coding agent

### CLI-Based Agents
- **OpenAI Codex CLI** (67k stars) - Lightweight terminal coding agent in Rust
- **Claude Code** - Anthropic's CLI coding agent

### Frameworks
- **Tandem** - Open source local-first AI coding assistant
- Build custom agents with LangChain, AutoGen, or CrewAI

---

## Quick Start Recommendations

1. **For GitHub Actions + AI**: Use `actions/ai-inference` with GitHub Models
2. **For self-hosted**: Tabby or Continue + Ollama
3. **For privacy-first**: Reflyx or self-hosted Tabby
4. **For CLI automation**: OpenAI Codex CLI or Claude Code

---

*Generated: 2026-03-24*