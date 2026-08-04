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

## The `education.cccp.*` Ecosystem — 29 boroughs

[`cccp.education`](https://cccp.education/)


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

