# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 **বাংলা** · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**সফ্টওয়্যার আর্টিসান · ট্রেনার · গ্রেডল টুলিং অথর**

আমি প্রজেক্ট টুলিং, এক্সিকিউটেবল ডকুমেন্টেশন এবং শিক্ষানবিস সামগ্রী উত্পাদনের জন্য গ্রেডল কোটলিন ডিএসএল প্লাগইনের একটি ইকোসিস্টেম ডিজাইন করি।
আমার কাঁচা উপাদান: কোটলিন, গ্রেডল, এস্কিডোক, ল্যাংচেন4জ, কুগ।

---

## পজিশনিং

আমি তিনটি ডোমেনের সংযোগস্থলে কাজ করি:

- **সফ্টওয়্যার ক্রাফ্টসম্যানশিপ** — টিডিডি, বিডিডি কার্কবার, হেক্সাগোনাল আর্কিটেকচার, আইডিওম্যাটিক কোটলিন।
- **ডেভেলপার টুলিং** — পুনরায় ব্যবহারযোগ্য গ্রেডল প্লাগইন, পরিষ্কার [Maven Central](https://plugins.gradle.org/search?term=education.cccp) এ `education.cccp` নেমস্পেসে প্রকাশিত।
- **এডটেক** — শিক্ষাবিদ্যা সামগ্রী, উত্পন্ন স্ট্যাটিক সাইটস, ট্রেসেবল ট্রেনিং ম্যাটেরিয়াল।

এর সমস্ত স্থায়িত্ব একটি সাধারণ বিশ্বাসের উপর ভিত্তি করে: **একজন বিশ্বস্ত ডেভেলপার/ট্রেনার
তাদের নিজেদের টুল তৈরি করে এবং ব্যবহার করে**। আমি যা বিক্রি করি না যা আমি দৈনন্দিন ব্যবহার করি না।

---

## আর্কিটেকচার আইডেন্টিটি — 4 ডোমেন, 3 অ্যাকাউন্ট

### ব্র্যান্ড পৃথকীকরণ

| ডোমেন | ভূমিকা | সিগন্যাল |
|---|---|---|
| `cheroliv.com` | ব্যক্তিগত পরিচয়, ব্লগ, নিবন্ধ | কোডের পিছনে মানুষ, সম্পাদকীয় কণ্ঠস্বর, সামাজিক মূলধন |
| `talarіаl.sсhооl` | ওয়েফ — যোগ্যতা ভিত্তিক প্রশিক্ষণ প্রতিষ্ঠান | প্রতিষ্ঠানিক ভিট্রিন এবং প্রশিক্ষণ ক্যাটালগ |
| `edster.cloud` | এসএসএ — নিবেদিত ক্লাউড অবকাঠামো | গ্রাহক ওয়ার্কস্পেস প্রমুখ (এমভিপি১) |
| `cccр·eduсаtiоn` | ডোমেন (এসএসএ/ওয়েব) | *কমন কন্টেন্ট ক্রিয়েটর প্রলেটারিয়ান* — ডিজিটাল পরিচয় এবং ওএসএস ভিট্রিন |

### প্রযুক্তিগত অ্যাকাউন্ট পৃথকীকরণ

| অ্যাকাউন্ট | প্ল্যাটফর্ম | ভূমিকা |
|---|---|---|
| `cheгo liv` | GitHub | কমিটস, পিআর, ইতিহাস, সামাজিক মূলধন (অপরিবর্তিত) |
| `cccp-education` | GitHub (সংগঠন) | প্লাগইন রিপোজিটরি হোস্টিং, পণ্য ব্র্যান্ড |
| `cccр-eduсаtіоn` | Maven Central | প্রকাশনা হ্যান্ডেল — https://central.sonatype.com/namespace/education.cccp |

### 3-প্রস্তর আর্কিটেকচার

```
cheroliv (dev) ──commits──▶ github.com/cccp-education (repos) ──publish──▶ cccp-education (Gradle Portal)
                               গ্রুপ ID: education.cccp
                               লাইসেন্স: অ্যাপাচি 2.0
```

*নিয়ম*: ব্যবসা স্বাধীন (অ্যাপাচি 2.0), শুধুমাত্র ব্যাংকিং লেনদেন (waiter-gradle) নয়।
কোডে কোনো আদর্শ নেই — গ্রুপ আইডি থাকে, তাই।

---

## মেথডোলজি

প্রতিটি প্লাগইনের জন্য যে চক্র আমি অনুসরণ করি:

1. **ব্যবসায়িক লজিক প্রোটোটাইপিং** মূল `build.gradle.kts` এর ভেতর, প্রাসঙ্গিক লগগুলির সাথে
   বাস্তব অবস্থার অধীনে আচরণ যাচাই করার জন্য।
2. **প্লাগইন মাইগ্রেশন** একবার যখন ডোমেন লজিক স্থিতিশীল হয়ে যায় — স্থানান্তর
   প্রমাণিত কোড একটি সমর্পিত মডিউলে, জেয়ুনিট 5 এর সাথে টিডিডি ব্যবহার করে।
3. **BDD কার্কবারের সাথে** যখন ডোমেন অনুমতি দেয়, ব্যবহারকারীর স্তরে
   ইচ্ছা বিবরণীয় করার জন্য।
4. **প্রকাশনা** Maven Centralে একটি সংস্করণযুক্ত এপিআই চুক্তির সাথে।

এটি একটি দমদার পদ্ধতি নয়, তবে এটি একটি যে সময়ের পরীক্ষা পার হয়।

---

## `education.cccp.*` ইকোসিস্টেম — ২৫ বোরোহস

প্লাগইনগুলি চার স্তর (DAG N0→N4) এর মধ্যে তিনটি ভূমিকার চারপাশে গঠিত।

### ফাউন্ডেশন — পুনরায় ব্যবহারযোগ্য বিল্ডিং ব্লক (N0)

| প্লাগইন | ভূমিকা |
|---|---|
| [`com.gradleup.nmcp.settings`](https://plugins.gradle.org/plugin/com.gradleup.nmcp.settings) | Maven Central প্রকাশনা (nmcp) |
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | এজেন্ট প্রোটোকল চুক্তি (শেয়ার্ড কার্নেল) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | কোডবেস র্যাগ চুক্তি (শেয়ার্ড কার্নেল) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | ভাইবেকোডিং চুক্তি (শেয়ার্ড কার্নেল) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | এলএলএম এপিআই পুল চুক্তি (শেয়ার্ড কার্নেল) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | পাইপলাইন চুক্তি (শেয়ার্ড কার্নেল) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | আন্তর্জাতীয়করণ চুক্তি (শেয়ার্ড কার্নেল) |

### স্ক্যানার — ওয়ার্কস্পেস গ্রাফ এক্সট্র্যাকশন (N0)

| প্লাগইন | ভূমিকা |
|---|---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | ওয়ার্কস্পেস থেকে জ্ঞান গ্রাফ (নোডস, এজস, সম্প্রদায়) → `graph.json` এর এক্সট্র্যাকশন |

### প্রসেসর — র্যাগ & ডেটাসেট (N1)

| প্লাগইন | ভূমিকা |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | বিল্ড-ইন ডেভেলপমেন্ট সহায়ক: প্রজেক্ট রিডিং, pgvector র্যাগ, ল্যাংচেন4জ কন্টেক্সট এনরিচমেন্ট, এস্কিডোক রিপোর্ট জেনারেশন, ডেটাসেট তৈরি। |

### কনজুমার — কন্টেন্ট জেনারেশন (N2)

| প্লাগইন | ভূমিকা |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | এলএলএম প্রম্প্টিং এসপিজি/এসপিডি এর জন্য (deepseek-v4-pro) — প্লানিং এক্সপার্ট ইচ্ছাকে এপিআইসি → ইউজার স্টোরিজ → গ্রেডল টাস্কে বিভক্ত করে। |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | এস্কিডোর্টার→পিডিএফ, স্লাইড, ডকুমেন্ট পাইপলাইন (রিড + র্যাগ)। |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | এস্কিডোক উৎস থেকে রিভিল.js প্রেজেন্টেশন জেনারেশন, একটি সমর্পিত শাখায় পুশ করে। |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | এলএলএম (ল্যাংচেন4জ, ৭ প্রভাইডার, র্যাগ pgvector, কেজি, পুল এপিআই কী) এর মাধ্যমে প্ল্যান্টইউএমএল সিনট্যাক্স যাচাই এবং রেন্ডারিং (পিএনজি/এসভিজি)। |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | এম্বেডেড প্ল্যান্টইউএমএল ডায়াগ্রাম এবং গিটহাব পেজেস প্রকাশনা জেগিটের মাধ্যমে বহুভাষা README জেনারেশন। |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | জেবেক স্ট্যাটিক সাইট এগ্রিগেটিং অন্যান্য প্লাগইন (ডায়াগ্রাম, স্লাইড, পোস্ট) দ্বারা উৎপন্ন আর্টিফ্যাক্ট। |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | ভিডিও ক্যাপসুল ক্যাপচার (রিভিল.জেএস + প্লেরাইট + টিটিএস)। |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | ট্রেনিং প্রজেক্ট অর্কেস্ট্রেশন — এজেন্ট কন্টেক্সট ফাইল (`AGENTS.md`) এর সাথে সিঙ্ক্রোনাইজ ব্যাকলগ, কোর্স ম্যাটেরিয়াল পাইপলাইন (এসপিজি→এসপিডি→স্লাইড→পিডিএফ→ফর্ম→ড্যাশবোর্ড)। |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | এস্কিডোক→এমপি৪ হাইপারফ্রেম (হেয়েজেন, অ্যাপাচি ২.০) এর মাধ্যমে, নোডজেএস ব্রিজ। |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | এলএলএম এপিআই কী পুল রোটেশন সহ (রাউন্ড-রোবিন, লিস্ট-ইউজড, ওয়েটেড), কোয়োটা ট্র্যাকিং, অডিট লগিং। |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | এস্কিডোর্টারজের মাধ্যমে এস্কিডোক মাল্টি-ফরম্যাট (এইচটিএমএল/পিডিএফ/ইপিউবি/ডোকবুক/ম্যানপেজ) ম্যানিপুলেশন + এআই-সহায়ক জেনারেশন (লিখুন + পাবলিশ)। |

### অর্কেস্ট্রেটর — ডিপ্লয়মেন্ট (N3)

| প্লাগইন | ভূমিকা |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | ড্যাগ অর্কেস্ট্রেশন, প্রভিশনিংসি এলআই, ডিপ্লয় ঘিপেজ। টার্মিনাল কনজুমার, জিরো ব্যবসায়িক যুক্তি। |

### কন্ট্রোলার — এজাইল & গভর্নেন্স (N4)

| প্লাগইন | ভূমিকা |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | এআই সহায়ক এজাইল অর্কেস্ট্রেশন: ৭ ওয়ার্কশপ (ভিজন→আর্কিটেকচার), ব্যাকলগ, স্প্রিন্ট, ভেলোসিটি, মাইলস্টোন। |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | গিটহাব টিকেট তৈরি এবং ট্র্যাকিং — ব্যাকলগ → ইস্যু, কানবান বোর্ড, কমিট↔টিকেট লিংকিং। |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | এআই সহায়ক কোড রিভিউ: পিআর বিশ্লেষণ, গুণমান স্কোর, গুণমান গেট, রহস্য সনাক্তকরণ। |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | অর্কেস্ট্রেশন merge/close/CI: গেট ঠিক হলে merge, স্বয়ংক্রিয় বন্ধ টিকেট, সিআই ট্রিগার। |

### স্পেশালাইজড টুলিং (N2)

| প্লাগইন | ভূমিকা |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | জেএইচপিরসিস্টেন্স অর্কেস্ট্রেশন (clean/generate/sync) `__codebase__/` এ কোটলিন কোড হারানো ছাড়াই। |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | আরজিএলএলএম সহিত জেএইচপিস্টার এআই সহায়ক। |

### ভেস্টিজ (নিষ্ক্রিয় প্রজেক্ট)

| প্লাগইন | স্ট্যাটাস |
|---|---|
| `com.cheroliv.magic-stick` | N2 — জেক্সবাক্টু আইএসও বিল্ডার (ডক সাইট, প্লাগিন নয়) |
| `com.cheroliv.newpipe` | N2 — YouTube→MP3 এক্সট্র্যাক্টর (ত্যাগ করা) |
| `com.cheroliv.notebook` | N2 — কোলাব অবসার্বরেবিলিটি (কেবল ধারণা) |
| `com.cheroliv.office-template` | N? — খালি টেম্পলেট (মুছে ফেলার জন্য) |

---

## পরিবেশ এবং কর্মস্থল

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

একটি গ্রেডল কোটলিন ডিএসএল বিল্ড স্ক্রিপ্ট যা একটি বুটেবল এক্সবাক্টু আইএসও তৈরির সংগঠন করে — এক **লাইভ ইউএসবি** এবং **ইন্সটলার** হিসেবে কাজ করে, তিনটি ব্যবহার প্রোফাইলের জন্য প্রয়োজনীয় টুলিং সম্পন্ন:

- **নোমাডিক কর্মস্থল** — আমার সম্পূর্ণ পোর্টেবল পরিবেশ ইউ-ড্রাইভে।
- **এফটিএইচ টেলিকম টেকনিশিয়ান** — ক্ষেত্রে ব্যবহারের জন্য প্রস্তুত টুলিং।
- **ছাত্র/প্রশিক্ষণার্থী** — কোনো পূর্ব-ইন্সটলেশনের প্রয়োজন ছাড়াই তাৎক্ষণিক অনবোর্ডিং।

এই প্রজেক্টটি ইকোসিস্টেমের দর্শন প্রদর্শন করে: কর্মস্থল নিজেও একটি **পুনরুৎপাদনযোগ্য, সংস্করণযোগ্য, ও দস্তাবেজযুক্ত** আর্টিফ্যাক্ট। প্রজেক্টের ডকুমেন্টেশন তৈরি এবং প্রকাশিত হয় [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) দ্বারা [cccp.education/magic-stick](https://cccp.education/magic-stick/) এ — যা প্রমাণ করে যে প্রকাশনা পাইপলাইন উৎপাদনে চলছে।

---

## কোর স্ট্যাক

জাভা · কোটলিন · গ্রেডল (কোটলিন ডিএসএল) · জেউনিট ৫ · কাকুবার · স্প্রিং বুট · এস্কিডোক · জেবেক · রিভিল.জেএস · প্ল্যান্টইউএমএল · জেগিট · জ্যাকসন · ল্যাংচেন4জ · কুগ · ডকার · পোস্টগ্রেএসকিউএল/পিজিভেক্টর · গিটহাব অ্যাকশন · এক্সবাক্টু/ডেবিয়ান প্যাকেজিং।

---

## লিঙ্ক

- ওয়েবসাইট: [cheroliv.com](https://cheroliv.com)
- প্রকাশিত প্লাগইন: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [ডকুমেন্টেশন](https://cccp.education/magic-stick/) · [রিপোজিটরি](https://github.com/cccp-education/magic-stick)

---


