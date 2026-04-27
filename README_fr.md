# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 **Français**

**Software Artisan · Formateur · Auteur d'outils Gradle**

Je conçois un écosystème de plugins Gradle Kotlin DSL pour l'outillage de projet,
la documentation exécutable et la production de contenu pédagogique.
Ma matière première : Kotlin, Gradle, AsciiDoc, LangChain4j.

---

## Positionnement

Je travaille à l'intersection de trois domaines :

- **Craft logiciel** — TDD, BDD Cucumber, architecture hexagonale, Kotlin idiomatique.
- **Outillage développeur** — plugins Gradle réutilisables, publiés sous le namespace `com.cheroliv` sur le [Gradle Plugin Portal](https://plugins.gradle.org/search?term=com.cheroliv).
- **Edtech** — contenus pédagogiques, sites statiques générés, supports de formation traçables.

La cohérence de l'ensemble tient à une conviction simple : **un développeur/formateur crédible
construit et utilise ses propres outils**. Je ne vends pas ce que je n'utilise pas
au quotidien.

---

## Méthode

Le cycle que je suis sur chaque plugin :

1. **Tâtonnement métier** dans le `build.gradle.kts` racine, avec logs pertinents
   pour valider le comportement en conditions réelles.
2. **Migration vers plugin** quand le métier est stabilisé — transplantation du
   code éprouvé vers un module dédié, sous TDD avec JUnit 5.
3. **BDD Cucumber** dès que le domaine métier le permet, pour documenter
   l'intention à hauteur d'usager.
4. **Publication** sur le Gradle Plugin Portal avec un contrat d'API versionné.

Ce n'est pas une méthode chic, c'est une méthode qui tient debout sur la durée.

---

## Écosystème `com.cheroliv.*`

Les plugins s'articulent autour de trois rôles :

### Fondation — briques réutilisables

| Plugin | Rôle |
|---|---|
| [`com.cheroliv.plantuml`](https://github.com/cheroliv/plantuml-gradle) | Validation syntaxique et rendu PNG/SVG de diagrammes PlantUML. Brique utilisée par les plugins en aval et consommable seule. |
| [`com.cheroliv.readme`](https://github.com/cheroliv/readme-plugin) | Génération de README multilingues avec diagrammes PlantUML embarqués et publication GitHub Pages via JGit. |
| [`com.cheroliv.slider`](https://github.com/cheroliv/slider-gradle) | Génération de présentations Reveal.js depuis des sources AsciiDoc, avec push vers branche dédiée. |

### Publication & agrégation

| Plugin | Rôle |
|---|---|
| [`com.cheroliv.bakery`](https://github.com/cheroliv/bakery-gradle-plugin) | Site statique JBake agrégeant les artefacts produits par les autres plugins (diagrammes, slides, posts). Une [version Scala/Mill](https://github.com/cheroliv/millBakerPlugin) de la même idée existe également. |

### Assistant de build & orchestration pédagogique

| Plugin | Rôle |
|---|---|
| [`com.cheroliv.codebase`](https://github.com/cheroliv/codebase-gradle) | Assistant de développement embarqué dans le build : lecture et analyse du projet, enrichissement de contexte LangChain4j, génération de rapports AsciiDoc, constitution de datasets. |
| [`com.cheroliv.training`](https://github.com/cheroliv/training-gradle) | Orchestration de projet de formation — backlog synchronisé avec les fichiers de contexte agent (`AGENTS.md`), pipeline de production des supports de cours. |

Chaque plugin suit la même discipline de configuration : YAML déclaratif
(`readme.yml`, `plantuml-context.yml`, `slides-context.yml`…), classes Kotlin
miroir via Jackson, et fonction d'anonymisation pour la traçabilité sans fuite
de secret.

---

## Environnement & poste de travail

### [`magic_stick`](https://github.com/cheroliv/magic_stick)

Build script Gradle Kotlin DSL qui orchestre la construction d'une ISO Xubuntu
bootable — à la fois **live USB** et **installateur**, équipée de l'outillage
nécessaire selon trois profils d'usage :

- **Poste de travail nomade** — mon environnement complet portable sur une clé.
- **Technicien télécom FTTH** — l'outillage terrain prêt à l'emploi.
- **Apprenant en formation** — une mise en route immédiate sans installation préalable.

Le projet illustre la philosophie de l'écosystème : l'environnement de travail
est lui-même un **artefact reproductible, versionné, documenté**. La
documentation du projet est générée et publiée par [`com.cheroliv.bakery`](https://github.com/cheroliv/bakery-gradle-plugin) sur
[cheroliv.com/magic_stick](https://cheroliv.com/magic_stick/) — preuve que
le pipeline de publication tourne en production.

---

## Ce que j'enseigne

- Java (8 à 25) de niveau intermédiaire à avancé — de l'API Stream aux Virtual Threads, Records, Pattern Matching.
- Kotlin de niveau intermédiaire à avancé — null safety, extensions, coroutines, sealed classes.
- Scala et alternatives de build JVM (Mill, sbt).
- Maven architectures multi-modules. 
- Gradle Kotlin DSL — de l'écriture de tâches au plugin publiable.
- Architecture hexagonale et tests — ports & adapters, JUnit 5, Cucumber, TestContainers.
- Spring Boot — API REST, sécurité JWT, tests d'intégration.
- Outillage de projet — CI/CD GitHub Actions, documentation exécutable, génération de contenu.

Les supports de cours sont produits avec les plugins de l'écosystème : les
slides sont du Reveal.js généré par [`slider`](https://github.com/cheroliv/slider-gradle),
les sites de cours par [`bakery`](https://github.com/cheroliv/bakery-gradle-plugin),
la clé de démarrage par [`magic_stick`](https://github.com/cheroliv/magic_stick).
La formation et l'outil se nourrissent mutuellement.

---

## Stack principale

Java · Kotlin · Scala · Gradle (Kotlin DSL) · Mill · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Liens

- Site : [cheroliv.com](https://cheroliv.com)
- Plugins publiés : [Gradle Plugin Portal — com.cheroliv](https://plugins.gradle.org/search?term=com.cheroliv)
- `magic_stick` : [documentation](https://cheroliv.com/magic_stick/) · [dépôt](https://github.com/cheroliv/magic_stick)

---

*Le code qu'on écrit pour soi est le laboratoire du code qu'on enseigne aux autres.*