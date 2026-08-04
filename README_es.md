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

## El Ecosistema `education.cccp.*` — 29 boroughs

[`cccp.education`](https://cccp.education/)


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

