# LLM Distribution Strategy: Getting Embedded in Major AI Platforms

> Research Summary - March 2025

This document outlines how AI products can get distributed through major LLM platforms (ChatGPT, Claude, Gemini, Perplexity) and the strategies that work for AI-native products.

---

## 1. How Apps Get Added to Major LLM Platforms

### ChatGPT (OpenAI) - GPT Store & Apps SDK

**Path to Listing:**
1. Build using OpenAI Apps SDK
2. Deploy your app (must be hosted externally)
3. Submit via OpenAI Platform Dashboard
4. Pass review against developer guidelines

**Requirements:**
- ChatGPT Plus/Pro subscription or Enterprise organization membership
- Developer verification (identity confirmation)
- Privacy policy required
- Must pass UX/UI guidelines review

**Key Guidelines:**
- Apps must provide functionality beyond ChatGPT's native capabilities
- Clear, accurate tool names and descriptions
- Proper annotations (readOnlyHint, openWorldHint, destructiveHint)
- Minimal data collection - only what's necessary
- No misleading names, copycat designs, or impersonation

**Current Limitations:**
- Physical goods commerce only (no digital products/services)
- No advertising within apps
- Limited to external checkout (no embedded payment)

**Enhanced Distribution:**
Apps with "strong real-world utility and high user satisfaction" may qualify for:
- Directory placement
- Proactive suggestions to users

> **Docs:** https://developers.openai.com/apps-sdk

---

### Claude (Anthropic) - Claude Marketplace & Plugins

**Two Distribution Channels:**

#### 1. Claude Marketplace (Enterprise)
- **Status:** Limited preview, invite-only
- **Target:** Enterprise customers with existing Anthropic commitments
- **How to apply:** Join partner waitlist
- **Current Partners:** GitLab, Harvey, Lovable, Replit, Rogo, Snowflake

#### 2. Claude Code Plugins (Developer)
- **Status:** Fully open
- **How to list:** Submit via in-app forms (claude.ai/settings/plugins/submit or platform.claude.com/plugins/submit)
- **Also possible:** Create own marketplace and distribute independently

**Plugin Types Available:**
- Skills (custom capabilities)
- Agents (autonomous workers)
- Hooks (automation triggers)
- MCP Servers (Model Context Protocol)

**Categories:**
- Code intelligence (language servers)
- External integrations (GitHub, Jira, Figma, Slack, etc.)
- Development workflows
- Output styles

> **Docs:** https://code.claude.com/docs/en/discover-plugins.md

---

### Google Gemini

**Integration Paths:**

#### 1. Gemini CLI Extensions
- **Status:** Open for development (October 2025)
- **How to build:** Create extensions to connect Gemini to workflows
- **Docs:** https://codelabs.developers.google.com/getting-started-gemini-cli-extensions

#### 2. Google Workspace Marketplace
- List integrations that work with Gemini Apps
- Example: GitHub for Gemini (1M+ users)

#### 3. Firebase Extensions
- Package AI functionality using Gemini API

---

### Perplexity

**Integration Options:**

#### 1. API Access
- **Quickstart:** https://docs.perplexity.ai/docs/getting-started/quickstart
- Generate API key, make calls in <3 minutes
- Both REST API and SDKs (Python, TypeScript)

#### 2. MCP Integration
- Model Context Protocol support
- Example: PitchBook integration for market intelligence
- Enables real-time data in Perplexity answers

#### 3. Partner Program
- Enterprise partnerships for data providers
- Referral/integration opportunities

---

## 2. Becoming an LLM Plugin/Integration

### The Model Context Protocol (MCP) - The New Standard

**What is MCP?**
An open standard (open-sourced by Anthropic) for connecting AI assistants to data sources, business tools, and development environments.

**Adoption:**
- Anthropic: Full support
- OpenAI: Support in Agents SDK
- Many other providers adopting

**Benefits:**
- Standardized way to connect LLMs to external systems
- Works across multiple LLM providers
- Enables interactive UI components (MCP Apps)

**Use Cases:**
- Data retrieval (databases, documents)
- Business tools (CRM, project management)
- Development environments (code repos, CI/CD)

> **Resource:** https://www.anthropic.com/research/model-context-protocol

---

### Direct API Integration

Most LLM platforms offer API access for custom integrations:

| Platform | API Key Generation | Docs |
|----------|-------------------|------|
| OpenAI | api.openai.com | developers.openai.com |
| Anthropic | console.anthropic.com | docs.anthropic.com |
| Perplexity | perplexity.ai/api | docs.perplexity.ai |
| Google | Google AI Studio | developers.generativeai.google |

**Best Practice:**
Start with API integration (fastest path), then pursue marketplace listing once product is validated.

---

## 3. Distribution Strategies for AI Products

### Three-Layer Distribution Model (IdeaPlan)

