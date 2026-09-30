# Artificialss

**Software & AI Ethical Labs**

An applied AI research and product laboratory deploying frontier agentic AI with measurable social benefit, a transparent ecological footprint, and ethical constraints. Every initiative we ship is evaluated against three criteria: technical merit, measurable social benefit, and a transparent ecological footprint.

We build for the people and places frontier technology usually skips.

## Portfolio

### Products
| Product | What it is | Stack | Status |
|---|---|---|---|
| [Papasar.cr](https://papasar.cr) | Free standardized-test and university-admission preparation for Costa Rican students (iOS, Android, Web) | Compose Multiplatform app (Android, iOS, Web), Next.js site, Firebase, Supabase, Vercel | Open Beta |
| Leyreal.com | Free AI legal review and document scanning under Costa Rican law | Compose Multiplatform apps (Android, iOS, Web); Rust (axum, sqlx), Dioxus and Neon platform in development | Coming soon |
| [CryptoAlly.dev](https://www.cryptoally.dev) | Live, free portfolio tracking for cryptocurrency and equities (Android, iOS, Web) | Kotlin and Compose Multiplatform app, Rust API (axum, sqlx, Neon), Dioxus, Supabase, Firebase, Vercel | Live (alpha) |
| [Antiquantum.eco](https://antiquantum.eco) | Post-quantum cryptography and AI-powered field hardware for ecological data | Astro, Firebase, Supabase, cPanel hosting | Live (alpha) |
| [Marca.eco](https://profiles.eco/marca) | Open registry for protected ecological land | Astro, Firebase, Supabase | Coming soon |

### Services
- **AI-powered software development**: design, prototyping, modernization and data engineering.
- **Data engineering**: turning scattered, undocumented public sources into clean, structured, continuously verified datasets.
- **Documentation audit and migration (linguistic audit)**: turnkey workflows that audit organizational documentation and migrate it to new style and compliance standards (APA, ISO, inclusive language), including institutional manuals and MCP integration. Available now.
- **Legal advisory**: Costa Rican residency, real estate, labor law and corporate formation.
- **Education**: AI literacy, context engineering and production agentic workflows.

### Showcase
Open-source reference projects, one per platform:
- **Rust:** [cryptoally-api](https://github.com/Artificialss/cryptoally-api), a production Rust API with clean architecture
- **Web:** [showcase-nextjs](https://github.com/Artificialss/showcase-nextjs), Next.js and TypeScript
- **Android:** [showcase-android](https://github.com/Artificialss/showcase-android), Kotlin and Jetpack Compose
- **iOS:** [showcase-ios](https://github.com/Artificialss/showcase-ios), Swift and SwiftUI
- **Multiplatform:** [showcase-cmm](https://github.com/Artificialss/showcase-cmm), Compose Multiplatform

## How we build

We ship production software with AI-assisted engineering under a strict architecture spec, then hold the result to the same standard as any hand-written codebase: real patterns, live APIs, no placeholders and no shortcuts.

**Spec first.** Every project starts with a written architecture spec: the layers, the dependency rules, the patterns (MVVM, dependency injection, ports and adapters), the data sources and the acceptance criteria. AI agents build inside that spec, so the design decisions are made by people up front instead of being improvised line by line.

**Real, end to end.** Our showcase apps were built end to end with Claude Code under exactly this kind of spec: real navigation, real state management, real local storage and live APIs. If a feature is on screen, it works. We do not ship mocked data, stubbed screens or TODO placeholders as if they were finished.

**Held to the hand-written standard.** Generated code goes through the same gates as any other: typed boundaries, formatting and linting, automated tests, security review, and a pull request that a person reads and approves. Speed comes from the tooling; accountability stays with the engineers.

**Designed to be handed off.** Clients get source code, architecture documentation, dependency lists, usage guides and migrations, so a team can take over without us. Documentation is audited as carefully as code: style and compliance standards (APA, ISO, inclusive language) are applied and verified, and existing documentation can be migrated to them with our audit workflows.

**Built to evolve.** Layers depend inward only, so databases, providers and UI frameworks can change without rewriting the business rules. Data ships with its methodology, coverage audits and known gaps documented, and schemas change only through versioned migrations.

### Architecture
There is no single right architecture, so we work with the one that fits the client, the team and the stage of the product. We build and maintain projects in any of these, and we adapt to a client's existing conventions and requirements instead of imposing our own:

| Pattern | What it is | Where it fits |
|---|---|---|
| **MVC** (Model-View-Controller) | The controller mediates between the model and the view | Server-rendered web apps and classic frameworks |
| **MVP** (Model-View-Presenter) | A presenter holds the UI logic and the view stays passive | Android and iOS apps that need highly testable screens |
| **MVVM** (Model-View-ViewModel) | Observable state (`StateFlow`, Observable) bound to the view | Compose, SwiftUI and reactive UIs |
| **MVI** (Model-View-Intent) | Unidirectional data flow: user intents in, immutable state out | Complex screens where predictable state matters |
| **Clean architecture** | Concentric layers (domain, use cases, data) with dependencies pointing inward | Products that will grow and outlive their frameworks |
| **Hexagonal** (ports and adapters) | The core defines ports; databases, HTTP and UIs plug in as adapters | Backends and integrations, our default for Rust services |

The principle underneath is the same in all of them: business rules do not depend on frameworks. Domain logic sits at the center with no I/O, use cases and ports define what the system needs, and adapters (databases, providers, UI) plug in at the edges with dependencies pointing inward only. A database, a provider or a UI framework can then change without touching the business rules.

**Architecture migrations.** Many projects begin as a prototype or a minimum viable product built for speed, and then hit the limits of that shortcut. We take these projects to a professional footing without a rewrite from zero: we audit the current structure, agree the target architecture, and migrate in safe increments while the product keeps shipping. Typical moves:
- From an MVP (Minimum Viable Product), the first version built for speed, to a layered, tested, production-grade codebase.
- From MVC (Model-View-Controller) or MVP (Model-View-Presenter) to MVVM (Model-View-ViewModel) or MVI (Model-View-Intent), with predictable state and testable screens.
- From a monolith or a tightly coupled backend to clean or hexagonal architecture, with ports around the database and the third-party services.
- From ad hoc data access to versioned schema migrations and typed API boundaries.
- Adding dependency injection, automated tests and CI around code that already works, so it becomes safe to change.

Each migration comes with the architecture documentation, so your team owns the result.

### Mobile
We build mobile apps the way each product needs them: native on each platform, or multiplatform from one codebase.

- **Native Android.** Kotlin and Jetpack Compose with MVVM and clean architecture, coroutines and `StateFlow`, dependency injection (Koin, Dagger and Hilt), Room for local data, Retrofit, Ktor and GraphQL for networking, and Material Design 3. In-app purchases, subscriptions and ads, released to Google Play.
- **Native iOS.** Swift and SwiftUI with MVVM and the modern Observable state pattern, Xcode tooling, and Objective-C and UIKit codebases maintained and modernized when a product depends on them. Released to the App Store.
- **Multiplatform.** Kotlin Multiplatform and Compose Multiplatform give us Android, iOS and Web from one codebase, with shared business logic, type-safe navigation and Room. We also work with Flutter and Dart (BLoC) when a team already uses them.

**Migration and upgrade service.** Mobile apps age quickly: platform requirements change, libraries are deprecated and old architectures slow every release. We modernize live apps in safe, incremental steps while they keep shipping, with unit tests around every change and no big-bang rewrite. Typical work:
- **UI:** XML/View system to Jetpack Compose, and UIKit to SwiftUI, screen by screen.
- **Language:** Java to Kotlin, and Objective-C to Swift.
- **Architecture:** MVP (Model-View-Presenter) or MVC (Model-View-Controller) to MVVM (Model-View-ViewModel) with clean architecture, and Observables and callbacks to coroutines and `StateFlow`.
- **Platform upgrades:** new Android and iOS releases and store requirements, such as Edge-to-Edge display on Android, plus SDK and dependency upgrades.
- **Cross-platform moves:** legacy stacks such as Xamarin to native or Kotlin Multiplatform, and shared code extracted so Android and iOS stop duplicating logic.
- **Foundations:** dependency injection, repository patterns, automated tests, CI and release automation added around code that already works.

Our showcase apps demonstrate the same patterns on each platform.

### Frontend
Next.js (App Router) and TypeScript for marketing sites and dashboards, with server and client component boundaries kept explicit, theming and font optimization built in, and hand-built UI primitives instead of heavy dependency trees. Sites are SEO-ready (structured data, sitemaps, canonical URLs) and rate-limit their data-heavy pages. We also build **Dioxus** frontends in Rust that compile to **WebAssembly**, sharing typed request and response models with the API, on top of solid semantic HTML and CSS.

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
- **Deployment:** each product goes where it fits. **Vercel** hosts our Next.js sites, the Dioxus web apps and the Rust APIs, with a preview deployment per pull request and production shipped from `main`. **Cloudflare** (Pages and Workers) is where our static and Next.js sites are moving: we build in GitHub Actions and upload with Wrangler, so there are no per-minute build charges, and we add Turnstile, WAF rules and Access-protected previews. **cPanel hosting on Spaceship** still serves sites such as artificialss.ai and antiquantum.eco until they are migrated. Configuration and secrets live in each platform's encrypted environment variables, never in the repository.
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

**Software development.** AI-powered software development, designed to be handed off: product design, prototyping, MVPs (Minimum Viable Products), modernization and data engineering. Full-stack across web, mobile and AI integration, with the same team and workflow for every client. Final rates are tailored to project scope and engagement length; contact us for a proposal.

| | Costa Rica | International (U.S. priority) |
|---|---|---|
| **Structure** | Flat monthly rate: predictable, no hidden fees | Direct 1099 contractor relationship with clean tax documentation |
| **Scope** | Full-stack development: web, mobile and AI integration | Senior, AI-powered engineering output, led from the U.S. |
| **Compliance** | SICOP vendor registration for public-sector projects | 1099-NEC issued at year end; no W-8BEN forms |
| **Cost** | Tailored per project | 35-50% savings vs. California and Delaware senior engineer salaries |
| **On-site work** | In person across Costa Rica | In person worldwide; the client covers the flights |

**In-person and worldwide.** Our team works on site with clients anywhere in the world, for build sprints, workshops, architecture reviews and team onboarding. For international in-person engagements, we ask the client to cover the flights; other travel details are agreed in the proposal. Remote engagements need no travel.

**Agentic AI Quick Sessions.** Short, focused working sessions where you go from idea to a real deliverable with AI agents, guided live by our engineers. Three tracks: *Agentic Coding* (web, Android, iOS and Kotlin Multiplatform with Firebase or Supabase), *Agentic UI Design* (Figma AI prototypes and design systems) and *Agentic Product Design* (architecture and platform strategy). Book privately for a 1:1 sprint, from idea to deployed product in 4 hours, or as a group of up to 8. You receive a full session summary and your deliverable (source code, design files or a product spec) within 24 hours, under NDA.

*Why this is a professional session, not casual prompting.* Anyone can ask an AI tool for code and hope it works. A quick session is different because it is run the way we run our own projects:
- **Guided by professionals.** A senior engineer or designer leads the session. They frame the problem, choose the architecture, make the design decisions and know when the agent is wrong, so the result is not whatever the first prompt produced.
- **Agents working inside a spec.** Before building, we write down the structure, the patterns and the acceptance criteria. Agents then work within that spec, which keeps the output consistent, reviewable and maintainable.
- **Human in the loop at every step.** Each change is reviewed as it lands. You see how decisions are made and learn the workflow, not only the output.
- **Production standards.** Typed boundaries, formatting and linting, tests where they matter, and real APIs instead of placeholders. The deliverable is something you can keep building on, not a throwaway demo.
- **A clean handoff.** The session summary explains what was built and why, and the source, design files or product spec arrive within 24 hours, so your team can continue without us.

**Legal advisory.** Direct introductions to independent, licensed Costa Rican attorneys, supported by AI-assisted guides, for residency, real estate, corporate formation, family and labor matters. Available in English and Spanish, for local and international clients. We connect you with counsel; we do not provide legal representation ourselves.
- Legal info request: free, with a written response and no call required
- Quick consultation: $20 for 30 minutes
- Full advisory hour: $40 for 1 hour
- Contact: [legal@artificialss.ai](mailto:legal@artificialss.ai)

**Academy.** Structured programs in Spanish (English on request) for educators and students, inclusive language, and professional and technical teams: context engineering, agentic coding and agentic workflow design. Two-hour workshops and a four-week intensive, in person in San Jose, online, or hosted at our lab in Costa Rica, where we receive students, educators and teams for hands-on learning. Groups of 10 or more receive a discount and priority scheduling. Built for Costa Rica and Latin America. Contact: [academy@artificialss.ai](mailto:academy@artificialss.ai)

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
