# Perplexity & AI Search Engine Distribution Research

**Research Date:** March 2026  
**Output Location:** `C:\Users\simit\Documents\repos\dj-names\results\perplexity_distribution.md`

---

## 1. Perplexity API Integration

Perplexity offers three main APIs for developers:

### Available APIs

| API | Purpose |
|-----|---------|
| **Agent API** | Multi-provider API for building LLM applications with web search tools |
| **Search API** | Raw, ranked web search results with advanced filtering |
| **Embeddings API** | Semantic search and RAG pipelines |

### Quick Start
- **Documentation:** https://docs.perplexity.ai/
- **SDKs:** Python and TypeScript available
- **Quickstart:** https://docs.perplexity.ai/docs/sdk/overview

### Pricing Model
- Pay-per-request model
- Free tier available for experimentation
- API keys available through Perplexity dashboard

---

## 2. How to Become a Source in Perplexity

Perplexity does **NOT** offer a paid inclusion program. Being cited requires earning visibility through content quality and external authority.

### Key Strategies

#### Content Optimization
- **Direct query relevance** - Answer the exact question being asked
- **Clear structure** - Use headings, bullet points, tables, bold key terms
- **Definition-first approach** - Start with "[Topic] is..." format
- **Question-based headings** - H2/H3 as questions: "What is...?", "How does...?"
- **Specific data points** - Include concrete numbers and statistics with cited sources
- **JSON-LD structured data** - Implement FAQ, article, and how-to schemas

#### Platform Presence
- Reddit and forums perform exceptionally well (community-validated content)
- LinkedIn articles and discussions
- GitHub documentation and repositories
- Amazon product listings

#### Earned Media
- News and journalism content **dominates** Perplexity citations
- Tier-1 publications (Forbes, TechCrunch, Business Insider) carry structural advantages
- Journalism passes editorial accountability that company websites cannot replicate

---

## 3. AI Search Engine Distribution

### Major AI Search Platforms

| Platform | Source Preferences | Distribution Approach |
|----------|-------------------|----------------------|
| **Perplexity** | News/earned media (60%) | Earned media, journalism |
| **ChatGPT Search** | Directories, listings (48%) | Structured data, directory presence |
| **Google AI Overviews** | Comprehensive content | Traditional SEO + structured data |
| **Gemini** | Brand-owned content (52%) | Own website content priority |

### Distribution Channels

1. **Earned Media** - News coverage, press releases, guest articles
2. **Platform Presence** - Reddit, LinkedIn, GitHub, forums
3. **Directory Listings** - Yelp, G2, Capterra forChatGPT
4. **Structured Data** - Schema markup for all AI engines

---

## 4. How Perplexity Chooses Sources

### The Three-Layer Reranking System

#### Layer 1: Initial Retrieval
- Standard relevance scoring from index
- Produces candidate document set

#### Layer 2: Standard Ranking
- Conventional authority and relevance signals
- Initial ordered list

#### Layer 3: L3 XGBoost Reranker (Critical)
- Uses BERT-based entity linking
- Filters for **entity clarity** and **authoritativeness**
- Key parameters: `l3_reranker_drop_threshold`, `l3_reranker_drop_all_docs_if_count_less_equal`
- **Result:** Would rather return no sources than low-quality ones

### Authoritative Domain Lists
Perplexity manually curates lists of trusted platforms:
- GitHub, Amazon, LinkedIn, Coursera, Reddit

Content connected to these platforms receives algorithmic boosts.

### Topic Multipliers
- **Amplified:** AI, ML, science, technology, business strategy (~3x visibility)
- **Suppressed:** Entertainment, sports, celebrity content

### Time Decay
- **30-day freshness sweet spot**
- Aggressive decay - content loses visibility rapidly
- Regular refreshes required for sustained citations

### New-Post CTR Window
- Strong early engagement (first hours after publication) determines long-term visibility
- Article promotion at launch is critical

---

## Key Takeaways for Content Distribution

1. **Perplexity is NOT a content problem - it's an authority problem**
2. **Earned media outperforms company websites** due to external validation
3. **Freshness matters** - maintain 30-day publication cadence
4. **Entity clarity** - clearly define what your company does and its category
5. **Multi-platform presence** - build authority across Reddit, LinkedIn, GitHub
6. **No paid inclusion** - cannot buy citations, must earn through quality

---

## References

- Perplexity Documentation: https://docs.perplexity.ai/
- Conbersa - How to Get Mentioned in Perplexity: https://www.conbersa.ai/learn/how-to-get-mentioned-in-perplexity-answers
- Authority Tech - How Perplexity Selects Sources: https://authoritytech.io/blog/how-perplexity-selects-sources-algorithm-2026
- Yext Citation Study (6.8M citations): https://www.yext.com/
- Search Engine Land coverage: https://searchengineland.com/
