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

## Экосистема `education.cccp.*` — 29 boroughs

Плагины структурированы вокруг 6 слоев (DAG N0→N4 + N-IDE).

### Фундамент — повторно используемые строительные блоки (N0)

| Плагин | Роль |
|---|---|
| [`api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | Пул API ключей LLM с ротацией (round-robin, least-used, weighted), отслеживание квот, аудит логгирования. |
| [`graphify`](https://github.com/cccp-education/graphify-gradle) | Извлечение графа знаний из рабочего пространства (узлы, ребра, сообщества) → `graph.json` |
| [`agent-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры протокола агента (общее ядро) |
| [`codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры RAG кодовой базы (общее ядро) |
| [`vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры Vibecoding (общее ядро) |
| [`llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры пула API LLM (общее ядро) |
| [`pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры пайплайна (общее ядро) |
| [`i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Договоры интернационализации (общее ядро) |
| [`conventions`](https://github.com/cccp-education/conventions-gradle) | 4 предварительно скомпилированных скриптовых плагина — соглашения о сборке (Cucumber, публикация, подпись, функциональный тест) |
| [`container-provision`](https://github.com/cccp-education/container-provision-gradle) | Предоставление среды выполнения Docker/Colab для LLM (Playwright, пул портов, GPU passthrough) |

### Процессор — RAG и наборы данных (N1)

| Плагин | Роль |
|---|---|
| [`codebase`](https://github.com/cccp-education/codebase-gradle) | Встроенный ассистент разработки: чтение проекта, pgvector RAG, обогащение контекста LangChain4j, генерация отчетов AsciiDoc, создание набора данных. |

### Потребитель — генерация контента (N2)

| Плагин | Роль |
|---|---|
| [`planner`](https://github.com/cccp-education/planner-gradle) | LLM prompting для SPG/SPD (deepseek-v4-pro) — эксперт планирования декомпозирует намерение → EPICs → User Stories → задачи Gradle. |
| [`codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, слайды, пайплайн документа (READ + RAG). |
| [`slider`](https://github.com/cccp-education/slider-gradle) | Генерация презентаций Reveal.js из источников AsciiDoc, с push в выделенную ветку. |
| [`plantuml`](https://github.com/cccp-education/plantuml-gradle) | Валидация синтаксиса PlantUML и рендеринг (PNG/SVG) через LLM (LangChain4j, 7 провайдеров, RAG pgvector, KG, пул API ключей). |
| [`readme`](https://github.com/cccp-education/readme-gradle) | Многоязычная генерация README с встроенными диаграммами PlantUML и публикацией GitHub Pages через JGit. |
| [`bakery`](https://github.com/cccp-education/bakery-gradle) | Статический сайт JBake агрегирующий артефакты от других плагинов (диаграммы, слайды, посты). |
| [`capsule`](https://github.com/cccp-education/capsule-gradle) | Захват видео-капсулы (reveal.js + Playwright + TTS). |
| [`training`](https://github.com/cccp-education/training-gradle) | Оркестрация проекта обучения — бэклог синхронизирован с файлами контекста агента (`AGENTS.md`), пайплайн учебного материала (SPG→SPD→Слайды→PDFs→Формы→Dashboard). |
| [`hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 через HyperFrames (HeyGen, Apache 2.0), Node.js bridge. |
| [`document`](https://github.com/cccp-education/document-gradle) | Манипуляция AsciiDoc многим форматом (HTML/PDF/EPUB/DocBook/ManPage) через AsciidoctorJ + генерация с помощью ИИ (WRITE + PUBLISH). |

### Специализированная инструментария (N2)

| Плагин | Роль |
|---|---|
| [`jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | Оркестрация JHipster persistence (clean/generate/sync) без потери Kotlin кода в `__codebase__/`. |
| [`jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | JHipster ИИ-ассистент с RAG LLM. |

### Оркестратор — развертывание (N3)

| Плагин | Роль |
|---|---|
| [`runner`](https://github.com/cccp-education/runner-gradle) | Оркестрация DAG, provisioning CLI, деплой gh-pages. Терминальный потребитель, нулевая бизнес-логика. |
| [`dashboard`](https://github.com/cccp-education/dashboard-gradle) | Статический сайт для отслеживания видения/прогресса workspace — агрегирует INDEX.adoc и BACKLOG.adoc boroughs. Без LLM/RAG. |
| [`dashboard-flow`](https://github.com/cccp-education/dashboard-flow-gradle) | Интерактивная визуализация React Flow графа знаний `graph.json` (graphify). |

### Контроллер — гибкое управление и управление (N4)

| Плагин | Роль |
|---|---|
| [`agile`](https://github.com/cccp-education/agile-gradle) | Оркестрация Agile с помощью ИИ-ассистента: 7 воркшопов (Видение→Архитектура), бэклог, спринты, скорость, вехи. |
| [`ticket`](https://github.com/cccp-education/ticket-gradle) | Создание и отслеживание GitHub тикетов — бэклог → Issues, доска Kanban, ссылка commit↔ticket. |
| [`review`](https://github.com/cccp-education/review-gradle) | Code review с помощью ИИ: анализ PR, оценка качества, quality gates, обнаружение секретов. |
| [`flow`](https://github.com/cccp-education/flow-gradle) | Оркестрация merge/close/CI: merge когда gates OK, авто-закрытие тикетов, триггер CI. |

### Cockpit — интеграция с IDE (N-IDE)

| Плагин | Роль |
|---|---|
| [`workspace-agent`](https://github.com/cccp-education/workspace-agent) | Плагин IntelliJ Platform — 5 панелей (потребление токенов, KG, сессии, RAG, chains) + действия ИИ в контекстном меню. |

### Вестиги (неактивные проекты)

| Плагин | Статус |
|---|---|
| `magic-stick` | N2 — Строитель ISO Xubuntu (документация сайта, не плагин) |
| `newpipe` | N2 — Извлекатель YouTube→MP3 (заброшен) |
| `notebook` | N2 — Наблюдаемость Colab (только концепция) |
| `office-template` | N? — пустой шаблон (для удаления) |
---

## Окружение и рабочее место

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

Скрипт сборки Gradle Kotlin DSL, который оркестирует создание загружаемого ISO Xubuntu — функционирующего как **live USB** и **установщик**, оснащенного необходимыми инструментами, адаптированными для трех профилей использования:

- **Номадическое рабочее место** — моё полное портативное окружение на USB-накопителе.
- **Техник связи FTTH** — готовые для использования инструменты для полевой работы.
- **Учащийся/Стажер** — немедленное Онбординг без предварительной установки.

Проект иллюстрирует философию экосистемы: само рабочее окружение
является **воспроизводимым, версионированным и документированным артефактом**. Документация проекта генерируется и публикуется [`bakery`](https://github.com/cccp-education/bakery-gradle) на
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

