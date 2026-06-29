# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 [हिन्दी](README_hi.md) · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 **اردو**

**software artisan · trainer · gradle tooling author**

میں پروجیکٹ ٹولنگ، قابل اجرا دستاویزات اور تعلیمی مواد کی پیداوار کے لیے گریڈل کوٹلن ڈی ایس ایل پلگ انز کا ایک生态系统 ڈیزائن کرتا ہوں۔
میریخام مادہ: کوچل، گریڈل، ای ایس کی ڈوک، lan چین4ج، koog۔
---

## پوزیشننگ

میں تین_domains کے تقاطع پر کام کرتا ہوں:

- **software craftsmanship** — ٹی ڈی ڈی، بی ڈی ڈی کرکبر، ہیکسیگونل آرکی ٹیکچر، ایدوماتک کوٹلن۔
- **developer tooling** — دوبارہ استعمال کے قابل گریڈل پلگ انز، پر [Maven Central](https://plugins.gradle.org/search?term=education.cccp) پر `education.cccp` نیمسپیس کے تحت شائع ہوں۔
- **edtech** — تعلیمی مواد، جنریٹڈ اسٹیٹک سائٹس، ٹریسیبل ٹریننگ میٹریالز۔

اس کی سب کچھ کی ہم آہنگی ایک سادہ عقیدے سے نکلتی ہے: **ایک قابل اعتماد ڈویلپر/ٹرینر
اپنے اپنے ٹولز بناتا ہے اور ان کا استعمال کرتا ہے**۔ میں جو فروخت نہیں کرتا جو میں نے روزمرہ استعمال نہیں کرتا۔
---

## میتھڈولوجی

ہر پلگ ان کے لیے میرے فالو کرنے والی لائف سائیکل:

1. **business logic prototyping** root `build.gradle.kts` میں، معنیٰ لاگ کے ساتھ
   حقیقی شرائط کے تحت رویہ کی تصدیق کے لیے۔
2. **plugin migration** ایک بار جب domain logic مستقر ہو جاتی ہے — کود کو ایک مخصوص ماڈیول میں منتقل کرنا
   ایک پروفیسڈ کوڈ، یو ٹی 5 کے ساتھ ٹی ڈی ڈی کے ساتھ۔
3. **bdd with cucumber** جب بھی domain اجازت دے، صارف کے لیے دستاویز
   نیتی کو مستقل سطح پر۔
4. **publication** Maven Central پر ایک ورژن ایپی آئی کے ساتھ۔

یہ ایک شاندار طریقہ نہیں ہے، لیکن یہ ایک ہے جو وقت کے ٹیسٹ کو برقرار رکھتا ہے۔
---

## `education.cccp.*` اکوسسٹم — 25 بوروہس

پلگ انز N0→N4 (دی ای گریڈ ان 4) میں چار پرتیں کے ارد گرد تین کرداروں کے گرد بنے ہوئے ہیں۔

### فاؤنڈیشن — دوبارہ استعمال کے قابل بننے کے اجزاء (N0)

| پلگ ان | رول |
|---|---|
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | اジェنٹ پروٹوکول کنٹریکٹس (شیئرڈ کرنل) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | کوڈ بیس ریگ کنٹریکٹس (شیئرڈ کرنل) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | وائیبیکوڈنگ کنٹریکٹس (شیئرڈ کرنل) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | ایل ایل ایم اے پی آئی پول کنٹریکٹس (شیئرڈ کرنل) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | پائپ لائن کنٹریکٹس (شیئرڈ کرنل) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | انٹرنیشنلائزیشن کنٹریکٹس (شیئرڈ کرنل) |

### اسکینر — ورک اسپیس گراف ایکسٹریکشن (N0)

| پلگ ان | رول |
|---|---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | ورک اسپیس سے جیان کا گراف (نود، اج، کمیونٹیز) → `graph.json` کا ایکسٹریکشن |

### پروسیسر — ریگ اینڈ ڈیٹا سیٹ (N1)

| پلگ ان | رول |
|---|---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | بِلڈ-ان ڈویلپمنٹ اسسٹنٹ: پراجیکٹ ریڈنگ، پی جی ویکٹر ریگ، lan چین4ج کنٹیکسٹ اینرچمنٹ، ایس کی ڈوک رپورٹ جنریشن، ڈیٹا سیٹ کریشن۔ |

### کنجرمر — مواد جنریشن (N2)

| پلگ ان | رول |
|---|---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | ایل ایل ایم پرومپٹنگ ایس پی جی/ایس پی ڈی کے لیے ( deepseek-v4-pro) — پلاننگ ماہر نیتی کو ایپکس → یوزر اسٹوریز → گریڈل ٹاسک میں تقسیم کرتا ہے۔ |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | ایس کی ڈوکٹر→پی ڈی ایف، سلائیڈز، دستاویز پائپ لائن (ریڈ + ریگ)۔ |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | ایس کی ڈوک سورس سے ریویل.جی ایس پریزنٹیشن جنریشن، ایک مخصوص برانچ میں پش کے ساتھ۔ |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | لیم (lan چین4ج، 7 پراوائیڈرز، ریگ پی جی ویکٹر، کی جی، پول ایپی کی کیز) کے ذریعے پلینٹیول سینٹیکس کی تصدیق اور رینڈرنگ (پی این جی/ایس وی جی)۔ |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | ایمبیڈیڈ پلا نٹیول ڈائیاگرامس کے ساتھ بہ زبان ریڈمی جنریشن اور گیتہاب پیجز پبلیکیشن جیگٹ کے ذریعے۔ |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | جی بیک اسٹیٹک سائٹ ایگریگیشن دیگر پلگ انز (ڈائیاگرامس، سلائیڈز، پوسٹس) کے ذریعے پیدا کردہ آرٹی فیکٹس۔ |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | ویڈیو کیپسول کیپچر (ریول.جی ایس + پلے رائٹ + ٹی ٹی ایس)۔ |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | ٹریننگ پراجیکٹ آرکیسٹریشن — ایجنٹ کنٹیکسٹ فائلوں (`AGENTS.md`) کے ساتھ سنکرونائزڈ بیک لاگ، کورس میٹریل پائپ لائن (ایس پی جی→ایس پی ڈی→سلائیڈز→پی ڈی ایف→فارم→ڈیش بورڈ)۔ |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | ای سی ڈی ایک→ایم پی 4 ہائپر فریم (ہی جین، ایپچی 2.0) کے ذریعے، نوڈ جی ایس برج۔ |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | ایل ایل ایم ایپی کی پول نقل کے ساتھ (راؤنڈ روبن، لیسٹ-یوزڈ، وزڈ)، کوٹا ٹریکنگ، آڈٹ لاگنگ۔ |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | ای سی ڈی ایکٹر جی کے ذریعے ایس کی ڈیکا ملٹی فارمیٹ (ایم ایل/پی ڈی ایف/اے پی یو بی/ڈیک بک/مانپیج) پر ہے فرکٹی + اے آئی--assisted جنریشن (لکھیں + شائع)۔ |

### آرکیسٹریٹر — ڈیپلوئمنٹ (N3)

| پلگ ان | رول |
|---|---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | ڈی ای آر ایس آرکیسٹریشن، پرموشن سی ایل آئی، ڈیپلوی گی پیجز۔ برہان کنجرمر، زیرو بزنس لاجک۔ |

### کنٹرولر — ایگل اینڈ گورننس (N4)

| پلگ ان | رول |
|---|---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | اے آئی assisted ایگل آرکیسٹریشن: 7 ورکشاپس (ویژن→آرکی ٹیکچر)، بیک لاگ، سپرنٹس، ویلوسٹی، مائل اسٹونز۔ |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | گیتہاب ٹکٹ تخلیق اینڈ ٹریکنگ — بیک لاگ → ایشو، کیمبن بورڈ، کمیٹ↔ٹکٹ لنکنگ۔ |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | اے آئی-assisted کوڈ ریویو: پی آر تحلیل، کوالٹی اسکور، کوالٹی گیٹس، سیکریٹ ڈیٹیکشن۔ |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | آرکیسٹریشن مرج/کلوس/سی آئی: مرج کبھی گیٹس بہتر، خود کار طور پر بند ٹکٹ، سی آئی ٹریگر۔ |

### مخصوص ٹولنگ (N2)

| پلگ ان | رول |
|---|---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | جی ہسٹر پرسس اینس آرکیسٹریشن (کلین/جنریٹ/سنک) `__codebase__/` میں کوٹلن کوڈ ضائع کیے بغیر۔ |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | جی ہسٹر اے آئی اسسٹنٹ ریگ ایل ایل ایم کے ساتھ۔ |

### ویسٹیجز (غیر فعال پروجیکٹس)

| پلگ ان | اسٹیٹس |
|---|---|
| `com.cheroliv.magic-stick` | N2 — ایک ایکس باکس ٹو ایس ایل آئی ایس او بیلڈر (داک سائٹ، نہیں پلگ ان) |
| `com.cheroliv.newpipe` | N2 — یو ٹیub→ایم پی 3 ایکسٹریکٹر (چھوڑ دیا) |
| `com.cheroliv.notebook` | N2 — کولاب آbservability (صرف تصور) |
| `com.cheroliv.office-template` | N? — خالی ٹیمپلیٹ ( حذف کرنے کے لیے) |
---

## ماحول اور ورک سٹیشن

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

ایک گریڈل کوٹلن ڈی ایس ایل بُلڈ اسکرپٹ جو ایک بُوبل ایکس باکس ٹو ایس ایل آئی ایس او کی تخلیق کی آرکیسٹریشن کرتا ہے — بطور **لائیو یو ایس بی** اینڈ **انستالر**، تین استعمال کے پروفائلز کے لیے ضروری ٹولنگ سے لیس:

- **نومادک ورک سٹیشن** — میں بورا موبائل ماحول یو- ڈرائیو پر۔
- **ایف ٹی ہ ایل ٹیلیcomm ٹیکنیشن** — فیلڈ ٹولنگ تیار کار استعمال کے لیے۔
- **طالب علم/ترنی** — کسی بھی پیشگی انسٹالیشن کی ضرورت کے بغیر فوری آن بورڈنگ۔

اس پروجیکٹ سے生态系统 کے فلسفے کی نمائش کی جاتی ہے: ورک ماحول خود بھی ایک **قابل دوبارہ تخلیق، ورژن، اور دستاویزات** آرٹی فیکٹس ہے۔ پروجیکٹ کی دستاویزات [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) پر جنریٹ اور شائع ہوتی ہے [cccp.education/magic-stick](https://cccp.education/magic-stick/) پر — ثابت کرنے والی کہ
شائع کرنے کی پائپ لائن پیداوار میں چلتی ہے۔
---

## کور اسٹاک

جاوا · کوٹلن · گریڈل (کوٹلن ڈی ایس ایل) · جی یونٹ 5 · کرکبر · سپرنگ بُوٹ · ای سی ڈی ایک · جی بیک · ریویل.جی ایس · پلینٹیول · جی گیٹ · جیکسن · lan چین4ج · koog · ڈوکر · پوسٹگری آ ایل/پی جی ویکٹر · گیتہاب ایکشنز · ایکس باکس/ڈیبین پیکیجنگ۔
---

## لنکس

- ویب سائٹ: [cheroliv.com](https://cheroliv.com)
- شائع کردہ پلگ انز: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [دستاویزات](https://cccp.education/magic-stick/) · [ریپوزٹری](https://github.com/cccp-education/magic-stick)
---

