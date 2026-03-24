# LLM + YouTube Integration Research

Research on integrating LLMs with YouTube for video creation, captioning, content ideas, and description generation.

---

## 1. YouTube API + AI Video Generation

### Google Veo (Recommended)
- **Veo 3.1** via Gemini API — generates 8-second videos in 720p/1080p/4K with audio
- **Veo 2** — Generally available for developers via Google AI Studio and Vertex AI
- Docs: https://ai.google.dev/gemini-api/docs/video
- Vertex AI: https://cloud.google.com/vertex-ai/generative-ai/docs/model-reference/veo-video-generation

### YouTube Create App
- YouTube's native AI tool for creators
- Auto-generates labels disclosing synthetic content
- https://support.google.com/youtube/answer/16631240

### Alternatives
- Runway ML ( Gen-3, Gen-2 )
- Pika Labs
- Luma Dream Machine

---

## 2. Auto-Captioning/Subtitling with AI

### Whisper-based Solutions
| Service | Pricing | Notes |
|---------|---------|-------|
| **Apify YouTube Transcribe** | $0.15/min | Uses Faster-Whisper, outputs JSON/SRT/VTT |
| **TurnScribe** | API | Supports YouTube, TikTok, Instagram |
| **Subper** | Free tier | 98.5% accuracy, OpenAI Whisper-powered |
| **api.video** | API | Generates transcripts with single API call |

### Implementation
- Use `practicaltools/apify-youtube-transcribe` on Apify
- OpenAI Whisper API for direct audio processing
- Gladia offers a dedicated YouTube transcription pipeline

---

## 3. YouTube Content Ideas with LLM

### AI Idea Generators
| Tool | Features |
|------|----------|
| **KlickGen** | Connects to your channel, scans trending in niche |
| **YouTube Tools Hub** | Free AI-powered idea generator |
| **ideas-generator.com** | Trained on top trending videos monthly |
| **EzCreator** | Paste any YouTube link, mines viral ideas |
| **WritingTools.ai** | Generates titles + hooks + angles |

### Custom Implementation
- Use YouTube Data API v3 to fetch trending videos
- Feed data to LLM (MiniMax, GPT-4) for idea generation
- Prompt: "Generate 10 YouTube video ideas for [niche] based on trending topics..."

---

## 4. Video Description Generators

### Ready-made Tools
| Tool | Features |
|------|----------|
| **Zubtitle** | Timestamps, SEO-optimized, social media export |
| **SummarAIze** | Auto descriptions + titles + hashtags |
| **Miniloop** | SEO-friendly with timestamps + links |
| **ScreenApp** | Video-to-description, timestamps, hashtags |

### Custom Implementation
- Use YouTube Data API to update video description
- LLM generates description from video transcript or title
- Include: hooks, timestamps, CTA, relevant hashtags

---

## Recommended Stack for Automation

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   YouTube API   │────▶│  LLM (MiniMax)  │────▶│ YouTube Data API│
│   (Data v3)     │     │  (Ideas/Desc)   │     │  (Upload)       │
└─────────────────┘     └─────────────────┘     └─────────────────┘
         │                                               ▲
         ▼                                               │
┌─────────────────┐                           ┌─────────────────┐
│   Video Gen     │                           │  Caption API    │
│   (Veo/Pika)    │                           │ (Whisper/Apify) │
└─────────────────┘                           └─────────────────┘
```

### Quick Start
1. **Ideas**: YouTube Data API → trending feed → LLM → content ideas
2. **Video**: Veo 2/3 via Gemini API → generate clip
3. **Captions**: Apify Whisper actor → SRT/VTT
4. **Description**: LLM → SEO-optimized description → YouTube Data API upload

---

*Research completed: 2026-03-24*
