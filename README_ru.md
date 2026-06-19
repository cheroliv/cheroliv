# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 **Русский** · 🇵🇰 [اردو](README_ur.md)

**Мастер программного обеспечения · Тренер · Автор инструмента Gradle**

Я проектирую экосистему плагинов Gradle Kotlin DSL для инструментов проекта,
исполняемой документации и производства образовательного контента.
Мои исходные материалы: Kotlin, Gradle, AsciiDoc, LangChain4j, Koog.
---

## Позиционирование

Я работаю на стыке трех доменов:

- **Программное ремесло** — TDD, BDD Cucumber, Гексагональная архитектура, Идиоматичный Kotlin.
- **Инструменты разработчика** — повторно используемые плагины Gradle, опубликованные под пространством имен `education.cccp` на [Maven Central](https://plugins.gradle.org/search?term=education.cccp).
- **EdTech** — образовательный контент, генерируемые статические сайты, прослеживаемые учебные материалы.

Согласованность всего этого исходит из простого убеждения: **достоверный разработчик/тренер
создает и использует собственные инструменты**. Я не продаю то, что не использую
в повседневной жизни.
---

## Архитектурная идентичность — 4 домена, 3 аккаунта

### Разделение брендов

| Домен | Роль | Сигнал |
|
---|
---|
---|
| `cheroliv.com` | Личная идентичность, блог, статьи | Человек за кодом, редакционный голос, социальный капитал |
| `talaria.school` | OF — Организация Обучения Квалипио | Институциональный фронт и каталог обучения |
| `edster.cloud` | SaaS — Выделенная облачная инфраструктура | Провижнинг клиентских рабочих пространств (MVP1) |
| `cccp.education` | Домен (SaaS/Веб) | *Common Content Creator Proletarian* — цифровая идентичность и фронт OSS |

### Разделение технических аккаунтов

| Аккаунт | Платформа | Роль |
|
---|
---|
---|
| `cheroliv` | GitHub | Коммиты, PRs, история, социальный капитал (без изменений) |
| `cccp-education` | GitHub (организация) | Хостинг репозиториев плагинов, продукт бренда |
| `cccp-education` | Maven Central | Контроль публикации — https://central.sonatype.com/namespace/education.cccp |


---

## Методология

Жизненный цикл, который я следую для каждого плагина:

1. **Прототипирование бизнес-логики** в корне `build.gradle.kts`, с соответствующими логами
   для проверки поведения в реальных условиях.
2. **Миграция плагина** как только логика домена стабилизируется — трансплантация
   проверенного кода в выделенный модуль, используя TDD с JUnit 5.
3. **BDD с Cucumber** как только домен позволяет, для документирования
   намерения на уровне пользователя.
4. **Публикация** на Maven Central с версионированным API контрактом.

Это не fancy метод, но тот, который выдерживает испытание временем.
---

## Экосистема `education.cccp.*` — 25 boroughs

Плагины структурированы вокруг трех ролей в 4 слоях (DAG N0→N4).

### Фундамент — повторно используемые строительные блоки (N0)

| Плагин | Роль |
|
---|
---|
| [`com.gradleup.nmcp.settings`](https://plugins.gradle.org/plugin/com.gradleup.nmcp.settings) | Публикация Maven Central (nmcp) |
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры протокола агента (общее ядро) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры RAG кодовой базы (общее ядро) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры Vibecoding (общее ядро) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры пула API LLM (общее ядро) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры пайплайна (общее ядро) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры интернационализации (общее ядро) |

### Сканер — извлечение графа рабочего пространства (N0)

| Плагин | Роль |
|
---|
---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | Извлечение графа знаний из рабочего пространства (узлы, ребра, сообщества) → `graph.json` |

### Процессор — RAG и наборы данных (N1)

| Плагин | Роль |
|
---|
---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | Встроенный ассистент разработки: чтение проекта, pgvector RAG, обогащение контекста LangChain4j, генерация отчетов AsciiDoc, создание набора данных. |

### Потребитель — генерация контента (N2)

| Плагин | Роль |
|
---|
---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting для SPG/SPD (deepseek-v4-pro) — эксперт планирования декомпозирует намерение → EPICs → User Stories → задачи Gradle. |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, слайды, пайплайн документа (READ + RAG). |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | Генерация презентаций Reveal.js из источников AsciiDoc, с push в выделенную ветку. |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | Валидация синтаксиса PlantUML и рендеринг (PNG/SVG) через LLM (LangChain4j, 7 провайдеров, RAG pgvector, KG, пул API ключей). |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | Многоязычная генерация README с встроенными диаграммами PlantUML и публикацией GitHub Pages через JGit. |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | Статический сайт JBake агрегирующий артефакты от других плагинов (диаграммы, слайды, посты). |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | Захват видео-капсулы (reveal.js + Playwright + TTS). |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | Оркестрация проекта обучения — бэклог синхронизирован с файлами контекста агента (`AGENTS.md`), пайплайн учебного материала (SPG→SPD→Слайды→PDFs→Формы→Dashboard). |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 через HyperFrames (HeyGen, Apache 2.0), Node.js bridge. |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | Пул API ключей LLM с ротацией (round-robin, least-used, weighted), отслеживание квот, аудит логгирования. |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | Манипуляция AsciiDoc многим форматом (HTML/PDF/EPUB/DocBook/ManPage) через AsciidoctorJ + генерация с помощью ИИ (WRITE + PUBLISH). |

### Оркестратор — развертывание (N3)

| Плагин | Роль |
|
---|
---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | Оркестрация DAG, provisioning CLI, деплой gh-pages. Терминальный потребитель, нулевая бизнес-логика. |

### Контроллер — гибкое управление и управление (N4)

| Плагин | Роль |
|
---|
---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | Оркестрация Agile с помощью ИИ-ассистента: 7 воркшопов (Видение→Архитектура), бэклог, спринты, скорость, вехи. |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | Создание и отслеживание GitHub тикетов — бэклог → Issues, доска Kanban, ссылка commit↔ticket. |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | Code review с помощью ИИ: анализ PR, оценка качества, quality gates, обнаружение секретов. |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | Оркестрация merge/close/CI: merge когда gates OK, авто-закрытие тикетов, триггер CI. |

### Специализированная инструментария (N2)

| Плагин | Роль |
|
---|
---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | Оркестрация JHipster persistence (clean/generate/sync) без потери Kotlin кода в `__codebase__/`. |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster ИИ-ассистент с RAG LLM. |

### Вестиги (неактивные проекты)

| Плагин | Статус |
|
---|
---|
| `com.cheroliv.magic-stick` | N2 — Строитель ISO Xubuntu (документация сайта, не плагин) |
| `com.cheroliv.newpipe` | N2 — Извлекатель YouTube→MP3 (заброшен) |
| `com.cheroliv.notebook` | N2 — Наблюдаемость Colab (только концепция) |
| `com.cheroliv.office-template` | N? — пустой шаблон (для удаления) |
---

## Окружение и рабочее место

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

Скрипт сборки Gradle Kotlin DSL, который оркестирует создание загружаемого ISO Xubuntu — функционирующего как **live USB** и **установщик**, оснащенного необходимыми инструментами, адаптированными для трех профилей использования:

- **Номадическое рабочее место** — моё полное портативное окружение на USB-накопителе.
- **Техник связи FTTH** — готовые для использования инструменты для полевой работы.
- **Учащийся/Стажер** — немедленное Онбординг без предварительной установки.

Проект иллюстрирует философию экосистемы: само рабочее окружение
является **воспроизводимым, версионированным и документированным артефактом**. Документация проекта генерируется и публикуется [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) на
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — доказательство того, что
пайплайн публикации запущен в производство.
---

## Основной стек

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian упаковка.
---

## Ссылки

- Веб-сайт: [cheroliv.com](https://cheroliv.com)
- Опубликованные плагины: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [документация](https://cccp.education/magic-stick/) · [репозиторий](https://github.com/cccp-education/magic-stick)
---


