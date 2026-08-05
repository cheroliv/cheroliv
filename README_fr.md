# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 **Français** · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Software Artisan · Formateur · Auteur d'outils Gradle**

Je conçois un écosystème de plugins Gradle Kotlin DSL pour l'outillage de projet,
la documentation exécutable et la production de contenu pédagogique.

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

## Écosystème `education.cccp.*` — 29 boroughs

[`cccp.education`](https://cccp.education/)


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
documentation du projet est générée et publiée par [`bakery`](https://github.com/cccp-education/bakery-gradle) sur
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

