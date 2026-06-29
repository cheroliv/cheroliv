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

## `education.cccp.*` 生态系统 — 25 个行政区

插件围绕三个角色分布在 4 层 (DAG N0→N4)。

### 基础 — 可重用构建块 (N0)

| 插件 | 用途 |
|---|---|
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | 代理协议契约 (共享内核) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Codebase RAG 契约 (共享内核) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Vibecoding 契约 (共享内核) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | LLM API 池契约 (共享内核) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Pipeline 契约 (共享内核) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | 国际化契约 (共享内核) |

### 扫描器 — 工作区图提取 (N0)

| 插件 | 用途 |
|---|---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | 从工作区提取知识图谱 (节点、边、社区) → `graph.json` |

### 处理器 — RAG & 数据集 (N1)

| 插件 | 用途 |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | 构建内开发助手：项目读取、pgvector RAG、LangChain4j 上下文增强、AsciiDoc 报告生成、数据集构建。 |

### 消费者 — 内容生成 (N2)

| 插件 | 用途 |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | LLM 提示用于 SPG/SPD (deepseek-v4-pro) — 计划专家将意图分解为 EPICs → 用户故事 → Gradle 任务。 |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF、幻灯片、文档管道 (READ + RAG)。 |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | 从 AsciiDoc 源生成 Reveal.js 演示，推送到专用分支。 |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | 通过 LLM (LangChain4j、7 个提供者、RAG pgvector、KG、API 密钥池) 的 PlantUML 语法验证和渲染 (PNG/SVG)。 |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | 多语言 README 生成，嵌入 PlantUML 图表并发布到 GitHub Pages 通过 JGit。 |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | JBake 静态站点聚合来自其他插件的工件 (图表、幻灯片、文章)。 |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | 视频胶囊捕获 (reveal.js + Playwright + TTS)。 |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | 培训项目编排 — 与代理上下文文件 (`AGENTS.md`) 同步的待办事项列表、课程材料管道 (SPG→SPD→幻灯片→PDFs→表格→仪表板)。 |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | 通过 HyperFrames (HeyGen、Apache 2.0) 进行 AsciiDoc→MP4，Node.js 桥接。 |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | LLM API 密钥池，具有轮换 (轮询、最少使用、加权)、配额跟踪、审计日志记录。 |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | 通过 AsciidoctorJ 的 AsciiDoc 多格式操作 (HTML/PDF/EPUB/DocBook/ManPage) + AI 辅助生成 (WRITE + PUBLISH)。 |

### 编排器 — 部署 (N3)

| 插件 | 用途 |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | DAG 编排、配置 CLI、部署 gh-pages。终端消费者、零业务逻辑。 |

### 控制器 — 敏捷 & 治理 (N4)

| 插件 | 用途 |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | AI 辅助敏捷编排：7 个研讨会 (愿景→架构)、待办事项列表、sprints、速度、里程碑。 |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | GitHub 工单创建和跟踪 — 待办事项列表 → 问题、看板板、提交↔工单链接。 |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | AI 辅助代码审查：PR 分析、质量评分、质量门、秘密检测。 |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | 编排 merge/close/CI： Gates OK 时 merge、自动关闭工单、CI 触发器。 |

### 专用工具 (N2)

| 插件 | 用途 |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster 持久性编排 (clean/generate/sync)，不丢失 `__codebase__/` 中的 Kotlin 代码。 |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | 带 RAG LLM 的 J Hipster AI 助手。 |

### 遗迹 (非活动项目)

| 插件 | 状态 |
|---|---|
| `com.cheroliv.magic-stick` | N2 — Xubuntu ISO 构建器 (文档站点，非插件) |
| `com.cheroliv.newpipe` | N2 — YouTube→MP3 提取器 (已放弃) |
| `com.cheroliv.notebook` | N2 — Colab 可观察性 (仅概念) |
| `com.cheroliv.office-template` | N? — 空模板 (需删除) |
---

## 环境与工作站

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

一个 Gradle Kotlin DSL 构建脚本，协调可启动的 Xubuntu ISO 的创建 — 同时作为 **live USB** 和 **安装程序**，配备三类用户所需的必要工具：

- **移动工作站** — 我完整的可移植环境在 U 盘上。
- **FTTH 电信技术员** — 准备好的现场工具。
- **学生/实习生** — 无需先前安装即可立即上手。

该项目体现了生态系统的理念：工作环境本身就是一个**可重现、版本化、文档化**的 artifacts。项目文档由 [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) 生成并发布在 [cccp.education/magic-stick](https://cccp.education/magic-stick/)上 —— 证明发布管道正在生产运行。
---

## 核心堆栈

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian 打包。
---

## 链接

- 网站：[cheroliv.com](https://cheroliv.com)
- 已发布插件：[Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`：[文档](https://cccp.education/magic-stick/) · [仓库](https://github.com/cccp-education/magic-stick)
---

