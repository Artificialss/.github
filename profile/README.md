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
- **Clean and hexagonal architecture** across every stack. Domain logic sits at the center with no I/O; use cases and ports define what the system needs; adapters (databases, HTTP, UI) plug in at the edges. Dependencies point inward only.
- **Mobile and multiplatform:** Kotlin, Compose Multiplatform and Kotlin Multiplatform for Android, iOS and Web from a single codebase; native Swift and SwiftUI and Jetpack Compose where a platform deserves it. MVVM with StateFlow, Koin dependency injection, type-safe Navigation, Room for local data.
- **Web:** Next.js (App Router) and TypeScript with hand-built UI primitives and a deliberately small dependency footprint.
- **Backend:** Rust (axum, sqlx, Dioxus) on Vercel and Neon Postgres, alongside Supabase and Firebase where they fit; Python for data work and tooling.

### Data engineering
Many of our products depend on data that does not exist in a usable form. We reverse-engineer legacy systems, crawl public sources, and turn them into clean, structured, continuously verified datasets. Each dataset ships with its methodology, coverage audits and known gaps documented, so downstream products, including our AI agents, can cite their sources.

### AI
We use Claude across the stack, from engineering workflows to grounded, sourced answers in our own products. AI features are built with guardrails for off-topic and sensitive queries, and answers are anchored to verified sources rather than free-form generation.

### Engineering practices
- Gitflow with protected `main` and `dev` branches. Every change lands through a reviewed pull request with passing CI.
- Formatting, linting and tests enforced in continuous integration.
- Documentation lives with the code: architecture, dependencies and usage for every repository.
- Ethics is part of the definition of done: technical merit, measurable social benefit and a transparent ecological footprint.

## Contact
[artificialss.ai](https://artificialss.ai/) · info@artificialss.ai · Turrialba, Costa Rica
