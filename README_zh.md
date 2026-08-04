# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 **中文** · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**软件工匠 · 培训师 · Gradle 工具作者**

我设计了一套 Gradle Kotlin DSL 插件生态系统，用于项目工具、可执行文档和教育内容生成。
我的原材料：Kotlin、Gradle、AsciiDoc、LangChain4j、Koog。
---

## 定位

我工作于三个领域的交叉点：

- **软件工艺** — TDD、BDD Cucumber、六边形架构、地道 Kotlin。
- **开发者工具** — 可重用的 Gradle 插件，在 [Maven Central](https://plugins.gradle.org/search?term=education.cccp) 下以 `education.cccp` 命名空间发布。
- **教育科技** — 教育内容、生成的静态站点、可追踪的培训材料。

这一切的连贯性源于一个简单的信念：**一个可信的开发人员/培训师必须自己构建并使用自己的工具**。我从不销售我不能每天使用的东西。
---

## 方法论

我为每个插件采用的生命周期：

1. **业务逻辑原型** 在根目录 `build.gradle.kts` 中，使用相关日志验证实际条件下的行为。
2. **插件迁移** 在业务逻辑稳定后 —— 将经过验证的代码传输到专用模块，使用 TDD 与 JUnit 5。
3. **BDD Cucumber** 一旦领域允许，从用户级别记录意图。
4. **发布** 到 Maven Central，带有版本化的 API 合同。

这不是一种花哨的方法，但它经得起时间的考验。
---

## `education.cccp.*` 生态系统 — 29 个行政区

[`cccp.education`](https://cccp.education/)


## 环境与工作站

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

一个 Gradle Kotlin DSL 构建脚本，协调可启动的 Xubuntu ISO 的创建 — 同时作为 **live USB** 和 **安装程序**，配备三类用户所需的必要工具：

- **移动工作站** — 我完整的可移植环境在 U 盘上。
- **FTTH 电信技术员** — 准备好的现场工具。
- **学生/实习生** — 无需先前安装即可立即上手。

该项目体现了生态系统的理念：工作环境本身就是一个**可重现、版本化、文档化**的 artifacts。项目文档由 [`bakery`](https://github.com/cccp-education/bakery-gradle) 生成并发布在 [cccp.education/magic-stick](https://cccp.education/magic-stick/)上 —— 证明发布管道正在生产运行。
---

## 核心堆栈

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian 打包。
---

## 链接

- 网站：[cheroliv.com](https://cheroliv.com)
- 已发布插件：[Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`：[文档](https://cccp.education/magic-stick/) · [仓库](https://github.com/cccp-education/magic-stick)
---

