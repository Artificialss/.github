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
Rust services with a hexagonal core: **axum** for HTTP, **sqlx** for compile-time-checked SQL, and typed errors from the domain out to the wire. Endpoints sit behind API-key authentication (only a hash of each key is stored), and clients, browsers and mobile apps never connect to a database directly. The API is the only gatekeeper.

### Serverless
Deployed on **Vercel** with the official Rust runtime and Fluid Compute, backed by **Neon** serverless Postgres (pooled connections for the application, direct connections for migrations). Preview deployments per pull request, environment variables managed through the platform, and no servers of our own to patch.

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

### AI
We use Claude across the stack, from engineering workflows to grounded, sourced answers in our own products. AI features are built with guardrails for off-topic and sensitive queries, and answers are anchored to verified sources rather than free-form generation.

### Engineering practices
- Gitflow with protected `main` and `dev` branches. Every change lands through a reviewed pull request with passing CI.
- Formatting, linting and tests enforced in continuous integration.
- Documentation lives with the code: architecture, dependencies and usage for every repository.
- Ethics is part of the definition of done: technical merit, measurable social benefit and a transparent ecological footprint.

## Contact
[artificialss.ai](https://artificialss.ai/) · info@artificialss.ai · Turrialba, Costa Rica
