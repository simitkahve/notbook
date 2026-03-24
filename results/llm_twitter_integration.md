# LLM + Twitter/X Integration Research Summary

## Overview

This document covers how to integrate Large Language Models (LLMs) with Twitter/X for automated content generation and posting.

---

## 1. Twitter API v2 + AI

### Key Points
- **X Developer Platform** (developer.x.com) provides the official API
- **Twitter API v2** is the current standard with early access to new features
- Pay-per-usage pricing model is now available
- New v2 features include:
  - Advanced metrics (impressions, video views, clicks)
  - Topic annotations (entity/context filtering)
  - Improved conversation tracking
  - Academic Research product track (free, higher limits)

### API Capabilities
- **Tweet lookup** - Get tweets by ID
- **Manage Tweets** - Post or delete tweets
- **Search Tweets** - Query last 7 days or full archive
- **Timelines** - User timeline and mentions
- **Filtered Stream** - Real-time tweet filtering
- **User/Follow/Like management**

### Official Resources
- Docs: https://developer.x.com/en/docs/twitter-api
- API Reference: https://docs.x.com/llms.txt
- Getting Started: https://developer.x.com/en/docs/tutorials/step-by-step-guide-to-making-your-first-request-to-the-twitter-api-v2

---

## 2. Auto-Tweeting with LLM

### Popular Python Libraries
- **Tweepy** - Most popular Python Twitter library
- **LangChain** - For LLM orchestration
- **Hugging Face Transformers** - For local LLM inference
- **OpenAI API** - For GPT models

### Open Source Projects

#### twitter-llm-bot (GitHub: garyb9/twitter-llm-bot)
- **Stars:** 51 | **Language:** Python
- Fully automatic async Twitter bot using LLMs
- Uses OpenAI API or Hugging Face models
- Features:
  - Contextual content generation
  - APScheduler for timing
  - Redis for state management
  - Docker support
- Tech stack: Python 3.11+, Redis, LangChain, Tweepy

#### x-bot (GitHub: aman-shitta/x-bot)
- Simple Python bot for making tweets
- MIT License

#### mytwitter-bot (GitHub: vmmuthu31/mytwitter-bot)
- AI-powered with Groq LLM
- Covers Web3, Full Stack, DevOps topics
- Runs on GitHub Actions

### Commercial Solutions

#### OpenTweet (opentweet.io)
- **Pricing:** $11.99-19.99/month
- Features:
  - AI content generation (Claude, GPT-4o, Gemini)
  - RSS, GitHub, Stripe connectors
  - Visual calendar scheduling
  - Chrome extension
  - REST API for developers
  - MCP server for AI agents
  - 7-day free trial

---

## 3. Twitter Bot Development

### Basic Setup Steps
1. **Apply for Developer Account** at developer.x.com
2. **Create App** in developer portal to get API keys
3. **Authentication:** OAuth 1.0a (user context) or OAuth 2.0 (app context)
4. **Choose library:** Tweepy is the standard

### Example: Basic Tweet with Tweepy
```python
import tweepy

# API credentials
API_KEY = "your_consumer_key"
API_SECRET = "your_consumer_secret"
ACCESS_TOKEN = "your_access_token"
ACCESS_SECRET = "your_access_token_secret"

# Authenticate
auth = tweepy.OAuth1UserHandler(API_KEY, API_SECRET, ACCESS_TOKEN, ACCESS_SECRET)
api = tweepy.API(auth)

# Post tweet
api.update_status("Hello from my AI bot!")
```

### Example: LLM-Generated Tweet
```python
import openai
import tweepy

# Generate tweet with LLM
client = openai.OpenAI(api_key="your-key")
response = client.chat.completions.create(
    model="gpt-4",
    messages=[{"role": "user", "content": "Write a tech tweet about AI"}]
)
tweet_text = response.choices[0].message.content

# Post tweet
api.update_status(tweet_text)
```

---

## 4. AI Content Generation for Twitter

### Content Strategies
1. **RSS to Tweet** - Transform blog posts automatically
2. **GitHub Activity** - Auto-post commits/releases
3. **Stripe Events** - Tweet revenue milestones
4. **Custom Prompts** - Generate based on topics
5. **Style Learning** - Analyze past tweets for authentic tone

### Best Practices
- **Character limit:** 280 chars (threads up to 25 tweets)
- **Scheduling:** Use tools like APScheduler or cron
- **Rate limiting:** Respect API limits (avoid bans)
- **Content variety:** Mix original content with curated
- **Engagement:** Reply to interactions

### Safety Considerations
- Don't spam (risk of account suspension)
- Add disclosure if posting as a bot
- Human oversight for important content
- Monitor for content policy violations

---

## Quick Start Checklist

1. [ ] Apply for X Developer Account
2. [ ] Create Twitter App and get API keys
3. [ ] Install library: `pip install tweepy openai`
4. [ ] Test authentication
5. [ ] Create simple tweet bot
6. [ ] Integrate LLM for content generation
7. [ ] Add scheduling/cron
8. [ ] Monitor and iterate

---

## Resources

| Resource | URL |
|----------|-----|
| X Developer Portal | https://developer.x.com |
| API Docs | https://developer.x.com/en/docs/twitter-api |
| Tweepy Docs | https://docs.tweepy.org |
| OpenTweet | https://opentweet.io |
| twitter-llm-bot | https://github.com/garyb9/twitter-llm-bot |
| OpenTweet MCP Server | https://github.com/opentweetio/mcp-server |