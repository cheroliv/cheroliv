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

## Architecture Identity — 4 Domains، 3 Accounts

### Brands separation

| Domain | Role | Signal |
|---|---|---|
| `cheroliv.com` | الهوية الشخصية، المدونة، المقالات | L'humain derrière le code، la voix éditoriale، le capital social |
| `talaria.school` | OF — Organisme Formateur Qualiopi | La vitrine institutionnelle et le catalogue des formations |
| `edster.cloud` | SaaS — Infrastructure cloud dédiée | Le provisioning des espaces de travail clients (MVP1) |
| `cccp.education` | Domain (SaaS/Web) | *Common Content Creator Proletarian* — identité numérique و vitrine OSS |

### Technical accounts separation

| Account | Platform | Role |
|---|---|---|
| `cheroliv` | GitHub | Commits، PRs، historique، capital social (inchangé) |
| `cccp-education` | GitHub (org) | Hébergement des dépôts de plugins، brand produit |
| `cccp-education` | Maven Central | Handle de publication — https://central.sonatype.com/namespace/education.cccp |

### 3-layers architecture

```
cheroliv (dev) ──commits──▶ github.com/cccp-education (repos) ──publish──▶ cccp-education (Gradle Portal)
                                GroupId: education.cccp
                                Licence: Apache 2.0
```

*Rule* : le métier est libre (Apache 2.0)، فقط المعاملة المصرفية (waiter-gradle) لا هي.
Le code ne porte pas d'idéologie — le groupId، si.

---

## Methodology

الدورة الحياتية التي أتبعها لكل إضافة:

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
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | Knowledge graph extraction from workspace (nodes، edges، communities) → `graph.json` |

### Processor — RAG & datasets (N1)

| Plugin | Role |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | In-build development assistant: project reading، pgvector RAG، LangChain4j context enrichment، AsciiDoc report generation، dataset creation. |

### Consumer — content generation (N2)

| Plugin | Role |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting for SPG/SPD (deepseek-v4-pro) — planning expert decomposes intention → EPICs → User Stories → Gradle tasks. |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF، slides، document pipeline (READ + RAG). |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | Reveal.js presentation generation from AsciiDoc، with push to dedicated branch. |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | PlantUML syntax validation and rendering (PNG/SVG) via LLM (LangChain4j، 7 providers، RAG pgvector، KG، pool API keys). |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | Multilingual README generation with embedded PlantUML diagrams and GitHub Pages publication via JGit. |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | JBake static site aggregating artifacts from other plugins (diagrams، slides، posts). |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | Video capsule capture (reveal.js + Playwright + TTS). |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | Training project orchestration — backlog synchronized with agent context files (`AGENTS.md`)، course material pipeline (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 via HyperFrames (HeyGen، Apache 2.0)، Node.js bridge. |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | LLM API key pool with rotation (round-robin، least-used، weighted)، quota tracking، audit logging. |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | AsciiDoc manipulation multi-format (HTML/PDF/EPUB/DocBook/ManPage) via AsciidoctorJ + AI-assisted generation (WRITE + PUBLISH). |

### Orchestrator — deployment (N3)

| Plugin | Role |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | DAG orchestration، provisioning CLI، deploy gh-pages. Consommateur terminal، zéro logique métier. |

### Controller — agile & governance (N4)

| Plugin | Role |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | Agile piloting with AI assistant: 7 workshops (Vision→Architecture)، backlog، sprints، velocity، milestones. |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | GitHub ticket creation & tracking — backlog → Issues، Kanban board، commit↔ticket linking. |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | AI-assisted code review: PR analysis، quality score، quality gates، secret detection. |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | Orchestration merge/close/CI: merge when gates OK، auto-close tickets، CI trigger. |

### Specialized tooling (N2)

| Plugin | Role |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster persistence orchestration (clean/generate/sync) without losing Kotlin code in `__codebase__/`. |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster AI assistant with RAG LLM. |

### Vestiges (inactive projects)

| Plugin | Status |
|---|---|
| `com.cheroliv.magic-stick` | N2 — Xubuntu ISO builder (doc site، not plugin) |
| `com.cheroliv.newpipe` | N2 — YouTube→MP3 extractor (abandoned) |
| `com.cheroliv.notebook` | N2 — Colab observability (concept only) |
| `com.cheroliv.office-template` | N? — empty template (to delete) |

---

## Environment & Workstation

### [`magic-stick`](https://github.com/cheroliv/magic-stick)

نص Gradle Kotlin DSL ينسق إنشاء ISO قابل للتحميل Xubuntu — يعمل ككل من **live USB** و **installer**، ومزود بالأدوات الضرورية المصممة خصيصًا لثلاثة أنماط استخدام:

- **Nomadic workstation** — بيتي المحمولة الكاملة على محرك أقراص USB.
- **FTTH Technician** — أداة ميدانية جاهزة للاستخدام.
- **طالب/متدرب** — بدء فوري بدون أي تثبيت مسبق مطلوب.

يوضح المشروع الفلسفة البيئية: بيئة العمل نفسها
هي **reproducible، versioned، و documented artifact**.
The
Project's documentation is generated and published by [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) at
[cheroliv.com/magic-stick](https://cheroliv.com/magic-stick/) — proof that
the publication pipeline runs in production.

---

## What I Teach

- Java من intermediate إلى advanced (8 إلى 25) — من Stream API إلى Virtual Threads، Records، Pattern Matching.
- Kotlin من intermediate إلى advanced — null safety، extensions، coroutines، sealed classes.
- Scala و بدائل بناء JVM (Mill، sbt).
- Maven multi-module architectures.
- Gradle Kotlin DSL — من كتابة المهام إلى الإضافات القابلة للنشر.
- Hexagonal Architecture و testing — ports & adapters، JUnit 5، Cucumber، TestContainers.
- Spring Boot — REST APIs، JWT security، integration testing.
- Project tooling — GitHub Actions CI/CD، document قابل للتنفيذ، إنشاء المحتوى.

يتم إنتاج مواد الدورة باستخدام إضافات النظام البيئي:
الشرائح هي Reveal.js تم توليدها بواسطة [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle)،
 websites الدورة بواسطة [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle)،
و محرك الأقراص القابل للتحميل بواسطة [`magic-stick`](https://github.com/cheroliv/magic-stick).
يغذّي التدريب والأدوات بعضها البعض بشكل متبادل.

---

## Core Stack

Java · Kotlin · Scala · Gradle (Kotlin DSL) · Mill · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Links

- Website: [cheroliv.com](https://cheroliv.com)
- Published Plugins: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentation](https://cheroliv.com/magic-stick/) · [repository](https://github.com/cheroliv/magic-stick)

---

*الكود الذي نكتبه لأنفسنا هو المختبر للكود الذي نعلّمه للآخرين.*
