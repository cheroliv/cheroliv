# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 **Português** · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**Artesão de software · Instrutor · Autor de ferramentas Gradle**

Eu projeto um ecossistema de plugins Gradle Kotlin DSL para ferramentas de projeto,
documentação executável e produção de conteúdo educacional.

---

## Posicionamento

Eu trabalho na interseção de três domínios:

- **Artesanato de software** — TDD, BDD Cucumber, Arquitetura Hexagonal, Kotlin idiomática.
- **Ferramentas de desenvolvedor** — plugins Gradle reutilizáveis, publicados sob o namespace `education.cccp` no [github.com/cccp-education](https://github.com/cccp-education).
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

## O Ecossistema `education.cccp.*` — 29 boroughs

[`cccp.education`](https://cccp.education/)


---

## Pilha Principal

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging.

---

## Links

- Website: [cheroliv.com](https://cheroliv.com)
- Plugins publicados: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [documentation](https://cccp.education/magic-stick/) · [repository](https://github.com/cccp-education/magic-stick)

---

