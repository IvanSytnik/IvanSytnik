# Ivan Sytnik
**Full-Stack & Backend Engineer** · TypeScript · Next.js · Node.js · Python
Graz, Austria · Open to Remote (Europe/Vienna ±2h) & B2B Contracts
🌐 [sytnik-studio.com](https://sytnik-studio.com) · [LinkedIn](https://linkedin.com/in/ivan-sytnik) · [ivan.sytnik02@gmail.com](mailto:ivan.sytnik02@gmail.com)

I build and ship production web systems and resilient backend services, focusing on concurrency-safe data operations, verifiable backend invariants, and deterministic AI pipelines.

---

### 🌟 Selected Projects

#### 1. [Restaurant CRM & Booking Engine](https://github.com/IvanSytnik/restaurant-crm) — [Live Demo ↗](https://restaurant.sytnik-studio.com)
* **Problem:** An Austrian restaurant needed an in-house reservation platform to replace recurring per-cover fees and prevent double-booking across a multilingual staff (`DE`/`EN`/`UK`).
* **My Role:** Sole engineer — responsible for data modeling, reservation logic, UI, and deployment.
* **Technical Solution:** PostgreSQL transactional advisory locks serialize conflicting table-allocation requests. Reservation slots are generated in the `Europe/Vienna` timezone, with DST transitions covered by tests.
* **Verification:** Runs in daily production and is covered by 58 Vitest tests, including concurrency and DST checks executed with the host timezone set to `America/New_York`.
* *Stack: Next.js 15, TypeScript, PostgreSQL (Neon), Prisma, Tailwind CSS, Vitest*

#### 2. [DealRadar — Marketplace Valuation Bot](https://github.com/IvanSytnik/dealradar) — [Live Telegram Bot ↗](https://t.me/dealradar_austria_bot)
* **Problem:** Blended price medians on marketplaces conflate distinct hardware tiers (e.g. PS5 Digital Edition vs. PS5 Pro), producing false discount alerts.
* **My Role:** End-to-end design and implementation: scraping queues, LLM evaluation contour, and AWS deployment.
* **Technical Solution:** A three-stage filtering pipeline combines lexicon rules, per-watch rules, and batched Anthropic classification under a daily user budget. The system calculates medians per hardware model and includes a transactional data-erasure flow designed to support GDPR Article 17 requests.
* **Verification:** 262 Vitest tests covering parser health alerts, per-host request throttling with jitter, and scheduler state machines.
* *Stack: TypeScript, Node.js 22, grammY, AWS (EC2, S3, CloudFront), Terraform, Docker*

#### 3. [Universal Media Downloader](https://github.com/IvanSytnik/Universal-Media-Downloader) — Async Processing Core
* **Problem:** Synchronous media extraction (`yt-dlp`) blocks asyncio event loops, while the hosted Telegram Bot API limits bot uploads to 50 MB.
* **My Role:** Backend architecture and open-source core implementation.
* **Technical Solution:** Clean Architecture with a zero-dependency domain; isolates media extraction in dedicated worker processes (`multiprocessing.Process`) that can be forcibly terminated on timeout; a self-hosted Telegram Bot API container sharing a Docker volume with the worker lifts upload limits up to 2000 MB.
* **Verification:** 343 tests with a 90% coverage gate on core layers; AST-based tests enforcing architectural layer boundaries in CI.
* *Stack: Python 3.13, aiogram 3, arq, Redis 7, PostgreSQL 16, SQLAlchemy 2, Docker*

---

### 🔬 Additional Architectural Systems

<details>
<summary><b>ShopSmart AI — Grounded Grocery Planner & Cost-Bounded LLM</b></summary>

* **Problem:** Unconstrained LLMs invent prices and nutritional values, making budget limits unreliable.
* **Technical Solution:** OpenAI outputs are restricted to per-request candidate ID enums; FastAPI computes pricing, portion scaling, and budget trimming deterministically from a dated catalog.
* **Verification:** 451 automated tests (359 backend pytest + 92 frontend Vitest). In a 20-scenario offline evaluation, all plans stayed within budget and no diet-rule violations were observed. Reported p50 latency: 4.09s; average cost: $0.00108 per request (see `backend/evals/report.md` for methodology).
* *Stack: Python 3.11+, FastAPI, React 18, TypeScript, Docker, Cloud Run*
* *Links:* [GitHub Repo](https://github.com/IvanSytnik/shopsmart-ai) · [Live App ↗](https://shopsmart.sytnik-studio.com)

</details>

<details>
<summary><b>EnglishLearn — Adaptive Language Learning Platform</b></summary>

* **Problem:** Traditional language apps lack structural knowledge tracing, failing to address specific prerequisite gaps.
* **Technical Solution:** 3-layer learner model (DAG prerequisite graph, BKT+ with IRT 2PL, FSRS spaced repetition) with a Thompson Sampling selection policy over an append-only event-sourced log.
* **Verification:** 158 tests across the model package, including property-based tests via `fast-check` to verify DAG acyclicity and state-fold invariants.
* *Stack: Next.js 16, TypeScript, Turborepo, Prisma, PostgreSQL (Neon), fast-check, Vitest*
* *Links:* [GitHub Repo](https://github.com/IvanSytnik/english-learn) · [Preview Deployment ↗](https://englishlearn.sytnik-studio.com)

</details>

<details>
<summary><b>StyleMe — AI Hairstyle Try-On SaaS</b></summary>

* **Problem:** The app needed to prevent replaying rewarded-credit claims without trusting client-side state.
* **Technical Solution:** Server-authoritative daily allowances, Supabase ES256 JWKS authentication, and single-use nonces burned atomically via Redis `DEL`.
* **Verification:** Dual-backend contract tests validating identical behavior across local fallbacks and Upstash Redis.
* *Stack: Next.js 16, Express, TypeScript, Supabase, Upstash Redis, Replicate, Vitest*
* *Links:* [GitHub Repo](https://github.com/IvanSytnik/styleme) · [Preview ↗](https://styleme.sytnik-studio.com)

</details>

---

### 💼 Commercial Delivery & Background

* **Independent Full-Stack Delivery ([Sytnik Studio](https://sytnik-studio.com)):** Providing end-to-end web engineering for small businesses across Austria, Germany, and Ukraine (B2B contracts).
* **Commercial Systems:** Delivered **[MedConsult Pro](https://github.com/IvanSytnik/medconsult-pro)** ([Live ↗](https://medconsult.sytnik-studio.com)), a multilingual lead-generation platform with dual Telegram and SMTP notification channels.
* **Teaching & Mentorship:** Former Teaching Assistant at **ROBOCODE** (Villingen-Schwenningen, Germany), teaching programming, C++, and robotics to students aged 7–14.
* **Education:** **MSc** (2025) and **BSc** in Computer Science, NTU "Kharkiv Polytechnic Institute".

---

### 🛠️ Core Tech Stack

* **Languages:** TypeScript, JavaScript, Python 3.13, SQL
* **Frontend:** React, Next.js (App Router), Tailwind CSS, TanStack Query, Zustand, next-intl
* **Backend:** Node.js, Express, FastAPI, aiogram 3, arq, PostgreSQL, Prisma, SQLAlchemy 2, Redis
* **DevOps & Cloud:** Docker, AWS (EC2, S3, CloudFront), Terraform, GitHub Actions, Vercel
* **Testing:** Vitest, pytest, Playwright, fast-check
