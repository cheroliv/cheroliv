# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 **Português** · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Artesão de software · Instrutor · Autor de ferramentas Gradle**

Eu projeto um ecossistema de plugins Gradle Kotlin DSL para ferramentas de projeto,
documentação executável e produção de conteúdo educacional.
Meus materiais brutos: Kotlin, Gradle, AsciiDoc, LangChain4j, Koog.

---

## Posicionamento

Eu trabalho na interseção de três domínios:

- **Artesanato de software** — TDD, BDD Cucumber, Arquitetura Hexagonal, Kotlin idiomática.
- **Ferramentas de desenvolvedor** — plugins Gradle reutilizáveis, publicados sob o namespace `education.cccp` no [Maven Central](https://plugins.gradle.org/search?term=education.cccp).
- **EduTech** — conteúdo educacional, sites estáticos gerados, materiais de treinamento rastreáveis.

A coerência de tudo isso decorre de uma convicção simples: **um desenvolvedor/instrutor credível
constrói e usa suas próprias ferramentas**. Eu não vendo o que eu não uso
no dia a dia.

---

## Metodologia

O ciclo que sigo para cada plugin:

1. **Protótipo da lógica de negócio** dentro do `build.gradle.kts` raiz, com logs relevantes
   para validar o comportamento sob condições reais.
2. **Migração do plugin** assim que a lógica de domínio estiver estável — transplantando o
   código comprovado para um módulo dedicado, usando TDD com JUnit 5.
3. **BDD com Cucumber** assim que o domínio permitir, para documentar
   a intenção no nível do usuário.
4. **Publicação** no Maven Central com um contrato de API versionado.

Não é um método elegante, mas é um que suporta o teste do tempo.

---

## O Ecossistema `education.cccp.*` — 25 boroughs

Os plugins são estruturados em torno de três papéis em 4 camadas (DAG N0→N4).

### Fundação — blocos de construção reutilizáveis (N0)

| Plugin | Função |
|---|---|
| [`agent-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de protocolo de agente (núcleo compartilhado) |
| [`codebase-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos RAG da base de código (núcleo compartilhado) |
| [`vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de vibecoding (núcleo compartilhado) |
| [`llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de pool de API LLM (núcleo compartilhado) |
| [`pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de pipeline (núcleo compartilhado) |
| [`i18n-contracts`](https://github.com/cccp-education/workspace-bom) | Contratos de internacionalização (núcleo compartilhado) |

### Scanner — extração de gráfico de espaço de trabalho (N0)

| Plugin | Função |
|---|---|
| [`graphify`](https://github.com/cccp-education/graphify-gradle) | Extração de gráfico de conhecimento do espaço de trabalho (nós, arestas, comunidades) → `graph.json` |

### Processador — RAG e conjuntos de dados (N1)

| Plugin | Função |
|---|---|
| [`codebase`](https://github.com/cccp-education/codebase-gradle) | Assistente de desenvolvimento integrado: leitura do projeto, RAG pgvector, enriquecimento de contexto LangChain4j, geração de relatório AsciiDoc, criação de conjunto de dados. |

### Consumidor — geração de conteúdo (N2)

| Plugin | Função |
|---|---|
| [`planner`](https://github.com/cccp-education/planner-gradle) | Prompting LLM para SPG/SPD (deepseek-v4-pro) — especialista em planejamento decompondo intenção → EPICs → User Stories → tarefas Gradle. |
| [`codex`](https://github.com/cccp-education/codex-gradle) | Asciidoctor→PDF, slides, pipeline de documento (READ + RAG). |
| [`slider`](https://github.com/cccp-education/slider-gradle) | Geração de apresentações Reveal.js a partir de fontes AsciiDoc, com push para branch dedicado. |
| [`plantuml`](https://github.com/cccp-education/plantuml-gradle) | Validação de sintaxe PlantUML e renderização (PNG/SVG) via LLM (LangChain4j, 7 provedores, RAG pgvector, KG, pool de chaves de API). |
| [`readme`](https://github.com/cccp-education/readme-gradle) | Geração multilíngue de README com diagramas PlantUML embutidos e publicação GitHub Pages via JGit. |
| [`bakery`](https://github.com/cccp-education/bakery-gradle) | Site estático JBake agregando artefatos de outros plugins (diagramas, slides, posts). |
| [`capsule`](https://github.com/cccp-education/capsule-gradle) | Captura de cápsula de vídeo (reveal.js + Playwright + TTS). |
| [`training`](https://github.com/cccp-education/training-gradle) | Orquestração de projeto de treinamento — backlog sincronizado com arquivos de contexto de agente (`AGENTS.md`), pipeline de material do curso (SPG→SPD→Slides→PDFs→Forms→Dashboard). |
| [`hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | AsciiDoc→MP4 via HyperFrames (HeyGen, Apache 2.0), bridge Node.js. |
| [`api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | Pool de chaves de API LLM com rotação (round-robin, menos usado, ponderado), rastreamento de cotas, log de auditoria. |
| [`document`](https://github.com/cccp-education/document-gradle) | Manipulação AsciiDoc multi-formato (HTML/PDF/EPUB/DocBook/ManPage) via AsciidoctorJ + geração assistida por IA (WRITE + PUBLISH). |

### Orquestrador — implantação (N3)

| Plugin | Função |
|---|---|
| [`runner`](https://github.com/cccp-education/runner-gradle) | Orquestração DAG, provisionamento CLI, implantação gh-pages. Consumidor terminal, zero lógica de negócio. |

### Controlador — ágil e governança (N4)

| Plugin | Função |
|---|---|
| [`agile`](https://github.com/cccp-education/agile-gradle) | Orquestração ágil assistida por IA: 7 workshops (Visão→Arquitetura), backlog, sprints, velocidade, marcos. |
| [`ticket`](https://github.com/cccp-education/ticket-gradle) | Criação e rastreamento de tickets GitHub — backlog → Issues, quadro Kanban, link commit↔ticket. |
| [`review`](https://github.com/cccp-education/review-gradle) | Revisão de código assistida por IA: análise PR, pontuação de qualidade, quality gates, detecção de segredos. |
| [`flow`](https://github.com/cccp-education/flow-gradle) | Orquestração merge/close/CI: merge quando as gates OK, auto-fechar tickets, trigger CI. |

### Ferramentas especializadas (N2)

| Plugin | Função |
|---|---|
| [`jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | Orquestração de persistência JHipster (clean/generate/sync) sem perder o código Kotlin em `__codebase__/`. |
| [`jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | Assistente JHipster IA com RAG LLM. |

### Vestígios (projetos inativos)

| Plugin | Status |
|---|---|
| `magic-stick` | N2 — Construtor ISO Xubuntu (site doc, não plugin) |
| `newpipe` | N2 — Extrator YouTube→MP3 (abandonado) |
| `notebook` | N2 — ObservabilidadeColab (apenas conceito) |
| `office-template` | N? — Template vazio (para excluir) |

---

## Ambiente e Estação de Trabalho

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

Um script de build Gradle Kotlin DSL que orquestra a criação de uma ISO Xubuntu inicializável — funcionando como ambos um **live USB** e um **instalador**, equipado com as ferramentas necessárias adaptadas para três perfis de uso:

- **Estação de trabalho nômade** — meu ambiente portátil completo em uma unidade USB.
- **Técnico de telecomunicações FTTH** — ferramentas de campo prontas para uso.
- **Estudante/tremendo** — onboarding imediato sem instalação prévia necessária.

O projeto ilustra a filosofia do ecossistema: o ambiente de trabalho em si
é um **artefato reproduzível, versionado e documentado**. A
documentação do projeto é gerada e publicada por [`bakery`](https://github.com/cccp-education/bakery-gradle) em
[cccp.education/magic-stick](https://cccp.education/magic-stick/) — prova de que
o pipeline de publicação é executado em produção.

---

## Pilha Principal

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Links

- Website: [cheroliv.com](https://cheroliv.com)
- Plugins publicados: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentation](https://cccp.education/magic-stick/) · [repository](https://github.com/cccp-education/magic-stick)

---

