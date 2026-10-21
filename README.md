# Ivan Sytnik

**Full-Stack Software Engineer (TypeScript · Next.js · Node.js · Python)**  
📍 Graz, Austria · Open to remote, hybrid, relocation (DACH/EU), and B2B contracts  
🌐 [**Portfolio & Studio (sytnik-studio.com)**](https://sytnik-studio.com) · [**LinkedIn**](https://www.linkedin.com/in/ivan-sytnik/) · [**ivan.sytnik02@gmail.com**](mailto:ivan.sytnik02@gmail.com)

I design and ship end-to-end web applications and AI-enabled backend systems where real business constraints require **verifiable backend invariants** rather than happy-path prototypes.

---

## What I Build & Services

If you are a founder, B2B client, or engineering team looking to ship production systems:
- **Web Applications & SaaS:** Production-ready architectures with Next.js, Node.js, and Python, complete with auth, multi-locale support, and CI.
- **Booking & CRM Systems:** Custom-built reservation flows, table allocation, and role-based management dashboards.
- **Controlled AI / LLM Integration:** Bounded pipelines where deterministic code enforces prices, budgets, and quotas, while models handle classification and extraction.
- **Scraping & Async Pipelines:** Resilient web parsers, background job queues, and process-isolated media processing workers.

---

## Featured Projects

### [Restaurant CRM](https://github.com/IvanSytnik/restaurant-crm) — Custom Reservation System & Public Site | [Live Demo ↗](https://restaurant.sytnik-studio.com)
* **Business Value:** Built for an Austrian restaurant to replace recurring per-cover SaaS fees, retain full ownership of guest data, and empower a multilingual staff (`DE`/`EN`/`UK`).
* **Architecture:** 15-minute slot generator and best-fit table allocator guarded against race conditions by PostgreSQL transactional advisory locks (`pg_advisory_xact_lock`).
* **Verification:** Role-based access (`OWNER`/`MANAGER`/`STAFF`), 30-second floor plan polling, and **58 unit tests** forcing host timezone to `America/New_York` to prove `Europe/Vienna` DST safety.

`Next.js 15 · TypeScript · PostgreSQL (Neon) · Prisma · NextAuth · next-intl · Resend · Vitest · Vercel`

### [DealRadar](https://github.com/IvanSytnik/dealradar) — Marketplace Deal-Finder & Valuation Bot | [Live Bot ↗](https://t.me/dealradar_austria_bot)
* **Business Value:** Automated Telegram monitoring of **willhaben.at** 🇦🇹 and **kleinanzeigen.de** 🇩🇪 searches, scoring deals against per-model market medians instead of flawed blended averages.
* **Architecture:** 3-layer filtering pipeline (lexicon rules $\rightarrow$ custom watch rules $\rightarrow$ batched Anthropic LLM classification under a strict daily user budget).
* **Verification:** Polite per-host queues with jittered backoff, rolling-window parser health alerts, single-transaction data erasure designed for GDPR Art. 17 workflows, and **262 Vitest tests**.

`TypeScript · Node.js 22 · grammY · Anthropic LLM · Zod · SQLite · Vitest · Docker · AWS · Terraform`

### [ShopSmart AI](https://github.com/IvanSytnik/shopsmart-ai) — Grounded Supermarket Planner | [Live App ↗](https://shopsmart.sytnik-studio.com)
* **Business Value:** Weekly grocery and meal planning for Austrian supermarkets (**Billa**, **Hofer**), featuring server-enforced budget limits and deterministic nutrition calculations.
* **Architecture:** The LLM selects product IDs from a per-request JSON-schema enum; FastAPI calculates prices and nutrition from a dated product catalog, adjusts portions, and trims non-essential items to enforce the configured budget limit.
* **Verification:** Covered by **359 backend pytest + 92 frontend Vitest tests**. Evaluated across 20 fixed scenarios: **100% budget adherence, 0 diet violations, 4.09s p50 latency, $0.00108/req**.

`Python 3.11+ · FastAPI · OpenAI Structured Outputs · React 18 · TypeScript · Vite · pytest · Cloud Run`

### [Universal Media Downloader](https://github.com/IvanSytnik/Universal-Media-Downloader) — Async Media Processing Core (★ 14)
* **Business Value:** Resilient asynchronous backend core for downloading media from YouTube, TikTok, Instagram, and X/Twitter past Telegram's 50 MB limits.
* **Architecture:** Strict Clean Architecture (10 domain ports) where `aiogram 3` handlers and `arq` workers act as thin entrypoints into shared use cases.
* **Verification:** Subprocess isolation (`multiprocessing.Process`) for blocking `yt-dlp` calls, Redis pub/sub progress streaming, atomic `GETDEL` tokens, and **314 tests**.

`Python 3.13 · aiogram 3 · arq · yt-dlp · FFmpeg · SQLAlchemy 2 · PostgreSQL 16 · Redis 7 · Docker`

---

## Architectural Experiments & Pre-Launch Platforms

- **[EnglishLearn](https://github.com/IvanSytnik/english-learn)** — Adaptive English learning platform featuring a standalone 3-layer mathematical learner model (DAG prerequisite graph, BKT+, IRT 2PL, FSRS spaced repetition, Thompson Sampling) built on an append-only event-sourced log. Verified by **158 unit and property-based tests**, including property-based checks with `fast-check`. *[Preview Deployment ↗](https://english-learn.sytnik-studio.com)*
- **[StyleMe](https://github.com/IvanSytnik/styleme)** — AI hairstyle try-on SaaS monorepo. Features server-authoritative quotas, JWKS Supabase auth, and an ad-fraud prevention contour for rewarded credits using atomic Redis nonces (`DEL` single-use burn). Verified by **43 tests** (including dual-backend Upstash Redis contract tests). *[Preview ↗](https://styleme.sytnik-studio.com)*

---

## Engineering Principles (What I Optimize For)

- **LLMs Bounded by Deterministic Code:** Models classify text or pick IDs via JSON-schema enums; server code calculates prices, budgets, and quotas.
- **Concurrency & Process Safety:** PostgreSQL advisory locks (`pg_advisory_xact_lock`), atomic Redis nonces (`GETDEL`/`DEL`), and isolated OS subprocesses (`multiprocessing.Process`).
- **Strict Boundaries & Testability:** Clean Architecture ports, pure event-sourced state folds, property-based testing (`fast-check`), and dual-backend contract tests.
- **European Production Readiness:** Multi-locale i18n (`DE`/`EN`/`UK`/`RU`), `Europe/Vienna` DST-safe scheduling, EU allergen models, and structured data-erasure paths.

---

## Client Work & Background

- **Independent Full-Stack Delivery ([Sytnik Studio](https://github.com/IvanSytnik/sytnik-studio) — [sytnik-studio.com](https://sytnik-studio.com)):** Full-stack contract engineering for clients in Austria and Germany (registered sole proprietorship, EU B2B reverse-charge ready). Built with Next.js 15, Drizzle/Neon, no-JS progressive enhancement, and localized legal pages (`Impressum`, `Datenschutzerklärung`).
- **Commercial Client Delivery:** Built **[MedConsult Pro](https://github.com/IvanSytnik/medconsult-pro)** ([medconsult-pro.sytnik-studio.com](https://medconsult-pro.sytnik-studio.com)), a 4-locale medical-tourism lead-generation platform with dual Telegram and SMTP routing.
- **Teaching & Mentorship:** Former Teaching Assistant at **ROBOCODE** (Villingen-Schwenningen, Germany), teaching robotics and programming to kids aged 7–14.
- **Education:** **MSc** (2025) and **BSc** in Computer Science, NTU "Kharkiv Polytechnic Institute" (KhPI).

---

## Core Technical Stack

- **Frontend & Monorepo:** TypeScript, React 18/19, Next.js 15/16, Tailwind CSS, TanStack Query, Zustand, `next-intl`, Turborepo, pnpm Catalogs.
- **Backend & Data:** Node.js, Express, Python, FastAPI, aiogram, grammY, arq, PostgreSQL (Neon, Supabase), Prisma, Drizzle, SQLAlchemy, Redis/Upstash, Zod, Pydantic, Sharp, FFmpeg.
- **AI & Infrastructure:** OpenAI SDK, Anthropic Claude, Replicate, AWS (EC2, S3, CloudFront, Terraform), Google Cloud Run, Vercel, Docker, GitHub Actions CI, Vitest, pytest, Playwright.
