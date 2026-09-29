# Artificialss

**Software & AI Ethical Labs**

An applied AI research and product laboratory deploying frontier agentic AI with measurable social benefit, a transparent ecological footprint, and ethical constraints. Every initiative we ship is evaluated against three criteria: technical merit, measurable social benefit, and a transparent ecological footprint.

We build for the people and places frontier technology usually skips.

## Portfolio

### Products
| Product | What it is | Status |
|---|---|---|
| [Papasar.cr](https://papasar.cr) | Free standardized-test and university-admission preparation for Costa Rican students (iOS, Android, Web) | Live |
| Leyreal.com | Free AI legal review and document scanning under Costa Rican law | Coming soon |
| [CryptoAlly.dev](https://www.cryptoally.dev) | Live, free portfolio tracking for cryptocurrency and equities (Android, iOS, Web) | Live (alpha) |
| [Antiquantum.eco](https://antiquantum.eco) | Post-quantum cryptography and AI-powered field hardware for ecological data | Live (alpha) |
| [Marca.eco](https://profiles.eco/marca) | Open registry for protected ecological land | Live (alpha) |

### Services
- **AI-powered software development**: design, prototyping, modernization and data engineering.
- **Data engineering**: turning scattered, undocumented public sources into clean, structured, continuously verified datasets.
- **Linguistic audit**: turnkey workflows to migrate organizational documentation to new style and compliance standards (APA, ISO, inclusive language). In development.
- **Legal advisory**: Costa Rican residency, real estate, labor law and corporate formation.
- **Education**: AI literacy, context engineering and production agentic workflows.

## How we build

We ship production software with AI-assisted engineering under a strict architecture spec, then hold the result to the same standard as any hand-written codebase: real patterns, live APIs, no placeholders and no shortcuts.

### Architecture
Clean and hexagonal architecture across every stack. Domain logic sits at the center with no I/O; use cases and ports define what the system needs; adapters (databases, HTTP, UI) plug in at the edges. Dependencies point inward only, so a database, a provider or a UI framework can change without touching the business rules.

### Mobile
Kotlin Multiplatform and Compose Multiplatform give us Android, iOS and Web from one codebase, with MVVM, `StateFlow`, Koin dependency injection, type-safe Navigation and Room for local data. Where a platform deserves it we go native: Swift and SwiftUI on iOS, Jetpack Compose on Android. Our showcase apps demonstrate the same patterns on each platform.

### Frontend
Next.js (App Router) and TypeScript for marketing sites and dashboards, with server and client component boundaries kept explicit, theming and font optimization built in, and hand-built UI primitives instead of heavy dependency trees. Sites are SEO-ready (structured data, sitemaps, canonical URLs) and rate-limit their data-heavy pages. We are also building **Dioxus** frontends in Rust, sharing typed request and response models with the API.

### Backend
Rust services built in layers that depend inward only, as in our production CryptoAlly API:
- `domain`: entities, newtypes (an asset id, a market slug, a plaintext API key and a stored key hash are all distinct types) and repository traits. It knows nothing about HTTP or Postgres.
- `application`: thin services that orchestrate the ports.
- `infrastructure`: the Postgres implementations, using **sqlx** with parameterized queries only, so SQL injection is ruled out by construction.
- `http`: one **axum** `Router` that serves every route, with authentication as a single middleware layer instead of code repeated per handler, and errors mapped in one place.

Security is designed in: API keys are random opaque tokens and only their SHA-256 hash is stored, so a key can be revoked instantly and a database leak exposes no usable key. The runtime database credential is read-only and separate from the one used by data ingestion, which runs out of band, and the API exposes no write endpoint at all. Clients, browsers and mobile apps never connect to a database directly. The API is the only gatekeeper. Because the domain is defined by traits, the whole HTTP layer (routing, auth, status codes and JSON shape) is tested end to end against in-memory fakes, with no database in the test process.

### Serverless
Deployed on **Vercel** with the official Rust runtime (`vercel_runtime` with axum, one function serving the whole router) and Fluid Compute, backed by **Neon** serverless Postgres (pooled connections for the application, direct connections for migrations). Preview deployments per pull request, environment variables managed through the platform, and no servers of our own to patch.

### Deployment, analytics and auth
- **Deployment:** Vercel for web and API. Every pull request gets a preview deployment, production ships from `main`, and configuration and secrets live in the platform's environment management. Rust services run on Vercel's Rust runtime; Next.js sites use the App Router on Fluid Compute.
- **Analytics:** Firebase Analytics (GA4) and Vercel Web Analytics side by side. Page views are captured automatically, and a single tracking helper sends the same custom event name to both, so the two dashboards always agree. Sites that host data-heavy pages add per-IP rate limiting that does not block search crawlers.
- **Auth and managed backend:** Supabase or Firebase, chosen per product. Supabase gives us Postgres with row-level security, auth and storage; Firebase gives us auth, analytics, messaging and app distribution on mobile. Where the API is the only gatekeeper to the data, as in our Rust services, we use API-key authentication instead and keep the database off the public internet.

### SQL and data modeling
Postgres is the system of record. Schemas are versioned migrations, relationships use real foreign keys instead of fuzzy matching, and JSON Schema validates every record before it is loaded. Where Postgres fits better than a hosted BaaS we choose Neon; where a full backend platform helps (auth, storage) we use Supabase or Firebase.

### Data engineering with Python
Many of our products depend on data that does not exist in a usable form, so we build the pipeline ourselves in Python:

1. **Enumerate.** Find out what exists before collecting it. Crawls are seeded from an official search index, not only from links between records, after we found that following links alone reached about a quarter of a national law corpus.
2. **Fetch.** Polite, rate-limited clients that call only the endpoints a site's own front end uses, retry with back-off, and never bypass access controls. A failure on one fragment is isolated and flagged instead of losing the whole record.
3. **Parse.** Extract structure (articles, relations, metadata) from HTML, PDFs and public APIs, and fix encoding problems at the source.
4. **Validate.** Every record is checked against a JSON Schema, plus content checks for defects a schema cannot see: corrupted text, placeholder articles, duplicates, and counts that disagree with the official source.
5. **Classify and link.** Records are tagged against a fixed taxonomy and their cross-references are resolved to real identifiers.
6. **Refresh.** A worker re-checks the oldest records first and records a freshness timestamp, so changes at the source are picked up continuously.
7. **Audit and document.** Coverage audits, known gaps and methodology are written down next to the data. Quality problems are labeled, never silently discarded, so downstream consumers, including our AI agents, can decide how much to trust each record.
8. **Load and serve.** Clean data is loaded into Postgres and exposed only through our Rust APIs.

### Full-stack Rust
Our newer products are Rust end to end. A Cargo workspace splits the project into crates that mirror the architecture: `domain`, `application` (use cases and ports), `adapters-db` (sqlx), `api` (axum, the composition root), `shared` (DTOs used by both sides) and `web` (Dioxus). The compiler enforces the dependency rules, the frontend and the API share one set of types, and the whole stack builds, lints and tests in a single CI pipeline.

### R&D: cryptography, crypto integrations and post-quantum security
Our research lab works on the cryptography that other products depend on, and we use Rust as the language to prototype and implement it.

- **Post-quantum signatures.** Antiquantum protects its conservation land registry with hash-based signatures (LMS and XMSS), whose security rests on hash functions instead of the number-theoretic problems that quantum computers threaten. We research how to build them safely, including the hard part of stateful schemes: never reusing a one-time key, and keeping signing state consistent across restarts and failures. Hashing uses SHA-512.
- **Physical entropy.** Randomness is the foundation of every key. We research entropy generation from biological sources, living hive colonies in the field, and how to condition, test and combine it with system randomness so a weak source can never weaken the result.
- **Crypto integrations.** Token validation SDKs and on-chain verification for the Proof of Pollination registry (verification on chain is coming soon), plus market data for crypto assets through CryptoAlly, including the hashed API-key scheme and distinct types for plaintext keys and stored hashes, so secrets cannot be mixed up by mistake.
- **Why Rust.** Memory safety without a garbage collector, strong types for keys and signatures that cannot be mixed up, and `unsafe` code forbidden by default in our workspaces. Rust also compiles to WebAssembly, so the same verification logic can run in the API, in the browser and in mobile apps.
- **How we work.** Standard, peer-reviewed primitives only; we do not invent our own algorithms. Test vectors from the specifications, property tests and constant-time considerations come first; independent review comes before anything protects real assets. This is research and engineering in progress, not an audited product.

### AI
We use Claude across the stack, from engineering workflows to grounded, sourced answers in our own products. AI features are built with guardrails for off-topic and sensitive queries, and answers are anchored to verified sources rather than free-form generation.

### Engineering practices
- Gitflow with protected `main` and `dev` branches. Every change lands through a reviewed pull request with passing CI.
- Formatting, linting and tests enforced in continuous integration.
- Documentation lives with the code: architecture, dependencies and usage for every repository.
- Ethics is part of the definition of done: technical merit, measurable social benefit and a transparent ecological footprint.

## Working with us

### Engagement models

**Software development.** AI-powered software development, designed to be handed off: product design, prototyping, MVPs, modernization and data engineering. Full-stack across web, mobile and AI integration, with the same team and workflow for every client. Final rates are tailored to project scope and engagement length; contact us for a proposal.

| | Costa Rica | International (U.S. priority) |
|---|---|---|
| **Structure** | Flat monthly rate: predictable, no hidden fees | Direct 1099 contractor relationship with clean tax documentation |
| **Scope** | Full-stack development: web, mobile and AI integration | Senior, AI-powered engineering output, led from the U.S. |
| **Compliance** | SICOP vendor registration for public-sector projects | 1099-NEC issued at year end; no W-8BEN forms |
| **Cost** | Tailored per project | 35-50% savings vs. California and Delaware senior engineer salaries |
| **On-site work** | In person across Costa Rica | In person worldwide; the client covers the flights |

**In-person and worldwide.** Our team works on site with clients anywhere in the world, for build sprints, workshops, architecture reviews and team onboarding. For international in-person engagements, we ask the client to cover the flights; other travel details are agreed in the proposal. Remote engagements need no travel.

**Vibe Sessions.** Hands-on working sessions in three tracks: *Vibe Coding* (web, Android, iOS and Kotlin Multiplatform with Firebase or Supabase), *Vibe UI Design* (Figma AI prototypes and design systems) and *Vibe Product Design* (architecture and platform strategy). Book privately for a 1:1 Vibe Sprint, from idea to deployed product in 4 hours, or as a group of up to 8. You receive a full session summary and your deliverable (source code, design files or a product spec) within 24 hours, under NDA.

**Legal advisory.** Direct introductions to independent, licensed Costa Rican attorneys, supported by AI-assisted guides, for residency, real estate, corporate formation, family and labor matters. Available in English and Spanish, for local and international clients. We connect you with counsel; we do not provide legal representation ourselves.
- Legal info request: free, with a written response and no call required
- Quick consultation: $20 for 30 minutes
- Full advisory hour: $40 for 1 hour
- Contact: [legal@artificialss.ai](mailto:legal@artificialss.ai)

**Academy.** Structured programs in Spanish (English on request) for educators and students, inclusive language, and professional and technical teams: context engineering, agentic coding and agentic workflow design. Two-hour workshops and a four-week intensive, in person in San Jose or online. Groups of 10 or more receive a discount and priority scheduling. Built for Costa Rica and Latin America. Contact: [academy@artificialss.ai](mailto:academy@artificialss.ai)

## Contact

| | |
|---|---|
| **Website** | [artificialss.ai](https://artificialss.ai/) |
| **Start a project or book a session** | [artificialss.ai/contact](https://artificialss.ai/contact) |
| **General** | [info@artificialss.ai](mailto:info@artificialss.ai) |
| **Legal advisory** | [legal@artificialss.ai](mailto:legal@artificialss.ai) |
| **Academy** | [academy@artificialss.ai](mailto:academy@artificialss.ai) |
| **LinkedIn** | [linkedin.com/company/artificialss](https://www.linkedin.com/company/artificialss/) |
| **GitHub** | [github.com/Artificialss](https://github.com/Artificialss) |
| **X** | [@ArtificialssAI](https://x.com/ArtificialssAI) |
| **YouTube** | [@Artificialss](https://www.youtube.com/@Artificialss) |
| **Headquarters** | Turrialba, Costa Rica |
