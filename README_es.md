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

## Architecture Identity — 4 Dominios, 3 Cuentas

### Separación de marcas

| Dominio | Rol | Señal |
|---|---|---|
| `cheroliv.com` | Identidad personal, blog, artículos | L'humain derrière le code, la voix éditoriale, le capital social |
| `talaria.school` | OF — Organisme Formateur Qualiopi | La vitrine institucional y el catálogo de formaciones |
| `edster.cloud` | SaaS — Infraestructura cloud dedicada | El provisioning de espacios de trabajo del cliente (MVP1) |
| `cccp.education` | Dominio (SaaS/Web) | *Common Content Creator Proletarian* — identidad digital y vitrine OSS |

### Separación de cuentas técnicas

| Cuenta | Plataforma | Rol |
|---|---|---|
| `cheroliv` | GitHub | Commits, PRs, historial, capital social (inchangé) |
| `cccp-education` | GitHub (org) | Hébergement des dépôts de plugins, brand produit |
| `cccp-education` | Maven Central | Gestionario de publicación — https://central.sonatype.com/namespace/education.cccp |

### Arquitectura de 3 capas

```
cheroliv (dev) ──commits──▶ github.com/cccp-education (repos) ──publish──▶ cccp-education (Gradle Portal)
                                GroupId: education.cccp
                                Licence: Apache 2.0
```

*Regla*: el negocio es libre (Apache 2.0), solo la transacción bancaria (waiter-gradle) no lo es.
El código no porta una ideología — el groupId, sí.

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
| [`com.gradleup.nmcp.settings`](https://plugins.gradle.org/plugin/com.gradleup.nmcp.settings) | Publicación en Maven Central (nmcp) |
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de protocolo de agentes (shared kernel) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de Codebase RAG (shared kernel) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de Vibecoding (shared kernel) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de pool de API LLM (shared kernel) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de pipeline (shared kernel) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de internacionalización (shared kernel) |

### Scanner — extracción de gráfico de workspace (N0)

| Plugin | Rol |
|---|---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | Extracción de grafo de conocimiento desde workspace (nodos, aristas, comunidades) → `graph.json` |

### Processor — RAG & datasets (N1)

| Plugin | Rol |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | Asistente de desarrollo en-build: lectura del proyecto, pgvector RAG, enriquecimiento de contexto LangChain4j, generación de informe AsciiDoc, creación de dataset. |

### Consumer — generación de contenido (N2)

| Plugin | Rol |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting para SPG/SPD (deepseek-v4-pro) — experto en planificación descompone intención → EPICs → User Stories → Tareas Gradle. |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, slides, pipeline documental (READ + RAG). |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | Generación de presentaciones Reveal.js desde AsciiDoc, con push a rama dedicada. |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | Validación de sintaxis PlantUML y renderizado (PNG/SVG) vía LLM (LangChain4j, 7 proveedores, RAG pgvector, KG, pool de claves API). |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | Generación de README multilenguaje con diagramas PlantUML integrados y publicación en GitHub Pages vía JGit. |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | Sitio estático JBake agregando artefactos de otros plugins (diagramas, slides, posts). |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | Captura de cápsula de video (reveal.js + Playwright + TTS). |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | Orquestación de proyecto de formación — backlog sincronizado con archivos de contexto del agente (`AGENTS.md`), pipeline de material curricular (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 vía HyperFrames (HeyGen, Apache 2.0), puente Node.js. |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | Pool de claves API LLM con rotación (round-robin, menos-usado, ponderado), seguimiento de cuotas, registro de auditoría. |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | Manipulación AsciiDoc multi-formato (HTML/PDF/EPUB/DocBook/ManPage) vía AsciidoctorJ + generación asistida por IA (WRITE + PUBLISH). |

### Orchestrator — despliegue (N3)

| Plugin | Rol |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | Orquestación DAG, CLI de provisioning, despliegue gh-pages. Consommateur terminal, cero lógica de negocio. |

### Controller — agile & gobernanza (N4)

| Plugin | Rol |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | Piloto agile con asistente IA: 7 talleres (Vision→Architecture), backlog, sprints, velocidad, hitos. |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | Creación y seguimiento de tickets GitHub — backlog → Issues, tablero Kanban, enlace commit↔ticket. |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | Code review asistido por IA: análisis de PR, puntuación de calidad, quality gates, detección de secretos. |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | Orquestación merge/close/CI: merge cuando gates OK, auto-cierre de tickets, trigger CI. |

### Tooling especializado (N2)

| Plugin | Rol |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | Orquestación de persistencia JHipster (clean/generate/sync) sin perder código Kotlin en `__codebase__/`. |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | Asistente JHipster IA con LLM RAG. |

### Vestiges (proyectos inactivos)

| Plugin | Status |
|---|---|
| `com.cheroliv.magic-stick` | N2 — Constructor de ISO Xubuntu (doc site, no plugin) |
| `com.cheroliv.newpipe` | N2 — Extractor YouTube→MP3 (abandonado) |
| `com.cheroliv.notebook` | N2 — Observabilidad Colab (concepto únicamente) |
| `com.cheroliv.office-template` | N? — plantilla vacía (para borrar) |

---

## Environment & Workstation

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

Un script de construcción Kotlin DSL de Gradle que orquesta la creación de una ISO Xubuntu arrancable — funcionando como un **USB activo** y un **instalador**, equipado con las herramientas necesarias adaptadas para tres perfiles de uso:

- **Estación de trabajo nómada** — mi entornoportable completo en una unidad USB.
- **Técnico de Telecom FTTH** — herramientas de campo listas para usar.
- **Estudiante/Trainee** — incorporación inmediata sin necesidad de instalación previa.

El proyecto ilustra la filosofía del ecosistema: el entorno de trabajo en
sí es un **artefacto imprimible, versionado y documentado**. La
documentación del proyecto es generada y publicada por [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) en
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — prueba de que
la pipeline de publicación funciona en producción.

---



---

## Core Stack

Java · Kotlin · Scala · Gradle (Kotlin DSL) · Mill · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Empaquetado Xubuntu/Debian.

---

## Links

- Sitio web: [cheroliv.com](https://cheroliv.com)
- Plugins publicados: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentación](https://cccp.education/magic-stick/) · [repositorio](https://github.com/cccp-education/magic-stick)

---

*El código personal alimenta el código compartido.*
