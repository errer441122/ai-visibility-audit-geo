# Public API Unit Economics (Cost per GEO Audit)

A key operational responsibility in AI Marketing Operations is **cost predictability before execution**. Every audit calculates call volume and upper-bound API cost upfront using public provider list prices (verified July 2026, USD converted conservatively at ~1:1 to EUR so estimates act as a ceiling, never an underestimate).

---

## 1. Cost Driver Formula

```text
Total search calls = Active Engines × Query Depth × Repetitions (× Paraphrase Variants)
```

The dominant cost driver in live GEO auditing is **not LLM tokens**, but the **per-call live web search / grounding fee** charged by model providers.

## 2. Public List-Price Reference (Upper-Bound Ceiling per Call)

| Engine | Default Model | Web Search / Grounding Fee (List) | Est. Token Cost / Call | Upper-Bound Cost / Call |
| --- | --- | --- | ---: | ---: |
| **Google Gemini** | `gemini-2.5-flash` | \$35 / 1,000 calls *(first 1,500/day included on paid billing)* | ~€0.002 | **~€0.04** *(~€0.002 within daily included quota)* |
| **OpenAI GPT** | `gpt-4o-mini` | \$10 / 1,000 web searches | ~€0.002 | **~€0.012** |
| **Anthropic Claude** | `claude-haiku-4-5` | \$10 / 1,000 searches (capped ≤3/call) | ~€0.013 | **~€0.04** |
| **Perplexity** | `sonar` | \$5–\$12 / 1,000 requests (search included) | ~€0.002 | **~€0.014** |

## 3. Typical Audit Cost & Recommended Cadence

| Audit Profile | Queries × Runs | 3–4 Engine Ceiling Cost | Operational Use Case |
| --- | --- | --- | --- |
| **Standard Baseline** | 15 queries × 1 run | **€0.60 – €1.60** | Initial prospect diagnosis & quick baseline |
| **Decision-Grade (Stability Checked)** | 15 queries × 3 runs | **€1.80 – €4.80** | Defensible Share of Voice with stability bands |
| **Deep Competitive Audit** | 30 queries × 2 runs | **€2.40 – €6.40** | Quarterly strategy, Source Gap & editorial planning |

**Why monthly cadence beats daily polling:** Third-party citations rotate gradually and content changes take weeks to get recrawled. Running **one locked-query multi-run audit per month** minimizes API waste while producing clean before/after deltas tied to shipped content and PR actions.
