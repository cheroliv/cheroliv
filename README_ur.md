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

## `education.cccp.*` اکوسسٹم — 29 بوروہس
[`cccp.education`](https://cccp.education/)


## کور اسٹاک

جاوا · کوٹلن · گریڈل (کوٹلن ڈی ایس ایل) · جی یونٹ 5 · کرکبر · سپرنگ بُوٹ · ای سی ڈی ایک · جی بیک · ریویل.جی ایس · پلینٹیول · جی گیٹ · جیکسن · lan چین4ج · koog · ڈوکر · پوسٹگری آ ایل/پی جی ویکٹر · گیتہاب ایکشنز · ایکس باکس/ڈیبین پیکیجنگ۔
---

## لنکس

- ویب سائٹ: [cheroliv.com](https://cheroliv.com)
- شائع کردہ پلگ انز: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [دستاویزات](https://cccp.education/magic-stick/) · [ریپوزٹری](https://github.com/cccp-education/magic-stick)
---

