# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 **Français** · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Software Artisan · Formateur · Auteur d'outils Gradle**

Je conçois un écosystème de plugins Gradle Kotlin DSL pour l'outillage de projet,
la documentation exécutable et la production de contenu pédagogique.
Ma matière première : Kotlin, Gradle, AsciiDoc, LangChain4j, Koog.

---

## Positionnement

Je travaille à l'intersection de trois domaines :

- **Craft logiciel** — TDD, BDD Cucumber, architecture hexagonale, Kotlin idiomatique.
- **Outillage développeur** — plugins Gradle réutilisables, publiés sous le namespace `education.cccp` sur le [Maven Central](https://plugins.gradle.org/search?term=education.cccp).
- **Edtech** — contenus pédagogiques, sites statiques générés, supports de formation traçables.

La cohérence de l'ensemble tient à une conviction simple : **un développeur/formateur crédible
construit et utilise ses propres outils**. Je ne vends pas ce que je n'utilise pas
au quotidien.

---

## Architecture Identité — 4 Marques, 3 Comptes

### Séparation des marques

| Marque | Rôle | Signal |
|---|---|---|
| `cheroliv.com` | Identité perso, blog, articles | L'humain derrière le code, la voix éditoriale, le capital social |
| `talaria.school` | OF — Organisme Formateur Qualiopi | La vitrine institutionnelle et le catalogue des formations |
| `edster.cloud` | SaaS — Infrastructure cloud dédiée | Le provisioning des espaces de travail clients (MVP1) |
| `cccp.education` | Domaine (SaaS/Web) | *Common Content Creator Proletarian* — identité numérique et vitrine OSS |

### Séparation des comptes techniques

| Compte | Plateforme | Rôle |
|---|---|---|
| `cheroliv` | GitHub | Commits, PRs, historique, capital social (inchangé) |
| `cccp-education` | GitHub (org) | Hébergement des dépôts de plugins, brand produit |
| `cccp-education` | Maven Central | Handle de publication — https://central.sonatype.com/namespace/education.cccp |

---

## Méthode

Le cycle que je suis sur chaque plugin :

1. **Tâtonnement métier** dans le `build.gradle.kts` racine, avec logs pertinents
   pour valider le comportement en conditions réelles.
2. **Migration vers plugin** quand le métier est stabilisé — transplantation du
   code éprouvé vers un module dédié, sous TDD avec JUnit 5.
3. **BDD Cucumber** dès que le domaine métier le permet, pour documenter
   l'intention à hauteur d'usager.
4. **Publication** sur le Maven Central avec un contrat d'API versionné.

Ce n'est pas une méthode chic, c'est une méthode qui tient debout sur la durée.

---

## Écosystème `education.cccp.*` — 25 boroughs

Les plugins s'articulent autour de trois rôles répartis sur 4 couches (DAG N0→N4).

### Fondation — briques réutilisables (N0)

| Plugin | Rôle |
|---|---|
| [`com.gradleup.nmcp.settings`](https://plugins.gradle.org/plugin/com.gradleup.nmcp.settings) | Publication Maven Central (nmcp) |
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | Contrats de protocole agent (shared kernel) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Contrats RAG codebase (shared kernel) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Contrats vibecoding (shared kernel) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | Contrats pool API LLM (shared kernel) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Contrats pipeline (shared kernel) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Contrats internationalisation (shared kernel) |

### Scanner — extraction de graphe du workspace (N0)

| Plugin | Rôle |
|---|---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | Extraction de graphe de connaissance du workspace (nœuds, arêtes, communautés) → `graph.json` |

### Processeur — RAG & datasets (N1)

| Plugin | Rôle |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | Assistant de développement embarqué dans le build : lecture du projet, RAG pgvector, enrichissement de contexte LangChain4j, génération de rapports AsciiDoc, constitution de datasets. |

### Consommateur — génération de contenu (N2)

| Plugin | Rôle |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | Prompting LLM pour SPG/SPD (deepseek-v4-pro) — expert de planification décompose l'intention → EPICs → User Stories → tâches Gradle. |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, slides, pipeline documentaire (READ + RAG). |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | Génération de présentations Reveal.js depuis des sources AsciiDoc, avec push vers branche dédiée. |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | Validation syntaxique et rendu PlantUML (PNG/SVG) via LLM (LangChain4j, 7 providers, RAG pgvector, KG, pool API keys). |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | Génération de README multilingues avec diagrammes PlantUML embarqués et publication GitHub Pages via JGit. |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | Site statique JBake agrégant les artefacts produits par les autres plugins (diagrammes, slides, posts). |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | Capture de capsules vidéo (reveal.js + Playwright + TTS). |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | Orchestration de projet de formation — backlog synchronisé avec les fichiers de contexte agent (`AGENTS.md`), pipeline de production des supports de cours (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 via HyperFrames (HeyGen, Apache 2.0), bridge Node.js. |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | Pool de clés API LLM avec rotation (round-robin, least-used, weighted), suivi de quotas, journalisation audit. |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | Manipulation AsciiDoc multi-format (HTML/PDF/EPUB/DocBook/ManPage) via AsciidoctorJ + génération assistée par IA (WRITE + PUBLISH). |

### Orchestrateur — déploiement (N3)

| Plugin | Rôle |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | Orchestration DAG, CLI provisioning, déploiement gh-pages. Consommateur terminal, zéro logique métier. |

### Contrôleur — agile & gouvernance (N4)

| Plugin | Rôle |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | Pilotage agile assisté par IA : 7 ateliers (Vision→Architecture), backlog, sprints, vélocité, jalons. |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | Création & suivi de tickets GitHub — backlog → Issues, Kanban board, lien commit↔ticket. |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | Code review assistée par IA : analyse PR, score qualité, quality gates, détection secrets. |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | Orchestration merge/close/CI : merge quand gates OK, auto-close tickets, trigger CI. |

### Outils spécialisés (N2)

| Plugin | Rôle |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | Orchestration JHipster persistence (clean/generate/sync) sans perdre le code Kotlin dans `__codebase__/`. |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | Assistant JHipster RAG LLM. |

### Vestiges (projets inactifs)

| Plugin | Statut |
|---|---|
| `com.cheroliv.magic-stick` | N2 — Constructeur ISO Xubuntu (site doc, pas plugin) |
| `com.cheroliv.newpipe` | N2 — Extracteur YouTube→MP3 (abandonné) |
| `com.cheroliv.notebook` | N2 — Observabilité Colab (concept uniquement) |
| `com.cheroliv.office-template` | N? — template vide (à supprimer) |

---

## Environnement & poste de travail

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

Build script Gradle Kotlin DSL qui orchestre la construction d'une ISO Xubuntu
bootable — à la fois **live USB** et **installateur**, équipée de l'outillage
nécessaire selon trois profils d'usage :

- **Poste de travail nomade** — mon environnement complet portable sur une clé.
- **Technicien télécom FTTH** — l'outillage terrain prêt à l'emploi.
- **Apprenant en formation** — une mise en route immédiate sans installation préalable.

Le projet illustre la philosophie de l'écosystème : l'environnement de travail
est lui-même un **artefact reproductible, versionné, documenté**. La
documentation du projet est générée et publiée par [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) sur
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — preuve que
le pipeline de publication tourne en production.

---

## Stack principale

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Liens

- Site : [cheroliv.com](https://cheroliv.com)
- Plugins publiés : [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick` : [documentation](https://cccp.education/magic-stick/) · [dépôt](https://github.com/cccp-education/magic-stick)

---


