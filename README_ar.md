# `cheroliv`

🇬🇧 **English** · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 **العربية** · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Software Artisan · Trainer · Gradle Tooling Author**

أصمّم نظامًا بيئيًا من إضافات Gradle Kotlin DSL لأدوات المشاريع، والوثائق القابلة للتنفيذ، وإ Producing المحتوى التعليمي.
موادي الخام: Kotlin، Gradle، AsciiDoc، LangChain4j، Koog.

---

## Positioning

أعمل عند تقاطع ثلاثة مجالات:

- **Software Craftsmanship** — TDD، BDD Cucumber، الهيكلية الهرمية (Hexagonal Architecture)، Kotlin المألوف.
- **Developer Tooling** — إضافات Gradle قابلة لإعادة الاستخدام، منشورة في namespace `education.cccp` على [Maven Central](https://plugins.gradle.org/search?term=education.cccp).
- **EdTech** — المحتوى التعليمي، المواقع الثابتة التي يتم توليدها، مواد التدريب القابلة للتتبع.

تكامل كل هذا ينبع من إيمان بسيط: **مدوف/مدرب موثوق** يبني ويستخدم أدواته الخاصة.
أنا لا أبيع ما لا أستخدمه يوميًا.

---

## Methodology

1. **Business logic prototyping** داخل `build.gradle.kts` الجذر، مع تسجيلات ذات صلة
   للتحقق من السلوك في ظروف حقيقية.
2. **Plugin migration** بمجرد استقرار منطق المجال — نقل
   الكود الذي تم التحقق منه إلى وحدة مخصصة، باستخدام TDD مع JUnit 5.
3. **BDD مع Cucumber** بمجردما يكون المجال يسمح بذلك، للتوثيق
   intention at the user level.
4. **Publication** إلى Maven Central مع عقد API مُحدد بإصدار.

إنه ليس منهجًا مبهرًا، ولكن منهج يخضع لاختبار الزمن.

---

## The `education.cccp.*` Ecosystem — 25 boroughs

الإضافة هي هيكلة حول ثلاثة أدوار عبر 4 طبقات (DAG N0→N4).

### Foundation — reusable building blocks (N0)

| Plugin | Role |
|---|---|
| [`agent-contracts`](https://github.com/cccp-education/workspace-bom) | Agent protocol contracts (shared kernel) |
| [`codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Codebase RAG contracts (shared kernel) |
| [`vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Vibecoding contracts (shared kernel) |
| [`llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | LLM API pool contracts (shared kernel) |
| [`pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Pipeline contracts (shared kernel) |
| [`i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Internationalization contracts (shared kernel) |

### Scanner — workspace graph extraction (N0)

| Plugin | Role |
|---|---|
| [`graphify`](https://github.com/cccp-education/graphify-gradle) | Knowledge graph extraction from workspace (nodes، edges، communities) → `graph.json` |

### Processor — RAG & datasets (N1)

| Plugin | Role |
|---|---|
| [`codebase`](https://github.com/cccp-education/codebase-gradle) | In-build development assistant: project reading، pgvector RAG، LangChain4j context enrichment، AsciiDoc report generation، dataset creation. |

### Consumer — content generation (N2)

| Plugin | Role |
|---|---|
| [`planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting for SPG/SPD (deepseek-v4-pro) — planning expert decomposes intention → EPICs → User Stories → Gradle tasks. |
| [`codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF، slides، document pipeline (READ + RAG). |
| [`slider`](https://github.com/cccp-education/slider-gradle) | Reveal.js presentation generation from AsciiDoc، with push to dedicated branch. |
| [`plantuml`](https://github.com/cccp-education/plantuml-gradle) | PlantUML syntax validation and rendering (PNG/SVG) via LLM (LangChain4j، 7 providers، RAG pgvector، KG، pool API keys). |
| [`readme`](https://github.com/cccp-education/readme-gradle) | Multilingual README generation with embedded PlantUML diagrams and GitHub Pages publication via JGit. |
| [`bakery`](https://github.com/cccp-education/bakery-gradle) | JBake static site aggregating artifacts from other plugins (diagrams، slides، posts). |
| [`capsule`](https://github.com/cccp-education/capsule-gradle) | Video capsule capture (reveal.js + Playwright + TTS). |
| [`training`](https://github.com/cccp-education/training-gradle) | Training project orchestration — backlog synchronized with agent context files (`AGENTS.md`)، course material pipeline (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 via HyperFrames (HeyGen، Apache 2.0)، Node.js bridge. |
| [`api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | LLM API key pool with rotation (round-robin، least-used، weighted)، quota tracking، audit logging. |
| [`document`](https://github.com/cccp-education/document-gradle) | AsciiDoc manipulation multi-format (HTML/PDF/EPUB/DocBook/ManPage) via AsciidoctorJ + AI-assisted generation (WRITE + PUBLISH). |

### Orchestrator — deployment (N3)

| Plugin | Role |
|---|---|
| [`runner`](https://github.com/cccp-education/runner-gradle) | DAG orchestration، provisioning CLI، deploy gh-pages. Consommateur terminal، zéro logique métier. |

### Controller — agile & governance (N4)

| Plugin | Role |
|---|---|
| [`agile`](https://github.com/cccp-education/agile-gradle) | Agile piloting with AI assistant: 7 workshops (Vision→Architecture)، backlog، sprints، velocity، milestones. |
| [`ticket`](https://github.com/cccp-education/ticket-gradle) | GitHub ticket creation & tracking — backlog → Issues، Kanban board، commit↔ticket linking. |
| [`review`](https://github.com/cccp-education/review-gradle) | AI-assisted code review: PR analysis، quality score، quality gates، secret detection. |
| [`flow`](https://github.com/cccp-education/flow-gradle) | Orchestration merge/close/CI: merge when gates OK، auto-close tickets، CI trigger. |

### Specialized tooling (N2)

| Plugin | Role |
|---|---|
| [`jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster persistence orchestration (clean/generate/sync) without losing Kotlin code in `__codebase__/`. |
| [`jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster AI assistant with RAG LLM. |

### Vestiges (inactive projects)

| Plugin | Status |
|---|---|
| `magic-stick` | N2 — Xubuntu ISO builder (doc site، not plugin) |
| `newpipe` | N2 — YouTube→MP3 extractor (abandoned) |
| `notebook` | N2 — Colab observability (concept only) |
| `office-template` | N? — empty template (to delete) |

---

## Environment & Workstation

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

نص Gradle Kotlin DSL ينسق إنشاء ISO قابل للتحميل Xubuntu — يعمل ككل من **live USB** و **installer**، ومزود بالأدوات الضرورية المصممة خصيصًا لثلاثة أنماط استخدام:

- **Nomadic workstation** — بيتي المحمولة الكاملة على محرك أقراص USB.
- **FTTH Technician** — أداة ميدانية جاهزة للاستخدام.
- **طالب/متدرب** — بدء فوري بدون أي تثبيت مسبق مطلوب.

يوضح المشروع الفلسفة البيئية: بيئة العمل نفسها
هي **reproducible، versioned، و documented artifact**.
The
Project's documentation is generated and published by [`bakery`](https://github.com/cccp-education/bakery-gradle) at
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — proof that
the publication pipeline runs in production.

---

---

## Core Stack

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Links

- Website: [cheroliv.com](https://cheroliv.com)
- Published Plugins: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentation](https://cccp.education/magic-stick/) · [repository](https://github.com/cccp-education/magic-stick)

---