#### Layer 1: Developer Adoption (Viral Foundation)
- **Target:** Developers who integrate your AI into products
- **Tactics:**
  - Frictionless onboarding (API key in 60 seconds)
  - Free tier with real value
  - Excellent developer experience (docs, SDKs, error messages)
  - Community building (Discord, GitHub)
  - Use case templates and code examples

**When it works:** Clear API/SDK, developer-influenced buying, technical use cases

#### Layer 2: Workflow Embedding (Integration Lock-In)
- **Target:** Embed into tools users already depend on
- **Tactics:**
  - Platform integrations (Slack, Notion, Figma, GitHub, VSCode)
  - API-first architecture for other products to embed
  - Contextual triggers (suggest at moment of need)
  - Data integration (connect to existing data sources)
  - Workflow customization

**Example:** GitHub Copilot embeds in IDEs, Notion AI lives inside Notion

#### Layer 3: Trust Positioning (Brand Moats)
- **Target:** Risk-averse industries (legal, healthcare, finance)
- **Tactics:**
  - Compliance-first messaging (SOC 2, HIPAA, GDPR)
  - Transparent limitations documentation
  - Industry partnerships
  - Case studies and testimonials
  - Dedicated support and SLAs

---

### Distribution Metrics That Matter

| Metric | What It Measures |
|--------|------------------|
| Developer activation rate | % making successful API calls within 24h |
| Integration depth | Apps/workflows per customer |
| Organic vs. paid growth | Word-of-mouth vs. paid acquisition |
| Time-to-production | Days from first call to production |
| Enterprise conversion rate | Developer trials → enterprise contracts |
| Reference customer NPS | Satisfaction for advocacy |

---

### Common Distribution Anti-Patterns

1. **Outbound sales before product-market fit** - Hiring SDRs before developers adopt organically
2. **Competing on benchmarks** - Marketing 2% higher scores; developers don't care
3. **Building standalone when integration is possible** - Separate app vs. embedding in existing tools
4. **Ignoring developer experience** - API as afterthought; bad docs kill adoption
5. **Enterprise-first without bottom-up** - Legal reviews before developers can try
6. **Overpromising capabilities** - "Fully autonomous" claims create distrust

---

## 4. Examples of Successful LLM-Native Products

### Developer/Tooling Category

| Product | What They Do | Distribution Strategy |
|---------|---------------|----------------------|
| **GitHub Copilot** | Code completion in IDEs | Workflow embedding (VSCode, JetBrains) |
| **v0 (Vercel)** | AI code generator | Developer-first, community viral |
| **Replit** | AI-powered coding platform | Embedded in Replit IDE |
| **Cursor** | AI code editor | IDE integration |

### Enterprise/Workflow Category

| Product | What They Do | Distribution Strategy |
|---------|---------------|----------------------|
| **Harvey AI** | Legal AI | Trust positioning + partnerships |
| **Notion AI** | Writing assistant in Notion | Workflow embedding |
| **Grammarly** | AI writing enhancement | Browser/editor integration |
| **Intercom AI** | Customer support | Workflow integration |
| **Glean** | Enterprise AI search | Trust + enterprise sales |

### Consumer Category

| Product | What They Do | Distribution Strategy |
|---------|---------------|----------------------|
| **ChatGPT** | General AI assistant | Direct + mobile app |
| **Claude.ai** | AI assistant | Trust positioning |
| **Midjourney** | Image generation | Discord community |

### API/Platform Category

| Product | What They Do | Distribution Strategy |
|---------|---------------|----------------------|
| **OpenAI API** | Model access | Developer-first + marketplace |
| **Anthropic API** | Claude access | Developer-first + enterprise |
| **Hugging Face** | Model hub + API | Community + marketplace |
| **Perplexity API** | Search + Q&A | API-first + MCP integration |

---

## Key Takeaways

1. **MCP is becoming the standard** - Model Context Protocol is being adopted across platforms; building MCP-compatible integrations future-proofs your distribution

2. **Start with API, then marketplace** - Prove product-market fit via direct API before investing in platform-specific listings

3. **Developer experience IS distribution** - Stripe won payments through DX; OpenAI won AI the same way. Docs, SDKs, and error messages matter more than marketing

4. **Embedding > standalone** - Products integrated into existing workflows (Notion AI, GitHub Copilot) beat standalone tools that require habit formation

5. **Trust is a moat in enterprise** - For regulated industries, compliance, transparency about limitations, and case studies matter more than benchmark scores

6. **Three layers compound** - Developers (Layer 1) → Integration (Layer 2) → Enterprise trust (Layer 3). Each builds on the previous

---

## Resources & Links

- OpenAI Apps SDK: https://developers.openai.com/apps-sdk
- Claude Code Docs: https://code.claude.com/docs/en/
- MCP Documentation: https://www.anthropic.com/research/model-context-protocol
- Gemini CLI Extensions: https://codelabs.developers.google.com/getting-started-gemini-cli-extensions
- Perplexity API: https://docs.perplexity.ai/
- IdeaPlan Distribution Playbook: https://www.ideaplan.io/guides/ai-product-distribution-playbook

---

*Generated: March 2025*