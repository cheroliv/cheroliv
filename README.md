# `cheroliv`

🇬🇧 **English** · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Software Artisan · Trainer · Gradle Tooling Author**

I design an ecosystem of Gradle Kotlin DSL plugins for project tooling,
executable documentation, and educational content production.
My raw materials: Kotlin, Gradle, AsciiDoc, LangChain4j, Koog.

---

## Positioning

I work at the intersection of three domains:

- **Software Craftsmanship** — TDD, BDD Cucumber, Hexagonal Architecture, Idiomatic Kotlin.
- **Developer Tooling** — reusable Gradle plugins, published under the `education.cccp` namespace on the [Maven Central](https://plugins.gradle.org/search?term=education.cccp).
- **EdTech** — educational content, generated static sites, traceable training materials.

The coherence of it all stems from a simple conviction: **a credible developer/trainer
builds and uses their own tools**. I don't sell what I don't use
on a daily basis.

---

## Methodology

The lifecycle I follow for each plugin:

1. **Business logic prototyping** within the root `build.gradle.kts`, with relevant logs
   to validate behavior under real conditions.
2. **Plugin migration** once the domain logic is stable — transplanting the
   proven code to a dedicated module, using TDD with JUnit 5.
3. **BDD with Cucumber** as soon as the domain allows, to document
   intent at the user level.
4. **Publication** to the Maven Central with a versioned API contract.

It's not a fancy method, but it's one that stands the test of time.

---

## The `education.cccp.*` Ecosystem 

[`cccp.education`](https://cccp-education/)


## Environment & Workstation

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

A Gradle Kotlin DSL build script that orchestrates the creation of a bootable Xubuntu ISO — functioning as both a **live USB** and an **installer**, equipped with the necessary tooling tailored for three usage profiles:

- **Nomadic workstation** — my complete portable environment on a USB drive.
- **FTTH Telecom Technician** — ready-to-use field tooling.
- **Student/Trainee** — immediate onboarding with no prior installation required.

The project illustrates the ecosystem's philosophy: the work environment itself
is a **reproducible, versioned, and documented artifact**. The
project's documentation is generated and published by [`bakery`](https://github.com/cccp-education/bakery-gradle) at
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — proof that
the publication pipeline runs in production.

---

## Core Stack

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Links

- Website: [cheroliv.com](https://cheroliv.com)
- Published Plugins: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentation](https://cccp.education/magic-stick/) · [repository](https://github.com/cccp-education/magic-stick)

---

