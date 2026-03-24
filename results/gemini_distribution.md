# Google Gemini/Gemma Distribution & Featured Guide

This document outlines how to get featured and distribute your AI products within the Google Gemini/Gemma ecosystem.

---

## 1. Gemini Extensions Development

### Gemini CLI Extensions
- **What**: Open-source extensions for the Gemini CLI terminal tool
- **How to build**: Create custom tools via MCP servers, custom commands
- **Documentation**: [Getting Started with Gemini CLI Extensions](https://google-gemini.github.io/gemini-cli/docs/extensions/getting-started-extensions.html)
- **Repository**: github.com/google-gemini/gemini-cli

### Firebase Extensions for Gemini API
- **What**: Pre-packaged AI functionality for Firebase apps
- **Status**: Currently paused for new submissions (as of early 2026)
- **Reference**: Firebase Extensions Hub

---

## 2. Google AI Studio Integration

### What is Google AI Studio?
- **Web-based IDE** for prototyping and building with Gemini API
- **Full-stack development**: Server-side runtime for secrets, external APIs, real-time apps
- **Vibe coding**: New "Antigravity" coding agent for automatic app generation (March 2026)

### How to Integrate
1. Go to [ai.google.dev/ai-studio](https://ai.google.dev/ai-studio)
2. Create prompts, experiment with models
3. Select "Get code" to export in your preferred language
4. Use full-stack mode for production apps with backend support

### Firebase Integration
- Firebase now integrates with Google AI Studio (March 2026)
- Enables "prompt to production" workflow

---

## 3. Gemma Open Source Model Distribution

### Available Gemma Models
| Model | Use Case |
|-------|----------|
| Gemma 3 | General text/image, 140+ languages, 128K context |
| CodeGemma | Code completion & programming |
| PaliGemma 2 | Visual data processing |
| ShieldGemma 2 | Safety evaluation |

### Distribution Channels

#### Kaggle Models
- Publish Keras/PyTorch models to Kaggle
- Tutorial: [Publish your Keras models on Kaggle and Hugging Face](https://developers.googleblog.com/en/publish-your-keras-models-on-kaggle-and-hugging-face)
- Gemma models available at: kaggle.com/models/google/gemma

#### Hugging Face
- Publish models to Hugging Face Hub
- Community-built variants also hosted there
- Official: github.com/google/gemma_pytorch

#### Vertex AI
- Deploy Gemma on Google Cloud Vertex AI
- Documentation: [Use Gemma open models on Vertex AI](https://docs.cloud.google.com/vertex-ai/generative-ai/docs/open-models/use-gemma)

#### Gemma Cookbook
- Community examples & guides: github.com/google-gemini/gemma-cookbook

---

## 4. How to Get Featured in Gemini

### Google Cloud Marketplace (AI Agents)
**Primary path for featured AI agents:**

1. **Become a vendor**: Sign up on Cloud Marketplace
2. **Create Agent Card**: JSON file following A2A (Agent2Agent) protocol specification
3. **Use Producer Portal**: Create listing, add product details, pricing
4. **Pricing options**: Free, subscription, usage-based, or combined
5. **Submit for review**: Google reviews and approves

**Requirements:**
- Must be software-only (no hardware/professional services)
- Must comply with Cloud Marketplace listing requirements
- Must implement A2A protocol for inter-agent communication

**Reference**: [Offer AI agents through Google Cloud Marketplace](https://docs.cloud.google.com/marketplace/docs/partners/ai-agents)

### Partner Programs
- **Gemini Enterprise Partner**: Join Google Cloud partner ecosystem
- **AI Agent Marketplace**: Dedicated marketplace for AI agents (October 2025)
- Reference: [Partners powering Gemini Enterprise](https://cloud.google.com/blog/topics/partners/partners-powering-the-gemini-enterprise-agent-ecosystem)

### Community Recognition
- **Gemmaverse**: Community showcase on Hugging Face
- Share your Gemma projects to get visibility
- Participate in Kaggle competitions with Gemma

---

## Summary: Quick Path to Featured

| Path | Best For | Link |
|------|----------|------|
| Cloud Marketplace | AI Agents, Enterprise | docs.cloud.google.com/marketplace |
| Kaggle Models | Model publishing | kaggle.com/models |
| Hugging Face | Open model distribution | huggingface.co/models |
| Google AI Studio | App development | ai.google.dev/ai-studio |
| Vertex AI | Enterprise deployment | cloud.google.com/vertex-ai |

---

*Last updated: March 2026*