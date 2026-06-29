# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 **Español** · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Artesano de Software · Trainer · Autor de Tooling de Gradle**

Diseño un ecosistema de plugins Gradle Kotlin DSL para herramientas de proyecto,
documentación ejecutable y producción de contenido educativo.
Mis materiales en bruto: Kotlin, Gradle, AsciiDoc, LangChain4j, Koog.

---

## Positioning

Trabajo en la intersección de tres dominios:

- **Software Craftsmanship** — TDD, BDD Cucumber, Arquitectura Hexagonal, Kotlin Idiomático.
- **Developer Tooling** — plugins Gradle reutilizables, publicados bajo el espacio de nombres `education.cccp` en el [Maven Central](https://plugins.gradle.org/search?term=education.cccp).
- **EdTech** — contenido educativo, sitios estáticos generados, materiales de formación rastreables.

La coherencia de todo esto surge de una simple convicción: **un desarrollador/trainer
creíble construye y utiliza sus propias herramientas**. No vendo lo que no uso
en mi día a día.

---

## Methodology

El ciclo de vida que sigo para cada plugin:

1. **Prototipado de lógica de negocio** dentro del `build.gradle.kts` raíz, con logs relevantes
   para validar el comportamiento en condiciones reales.
2. **Migración de plugin** una vez que la lógica de dominio es estable — transplantar el
   código probado a un módulo dedicado, usando TDD con JUnit 5.
3. **BDD con Cucumber** tan pronto como el dominio lo permita, para documentar
   la intención a nivel de usuario.
4. **Publicación** en el Maven Central con un contrato de API versionado.

No es un método fancy, pero es uno que resiste la prueba del tiempo.

---

## El Ecosistema `education.cccp.*` — 25 boroughs

Los plugins están estructurados alrededor de tres roles en 4 capas (DAG N0→N4).

### Foundation — bloques de construcción reutilizables (N0)

| Plugin | Rol |
|---|---|
| [`agent-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de protocolo de agentes (shared kernel) |
| [`codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de Codebase RAG (shared kernel) |
| [`vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de Vibecoding (shared kernel) |
| [`llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de pool de API LLM (shared kernel) |
| [`pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de pipeline (shared kernel) |
| [`i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de internacionalización (shared kernel) |

### Scanner — extracción de gráfico de workspace (N0)

| Plugin | Rol |
|---|---|
| [`graphify`](https://github.com/cccp-education/graphify-gradle) | Extracción de grafo de conocimiento desde workspace (nodos, aristas, comunidades) → `graph.json` |

### Processor — RAG & datasets (N1)

| Plugin | Rol |
|---|---|
| [`codebase`](https://github.com/cccp-education/codebase-gradle) | Asistente de desarrollo en-build: lectura del proyecto, pgvector RAG, enriquecimiento de contexto LangChain4j, generación de informe AsciiDoc, creación de dataset. |

### Consumer — generación de contenido (N2)

| Plugin | Rol |
|---|---|
| [`planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting para SPG/SPD (deepseek-v4-pro) — experto en planificación descompone intención → EPICs → User Stories → Tareas Gradle. |
| [`codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, slides, pipeline documental (READ + RAG). |
| [`slider`](https://github.com/cccp-education/slider-gradle) | Generación de presentaciones Reveal.js desde AsciiDoc, con push a rama dedicada. |
| [`plantuml`](https://github.com/cccp-education/plantuml-gradle) | Validación de sintaxis PlantUML y renderizado (PNG/SVG) vía LLM (LangChain4j, 7 proveedores, RAG pgvector, KG, pool de claves API). |
| [`readme`](https://github.com/cccp-education/readme-gradle) | Generación de README multilenguaje con diagramas PlantUML integrados y publicación en GitHub Pages vía JGit. |
| [`bakery`](https://github.com/cccp-education/bakery-gradle) | Sitio estático JBake agregando artefactos de otros plugins (diagramas, slides, posts). |
| [`capsule`](https://github.com/cccp-education/capsule-gradle) | Captura de cápsula de video (reveal.js + Playwright + TTS). |
| [`training`](https://github.com/cccp-education/training-gradle) | Orquestación de proyecto de formación — backlog sincronizado con archivos de contexto del agente (`AGENTS.md`), pipeline de material curricular (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 vía HyperFrames (HeyGen, Apache 2.0), puente Node.js. |
| [`api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | Pool de claves API LLM con rotación (round-robin, menos-usado, ponderado), seguimiento de cuotas, registro de auditoría. |
| [`document`](https://github.com/cccp-education/document-gradle) | Manipulación AsciiDoc multi-formato (HTML/PDF/EPUB/DocBook/ManPage) vía AsciidoctorJ + generación asistida por IA (WRITE + PUBLISH). |

### Orchestrator — despliegue (N3)

| Plugin | Rol |
|---|---|
| [`runner`](https://github.com/cccp-education/runner-gradle) | Orquestación DAG, CLI de provisioning, despliegue gh-pages. Consommateur terminal, cero lógica de negocio. |

### Controller — agile & gobernanza (N4)

| Plugin | Rol |
|---|---|
| [`agile`](https://github.com/cccp-education/agile-gradle) | Piloto agile con asistente IA: 7 talleres (Vision→Architecture), backlog, sprints, velocidad, hitos. |
| [`ticket`](https://github.com/cccp-education/ticket-gradle) | Creación y seguimiento de tickets GitHub — backlog → Issues, tablero Kanban, enlace commit↔ticket. |
| [`review`](https://github.com/cccp-education/review-gradle) | Code review asistido por IA: análisis de PR, puntuación de calidad, quality gates, detección de secretos. |
| [`flow`](https://github.com/cccp-education/flow-gradle) | Orquestación merge/close/CI: merge cuando gates OK, auto-cierre de tickets, trigger CI. |

### Tooling especializado (N2)

| Plugin | Rol |
|---|---|
| [`jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | Orquestación de persistencia JHipster (clean/generate/sync) sin perder código Kotlin en `__codebase__/`. |
| [`jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | Asistente JHipster IA con LLM RAG. |

### Vestiges (proyectos inactivos)

| Plugin | Status |
|---|---|
| `magic-stick` | N2 — Constructor de ISO Xubuntu (doc site, no plugin) |
| `newpipe` | N2 — Extractor YouTube→MP3 (abandonado) |
| `notebook` | N2 — Observabilidad Colab (concepto únicamente) |
| `office-template` | N? — plantilla vacía (para borrar) |

---

## Environment & Workstation

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

Un script de construcción Kotlin DSL de Gradle que orquesta la creación de una ISO Xubuntu arrancable — funcionando como un **USB activo** y un **instalador**, equipado con las herramientas necesarias adaptadas para tres perfiles de uso:

- **Estación de trabajo nómada** — mi entornoportable completo en una unidad USB.
- **Técnico de Telecom FTTH** — herramientas de campo listas para usar.
- **Estudiante/Trainee** — incorporación inmediata sin necesidad de instalación previa.

El proyecto ilustra la filosofía del ecosistema: el entorno de trabajo en
sí es un **artefacto imprimible, versionado y documentado**. La
documentación del proyecto es generada y publicada por [`bakery`](https://github.com/cccp-education/bakery-gradle) en
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — prueba de que
la pipeline de publicación funciona en producción.

---

## Core Stack

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Empaquetado Xubuntu/Debian.

---

## Links

- Sitio web: [cheroliv.com](https://cheroliv.com)
- Plugins publicados: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentación](https://cccp.education/magic-stick/) · [repositorio](https://github.com/cccp-education/magic-stick)

---

