# `cheroliv`

🇬🇧 **English** · 🇫🇷 [Français](README_fr.md)

**Software Artisan · Trainer · Gradle Tooling Author**

I design an ecosystem of Gradle Kotlin DSL plugins for project tooling,
executable documentation, and educational content production.
My raw materials: Kotlin, Gradle, AsciiDoc, LangChain4j, Koog.

---

## Positioning

I work at the intersection of three domains:

- **Software Craftsmanship** — TDD, BDD Cucumber, Hexagonal Architecture, Idiomatic Kotlin.
- **Developer Tooling** — reusable Gradle plugins, published under the `education.cccp` namespace on the [Gradle Plugin Portal](https://plugins.gradle.org/search?term=education.cccp).
- **EdTech** — educational content, generated static sites, traceable training materials.

The coherence of it all stems from a simple conviction: **a credible developer/trainer
builds and uses their own tools**. I don't sell what I don't use
on a daily basis.

---

## Architecture Identity — 4 Domains, 3 Accounts

### Brands separation

| Domain | Role | Signal |
|---|---|---|
| `cheroliv.com` | Personal identity, blog, articles | L'humain derrière le code, la voix éditoriale, le capital social |
| `talaria.school` | OF — Organisme Formateur Qualiopi | La vitrine institutionnelle, les formations payantes, le catalogue |
| `edster.cloud` | SaaS — VPS 30€/mois, marge ~95% | Le provisioning workspace client, Stripe + Orange Money (MVP1) |
| `cccp.education` | Domain (SaaS/Web) | *Common Content Creator Proletarian* — identité numérique et vitrine OSS |

### Technical accounts separation

| Account | Platform | Role |
|---|---|---|
| `cheroliv` | GitHub | Commits, PRs, historique, capital social (inchangé) |
| `cccp-education` | GitHub (org) | Hébergement des dépôts de plugins, brand produit |
| `cccp-education` | Gradle Plugin Portal | Handle de publication — https://plugins.gradle.org/u/cccp-education |

### 3-layers architecture

```
cheroliv (dev) ──commits──▶ github.com/cccp-education (repos) ──publish──▶ cccp-education (Gradle Portal)
                               GroupId: education.cccp
                               Licence: Apache 2.0
```

*Rule* : le métier est libre (Apache 2.0), seule la transaction bancaire (waiter-gradle) ne l'est pas.
Le code ne porte pas d'idéologie — le groupId, si.

---

## Methodology

The lifecycle I follow for each plugin:

1. **Business logic prototyping** within the root `build.gradle.kts`, with relevant logs
   to validate behavior under real conditions.
2. **Plugin migration** once the domain logic is stable — transplanting the
   proven code to a dedicated module, using TDD with JUnit 5.
3. **BDD with Cucumber** as soon as the domain allows, to document
   intent at the user level.
4. **Publication** to the Gradle Plugin Portal with a versioned API contract.

It's not a fancy method, but it's one that stands the test of time.

---

## The `education.cccp.*` Ecosystem — 25 boroughs

The plugins are structured around three roles across 4 layers (DAG N0→N4).

### Foundation — reusable building blocks (N0)

| Plugin | Role |
|---|---|
| [`com.gradleup.nmcp.settings`](https://plugins.gradle.org/plugin/com.gradleup.nmcp.settings) | Maven Central publishing (nmcp) |
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | Agent protocol contracts (shared kernel) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Codebase RAG contracts (shared kernel) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Vibecoding contracts (shared kernel) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | LLM API pool contracts (shared kernel) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Pipeline contracts (shared kernel) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Internationalization contracts (shared kernel) |

### Scanner — workspace graph extraction (N0)

| Plugin | Role |
|---|---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | Knowledge graph extraction from workspace (nodes, edges, communities) → `graph.json` |

### Processor — RAG & datasets (N1)

| Plugin | Role |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | In-build development assistant: project reading, pgvector RAG, LangChain4j context enrichment, AsciiDoc report generation, dataset creation. |

### Consumer — content generation (N2)

| Plugin | Role |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting for SPG/SPD (deepseek-v4-pro) — planning expert decomposes intention → EPICs → User Stories → Gradle tasks. |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, slides, document pipeline (READ + RAG). |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | Reveal.js presentation generation from AsciiDoc, with push to dedicated branch. |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | PlantUML syntax validation and rendering (PNG/SVG) via LLM (LangChain4j, 7 providers, RAG pgvector, KG, pool API keys). |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | Multilingual README generation with embedded PlantUML diagrams and GitHub Pages publication via JGit. |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | JBake static site aggregating artifacts from other plugins (diagrams, slides, posts). |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | Video capsule capture (reveal.js + Playwright + TTS). |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | Training project orchestration — backlog synchronized with agent context files (`AGENTS.md`), course material pipeline (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 via HyperFrames (HeyGen, Apache 2.0), Node.js bridge. |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | LLM API key pool with rotation (round-robin, least-used, weighted), quota tracking, audit logging. |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | AsciiDoc manipulation multi-format (HTML/PDF/EPUB/DocBook/ManPage) via AsciidoctorJ + AI-assisted generation (WRITE + PUBLISH). |

### Orchestrator — deployment (N3)

| Plugin | Role |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | DAG orchestration, provisioning CLI, deploy gh-pages. Consommateur terminal, zéro logique métier. |

### Controller — agile & governance (N4)

| Plugin | Role |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | Agile piloting with AI assistant: 7 workshops (Vision→Architecture), backlog, sprints, velocity, milestones. |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | GitHub ticket creation & tracking — backlog → Issues, Kanban board, commit↔ticket linking. |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | AI-assisted code review: PR analysis, quality score, quality gates, secret detection. |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | Orchestration merge/close/CI: merge when gates OK, auto-close tickets, CI trigger. |

### Specialized tooling (N2)

| Plugin | Role |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster persistence orchestration (clean/generate/sync) without losing Kotlin code in `__codebase__/`. |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster AI assistant with RAG LLM. |

### Vestiges (inactive projects)

| Plugin | Status |
|---|---|
| `com.cheroliv.magic-stick` | N2 — Xubuntu ISO builder (doc site, not plugin) |
| `com.cheroliv.newpipe` | N2 — YouTube→MP3 extractor (abandoned) |
| `com.cheroliv.notebook` | N2 — Colab observability (concept only) |
| `com.cheroliv.office-template` | N? — empty template (to delete) |

---

## Environment & Workstation

### [`magic-stick`](https://github.com/cheroliv/magic-stick)

A Gradle Kotlin DSL build script that orchestrates the creation of a bootable Xubuntu ISO — functioning as both a **live USB** and an **installer**, equipped with the necessary tooling tailored for three usage profiles:

- **Nomadic workstation** — my complete portable environment on a USB drive.
- **FTTH Telecom Technician** — ready-to-use field tooling.
- **Student/Trainee** — immediate onboarding with no prior installation required.

The project illustrates the ecosystem's philosophy: the work environment itself
is a **reproducible, versioned, and documented artifact**. The
project's documentation is generated and published by [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) at
[cheroliv.com/magic-stick](https://cheroliv.com/magic-stick/) — proof that
the publication pipeline runs in production.

---

## What I Teach

- Intermediate to advanced Java (8 to 25) — from the Stream API to Virtual Threads, Records, Pattern Matching.
- Intermediate to advanced Kotlin — null safety, extensions, coroutines, sealed classes.
- Scala and JVM build alternatives (Mill, sbt).
- Maven multi-module architectures.
- Gradle Kotlin DSL — from writing tasks to publishable plugins.
- Hexagonal Architecture and testing — ports & adapters, JUnit 5, Cucumber, TestContainers.
- Spring Boot — REST APIs, JWT security, integration testing.
- Project tooling — GitHub Actions CI/CD, executable documentation, content generation.

Course materials are produced using the ecosystem's plugins:
slides are Reveal.js generated by [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle),
course websites by [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle),
and the bootable drive by [`magic-stick`](https://github.com/cheroliv/magic-stick).
Training and tooling mutually feed into each other.

---

## Core Stack

Java · Kotlin · Scala · Gradle (Kotlin DSL) · Mill · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Links

- Website: [cheroliv.com](https://cheroliv.com)
- Published Plugins: [Gradle Plugin Portal — cccp-education](https://plugins.gradle.org/u/cccp-education)
- `magic-stick`: [documentation](https://cheroliv.com/magic-stick/) · [repository](https://github.com/cheroliv/magic-stick)

---

*The code we write for ourselves is the laboratory for the code we teach others.*
