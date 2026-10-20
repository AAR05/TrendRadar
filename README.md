# TrendRadar ⚡
### Autonomous Micro-Trend Spotter & Supplier Orchestrator
**Kritical Hacks 2026 — AI / ML Track Submission**

TrendRadar turns reactive e-commerce sourcing into a data-driven science. By wrapping autonomous web agents around dynamic social infrastructure, it shrinks the traditional 14-day trend-scouting lifecycle down to **6 hours**, protecting merchants from dead-stock accumulation via real-time wholesale pricing matches and mathematical viability clamping.

---

## ⚡ The Core Problem & Solution
* **The Manual Bottleneck:** Traditional scouts take roughly ~14 days to spot a product on social feeds, find matching entries on global B2B platforms (Alibaba/IndiaMART), parse inventory data, and compute margins on error-prone spreadsheets—often missing the trend window entirely.
* **The TrendRadar Fix:** An automated loop that crawls public infinite-scroll social media elements, runs high-velocity visual grouping over incoming images, evaluates targeted unit economics, and provides structured merchant alerts backed by live cryptographic proof.

---

## 🛠️ System Architecture Blueprint

```text
  [ Public Social Feeds ] (Reels, TikTok, Reddit)
             │
             ▼
  ┌────────────────────────────────────────────────────────┐
  │  TinyFish Framework Automation: run-async Web Agents   │
  └──────────────────────────┬─────────────────────────────┘
                             │
                             ▼
  ┌────────────────────────────────────────────────────────┐
  │     Multimodal Partition & Vector Processing Engine    │
  │  - OpenAI CLIP (ViT-B/32) -> 512d Image Vector Embeds  │
  │  - Gemini 1.5 Flash       -> 3-Level Json Taxonomy     │
  └──────────────────────────┬─────────────────────────────┘
                             │
                             ▼
  ┌────────────────────────────────────────────────────────┐
  │          PostgreSQL Unified Datastore + pgvector       │
  │      - HNSW Cosine Index Clamped for Zero Drift        │
  └──────────────────────────┬─────────────────────────────┘
                             │
                             ▼
  ┌────────────────────────────────────────────────────────┐
  │        TinyFish Search API & Cloud Browser CDP         │
  │  - Instant global B2B supplier scraping & cost parse   │
  │  - Full cryptographic page screenshot proof captures   │
  └──────────────────────────┬─────────────────────────────┘
                             │
                             ▼
  ┌────────────────────────────────────────────────────────┐
  │   Analytics Engine: Product Viability Index (PVI)      │
  │         Output: [0, 100] Clamped Merchant Alert         │
  └────────────────────────────────────────────────────────┘
```

### Key Technical Safeguards Applied:
1. **Zero Vector Sprawl:** By running `pgvector` inside a primary PostgreSQL instance, the app eliminates the synchronization lag and dual-write data drift associated with using independent services like ChromaDB or Pinecone.
2. **Defensive SSRF Firewall:** Every ingestion URL undergoes active DNS resolution at runtime. IPs are matched against deep network profiles blocking cloud loopbacks (`169.254.169.254`), private networks, and internal proxies to neutralize Time-of-Check to Time-of-Use (TOCTOU) rebinding bugs.
3. **Calibrated Saturation Penalties:** The Product Viability Index (PVI) automatically falls to zero if market density constraints cross saturation ceilings or if landed import costs outpace calculated retail value.

---

## 📂 Repository Code Structure

```text
├── trendradar_core.ipynb       # Executable End-to-End Notebook (Colab/VS Code ready)
├── README.md                   # System Architecture & Technical Specifications
└── trendradar/
    ├── __init__.py
    ├── schema.sql              # PostgreSQL DDL with HNSW Index Definitions
    ├── requirements.txt        # System library pinning manifest
    └── app/
        ├── __init__.py
        ├── config.py           # Infrastructure settings & blocklist profiles
        ├── security.py         # DNS-Pinning & SSRF validation middleware
        ├── analytics.py        # Vectorized PVI formulation & risk solvers
        ├── vision.py           # CLIP vector extraction & Gemini routing split
        ├── tinyfish_client.py  # Headless browser automation wrapper
        └── main.py             # FastAPI REST endpoints
```

---

## 🧮 Algorithmic Formulation

The system scores product feasibility using an empirically bounded priority matrix:

\[PVI = 100 \times (0.35 \cdot V + 0.25 \cdot C + 0.20 \cdot S + 0.20 \cdot M) \times (1 - R)\]

* **\(V\) (Mention Velocity):** Standardized keyword acceleration z-score squashed logistically between `[0.0, 1.0]`.
* **\(C\) (Cluster Growth):** Week-over-week post volume scaling within the visual embedding space.
* **\(S\) (Supply Feasibility):** Share of accessible wholesale paths matching margin and target Minimum Order Quantity (MOQ).
* **\(M\) (Landed Margin):** `(Estimated Retail - Estimated Landed Cost) / Estimated Retail`. Instantly clamped to `0` if costs exceed gross profit bounds.
* **\(R\) (Market Saturation Risk):** Exponential penalty applied when visual cosine similarity clustering meets or exceeds `0.90` across public marketplaces.

---

## 👥 Team Allocations (AI / ML Track)
* **Aaryan Prakash (Team Lead):** Product Architecture, Discovery Loops & PVI Specs
* **Vishesh:** Agent Orchestration, Defensive SSRF/DNS-Rebinding Engine & FastAPI
* **Vinayak Navneet Kothari:** AI/ML, CLIP Embeddings, Gemini Taxonomy & pgvector HNSW
* **Arnev Malik:** Frontend, Next.js Merchant Dashboard & Proof Verification UI

---

## 🛡️ Compliance Guardrail
TrendRadar traverses public-facing content streams only; no login-gated or authenticated boundaries are breached. Active rate-limiters are integrated throughout to strictly respect host platform `robots.txt` routing protocols.
