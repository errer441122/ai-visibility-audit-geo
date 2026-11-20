# Live 5-Brand SaaS AI Crawler Benchmark (`robots.txt` & `/llms.txt`)

**Verification date:** 2026-11-20 (live HTTP checks against public production domains)  
**Brands benchmarked:** `notion.so`, `clickup.com`, `airtable.com`, `coda.io`, `asana.com`  
**Raw data:** [`saas-ai-crawler-benchmark.csv`](saas-ai-crawler-benchmark.csv)

---

## Why This Check Matters Before Optimizing Content

Before investing in GEO content or Digital PR, a Marketing Operations / AEO team must verify the **upstream layer**: *can AI search and retrieval crawlers actually read the site without being blocked or trapped in parameterized URLs?*

Crucially, **training bots** (`GPTBot`, `ClaudeBot`, `Google-Extended`) are separate from **live AI search & user-fetch bots** (`OAI-SearchBot`, `ChatGPT-User`, `Claude-SearchBot`, `PerplexityBot`). Blocking training while leaving search/user-fetch open is a deliberate governance choice — accidentally blocking search bots makes a brand invisible in real-time AI answers.

---

## Live Benchmark Results (Verified 2026-11-20)

| Brand | `robots.txt` Rules | Explicit AI Agent Section | Search Bots (`OAI-SearchBot`, `PerplexityBot`, `Claude-SearchBot`) | Training Bots (`GPTBot`, `ClaudeBot`, `Google-Extended`) | `Amazonbot` | `/llms.txt` | Key Finding |
| --- | ---: | --- | --- | --- | --- | --- | --- |
| **Asana** (`asana.com`) | 55 | **Yes (17 named AI agents)** | Allowed on public pages (gated `/ebook/` & `/resources/thank-you` excluded) | Allowed on public pages (same exclusions) | Explicitly listed | **200 OK** (24.7 KB) | Clearest enterprise AI crawler governance: explicitly governs OpenAI, Anthropic, Perplexity, Google, Meta, Mistral, Apple, DuckDuckGo, and Common Crawl |
| **Notion** (`notion.so`) | 34 | Partial (`Amazonbot` only) | Allowed via `User-agent: *` | Allowed via `User-agent: *` | **Blocked (`Disallow: /`)** | **200 OK** (6.8 KB) | Publishes **11 segmented sitemaps**, including a dedicated Markdown sitemap (`notion.com/md/sitemap.xml`), while blocking third-party SEO scrapers (`AhrefsBot`, `SemrushBot`, `BLEXBot`, `dotbot`) |
| **ClickUp** (`clickup.com`) | 42 | No (wildcard `*`) | Allowed via `User-agent: *` | Allowed via `User-agent: *` | Allowed via `*` | **200 OK** (8.8 KB) | Strong crawl-budget hygiene: explicitly disallows `*utm_*`, `*fbclid=`, `*gclid=`, `*msclkid=`, `*mc_cid=` so AI & search bots don't index duplicate campaign URLs |
| **Airtable** (`airtable.com`) | 6 | No (wildcard `*`) | Allowed via `User-agent: *` | Allowed via `User-agent: *` | Allowed via `*` | **404** | Minimalist policy blocking `/studio/`, `/api/`, `/sanity-documentation`; no AI bot segmentation or UTM parameter rules |
| **Coda** (`coda.io`) | 6 | No (wildcard `*`) | Allowed via `User-agent: *` | Allowed via `User-agent: *` | Allowed via `*` | **404** | Minimalist policy protecting user workspaces (`/docs`, `/d/`); no explicit AI agent rules |

---

## Actionable Takeaways for Any Marketing / AEO Team

1. **Adopt Asana's explicit AI-agent block** if Legal or Security wants visibility/control over training vs. live retrieval bots (`OAI-SearchBot`, `PerplexityBot`, `Claude-SearchBot` kept open for discovery; gated lead magnets like `/ebook/` and `/resources/thank-you` excluded).
2. **Adopt ClickUp's marketing-parameter exclusions** (`Disallow: /*utm_*`, `/*fbclid=`, `/*gclid=`) to prevent paid-media URLs from diluting crawl budget and splitting canonical citations.
3. **Treat `/llms.txt` pragmatically:** 3 of the 5 leaders (Asana, Notion, ClickUp) now publish one, but independent crawl logs show very low autonomous bot pickup today — prioritize clean sitemaps (like Notion's segmented sitemaps), structured pricing/FAQ HTML, and third-party Source Gap coverage first.
