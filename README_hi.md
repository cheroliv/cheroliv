# `cheroliv`

🇬🇧 [English](README.md) · 🇫🇷 [Français](README_fr.md) · 🇨🇳 [中文](README_zh.md) · 🇮🇳 **हिन्दी** · 🇪🇸 [Español](README_es.md) · 🇸🇦 [العربية](README_ar.md) · 🇧🇩 [বাংলা](README_bn.md) · 🇵🇹 [Português](README_pt.md) · 🇷🇺 [Русский](README_ru.md) · 🇵🇰 [اردو](README_ur.md)

**सॉफ्टवेयर आर्टिसन · ट्रेनर · ग्रेडल टूलिंग ऑथर**

मैं प्रोजेक्ट टूलिंग, एक्जीक्यूटेबल डॉक्यूमेंटेशन और शैक्षिक सामग्री उत्पादन के लिए ग्रेडल कोटलिन डएसएल प्लगइन का एक पारिस्थितिकी व्यवस्था डिज़ाइन करता हूँ।
मेरी कच्ची सामग्री: कोटलिन, ग्रेडल, एस्कीडोक, लैंगकैन4ज, कूग।
---

## पوزिशनिंग

मैं तीन क्षेत्रों के संगम पर काम करता हूँ:

- **सॉफ्टवेयर क्राफ्टसमैनशिप** — टीडीडी, बीडीडी कर्कबर, हेक्सागोनल आर्किटेक्चर, इडियोमैटिक कोटलिन।
- **डेवलपर टूलिंग** — पुनः उपयोग करने योग्य ग्रेडल प्लगइन, पर [Maven Central](https://plugins.gradle.org/search?term=education.cccp) पर `education.cccp` नेमस्पेस के अंतर्गत प्रकाशित।
- **एडटेक** — शैक्षिक सामग्री, उत्पन्न स्टैटिक साइट्स, ट्रेसेबल ट्रेनिंग सामग्री।

सबकी संगति एक सरल विश्वास से जुड़ी है: **एक विश्वसनीय डेवलपर/ट्रेनर अपने खुद के टूल बनाता है और उनका उपयोग करता है**। मैं वह नहीं बेचता जो मैं दैनिक उपयोग नहीं करता।
---

## आर्किटेक्चर आईडेंटिटी — 4 डोमेन, 3 एकाउंट्स

### ब्रांड्स का पृथक्करण

| डोमेन | भूमिका | सिग्नल |
|
---|
---|
---|
| `cheroliv.com` | व्यक्तिगत पहचान, ब्लॉग, लेख | कोड के पीछे इंसान, संपादकीय आवाज़, सामाजिक पूंजी |
| `talaria.school` | OF — योग्यता भित्ति वाला प्रशिक्षण संस्थान | संस्थागत विज्ञापन और प्रशिक्षण कैटलॉग |
| `edster.cloud` | SaaS — समर्पित क्लाउड इंफ्रास्ट्रक्चर | ग्राहक वर्कस्पेस प्रोविजनिंग (MVP1) |
| `cccp.education` | डोमेन (SaaS/वेब) | *Common Content Creator Proletarian* — संख्यात्मक पहचान और ओएसएस विज्ञापन |

### तकनीकी खातों का पृथक्करण

| खाता | प्लेटफार्म | भूमिका |
|
---|
---|
---|
| `cheroliv` | GitHub | कमिट्स, पीआर, इतिहास, सामाजिक पूंजी (अपरिवर्तित) |
| `cccp-education` | GitHub (संगठन) | प्लगइन रिपॉजिटरी होस्टिंग, उत्पाद ब्रांड |
| `cccp-education` | Maven Central | प्रकाशन हैंडल — https://central.sonatype.com/namespace/education.cccp |

### 3-परत आर्किटेक्चर

```
cheroliv (dev) ──commits──▶ github.com/cccp-education (repos) ──publish──▶ cccp-education (Gradle Portal)
                              Group ID: education.cccp
                              लाइसेंस: एपाचे 2.0
```

*नियम* : व्यव‌ाय स्वतंत्र है (एपाचे 2.0), केवल बैंकिंग लेनदेन (waiter-gradle) ही नहीं है।
कोड में कोई विचारधारा नहीं होती — ग्रुप आईडी, ऐसा होता है।
---

## मेथडोलॉजी

मैं हर प्लगइन के लिए जो चक्र का अनुसरण करता हूँ:

1. **बिजनेस लॉजिक प्रोटोटाइपिंग** रूट `build.gradle.kts` में, प्रासंगिक लॉग के साथ
   वास्तविक परिस्थितियों के तहत व्यवहार को सत्यापित करने के लिए।
2. **प्लगइन माइग्रेशन** एक बार जब डोमेन लॉजिक स्थिर हो जाए — विशेष मॉड्यूल में स्थानांतरित करना
   परीक्षण के साथ साबित कोड, JUnit 5 के साथ TDD का उपयोग करें।
3. **BDD के साथ कर्कबर** जब भी डोमेन की अनुमति हो, यूजर स्तर पर
   इरादे को दस्तावेज़ीकृत करने के लिए।
4. **प्रकाशन** Maven Central पर एक वर्शनयुक्त एपीआई कॉन्ट्रैक्ट के साथ।

यह एक दमदार तरीका नहीं है, लेकिन यह एक ऐसा तरीका है जो समय का परीक्षण पारित करता है।
---

## `education.cccp.*` इकोसिस्टम — 25 बॉरोह्स

प्लगइन N0→N4 (डैग N0→N4) में 4 परतों के बीच तीन भूमिकाओं के आसपास व्यवस्थित हैं।

### फाउंडेशन — रियूज़ेबल बिल्डिंग ब्लॉक (N0)

| प्लगइन | भूमिका |
|
---|
---|
| [`com.gradleup.nmcp.settings`](https://plugins.gradle.org/plugin/com.gradleup.nmcp.settings) | Maven Central प्रकाशन (nmcp) |
| [`education.cccp.agent-contracts`](https://github.com/cccp-education/workspace-bom) | एजेंट प्रोटोकॉल कॉन्ट्रैक्ट (शेयर्ड कर्नल) |
| [`education.cccp.codebase-contracts`](https://github.com/cccp-education/workspace-bom) | कोडबेस रैग कॉन्ट्रैक्ट (शेयर्ड कर्नल) |
| [`education.cccp.vibecoding-contracts`](https://github.com/cccp-education/workspace-bom) | वाइबेकोडिंग कॉन्ट्रैक्ट (शेयर्ड कर्नल) |
| [`education.cccp.llm-pool-contracts`](https://github.com/cccp-education/workspace-bom) | एलएलएम एपीआई पूल कॉन्ट्रैक्ट (शेयर्ड कर्नल) |
| [`education.cccp.pipeline-contracts`](https://github.com/cccp-education/workspace-bom) | पाइपलाइन कॉन्ट्रैक्ट (शेयर्ड कर्नल) |
| [`education.cccp.i18n-contracts`](https://github.com/cccp-education/workspace-bom) | अंतर्राष्ट्रीयकरण कॉन्ट्रैक्ट (शेयर्ड कर्नल) |

### स्कैनर — वर्कस्पेस ग्राफ एक्सट्रैक्शन (N0)

| प्लगइन | भूमिका |
|
---|
---|
| [`education.cccp.graphify`](https://github.com/cccp-education/graphify-gradle) | कार्यक्षेत्र से ज्ञान ग्राफ़ (नोड्स, एज़, समुदाय) → `graph.json` का एक्सट्रैक्शन |

### प्रोसेसर — रैग & डेटासेट (N1)

| प्लगइन | भूमिका |
|
---|
---|
| [`education.cccp.codebase`](https://github.com/cccp-education/codebase-gradle) | बिल्ड-इन डेवलपमेंट असिस्टेंट: प्रोजेक्ट पढ़ाई, pgvector रैग, लैंगकैन4ज कॉन्टेक्स्ट एनरिचमेंट, एस्कीडोक रिपोर्ट जेनरेशन, डेटासेट क्रिएशन। |

### कंज़ूमर — कंटेंट जेनरेशन (N2)

| प्लगइन | भूमिका |
|
---|
---|
| [`education.cccp.planner`](https://github.com/cccp-education/planner-gradle) | एलएलएम प्रॉम्प्टिंग एसपीजी/एसपीडी के लिए (deepseek-v4-pro) — प्लानिंग एक्सपर्ट इरादे को एपीआईसी → यूजर स्टोरीज → ग्रेडल टास्क में विघटित करता है। |
| [`education.cccp.codex`](https://github.com/cccp-education/codex-gradle) | एस्कीडोक्टर→पीडीएफ, स्लाइड, डॉक्यूमेंट पाइपलाइन (रीड + रैग)। |
| [`education.cccp.slider`](https://github.com/cccp-education/slider-gradle) | एस्कीडोक सोर्स से रिवील.जेएस प्रेजेंटेशन जनरेशन, एक अलग शाखा में पुश के साथ। |
| [`education.cccp.plantuml`](https://github.com/cccp-education/plantuml-gradle) | एलएलएम (LangChain4j, 7 प्रोवाइडर, रैग pgvector, केजी, पूल एपीआई की) के जरिए PlantUML सिंटैक्स वैलिडेशन और रेंडरिंग (पीएनजी/एसवीजी)। |
| [`education.cccp.readme`](https://github.com/cccp-education/readme-gradle) | एम्बेडेड PlantUML डायग्राम के साथ मल्टीलिंगual README जेनरेशन और गिटहब पेजेस पब्लिकेशन जेगिट के माध्यम से। |
| [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) | जेबेक स्टैटिक साइट एग्रीगेटिंग अन्य प्लगइन (डायग्राम, स्लाइड, पोस्ट) द्वारा उत्पन्न आर्टिफैक्ट। |
| [`education.cccp.capsule`](https://github.com/cccp-education/capsule-gradle) | वीडियो कैप्सूल कैप्चर (रिवील.java + प्लेवराइट + टीटीएस)। |
| [`education.cccp.training`](https://github.com/cccp-education/training-gradle) | ट्रेनिंग प्रोजेक्ट ऑर्केस्ट्रेशन — एजेंट कॉन्टेक्स्ट फाइल (`AGENTS.md`) के साथ सिंक्रनाइज़ बैकलॉग, कोर्स मटेरियल पाइपलाइन (एसपीजी→एसपीडी→स्लाइड→पीडीएफ→प्रपत्र→डैशबोर्ड)। |
| [`education.cccp.hyperframes`](https://github.com/cccp-education/hyperframes-gradle) | एस्कीडोक→एमपी4 हाइपरफ्रेम (हेयजन, एपाचे 2.0) के माध्यम से, नोडजेस ब्रिज। |
| [`education.cccp.api-key-pool`](https://github.com/cccp-education/api-key-pool-gradle) | एलएलएम एपीआई की पूल रोटेशन के साथ (राउंड-रोबिन, कम-उपयोग, वेटेड), कोटा ट्रैकिंग, ऑडिट लॉगिंग। |
| [`education.cccp.document`](https://github.com/cccp-education/document-gradle) | एस्कीडोक्टरज के माध्यम से एस्कीडोक मल्टी-फॉर्मैट (एचएमएल/पीडीएफ/ईपीयूबी/डॉकबुक/मैनपेज) पर हेरफेर करें + एआई-सहायक जेनरेशन (लिखें + पब्लिश)। |

### ऑर्केस्ट्रेटर — डिप्लॉयमेंट (N3)

| प्लगइन | भूमिका |
|
---|
---|
| [`education.cccp.runner`](https://github.com/cccp-education/runner-gradle) | डैग ऑर्केस्ट्रेशन, प्रोविजनिंग सीएलआई, डिप्लॉय घी-पेज। अंतिम उपभोक्ता, शून्य व्यावसायिक तर्क। |

### कंट्रोलर — एजाइल & गवर्नेंस (N4)

| प्लगइन | भूमिका |
|
---|
---|
| [`education.cccp.agile`](https://github.com/cccp-education/agile-gradle) | एआई असिस्टेड एजाइल ऑर्केस्ट्रेशन: 7 वर्कशॉप (विजन→आर्किटेक्चर), बैकलॉग, स्प्रिंट, वेलोसिटी, माइलस्टोन। |
| [`education.cccp.ticket`](https://github.com/cccp-education/ticket-gradle) | गिटहब टिकट बनाना और ट्रैकिंग — बैकलॉग → इशू, कानबन बोर्ड, कमिट↔टिकट लिंकिंग। |
| [`education.cccp.review`](https://github.com/cccp-education/review-gradle) | एआई असिस्टेड कोड समीक्षा: पीआर विश्लेषण, गुणवत्ता स्कोर, गुणवत्ता गेट, रहस्य का पता लगाना। |
| [`education.cccp.flow`](https://github.com/cccp-education/flow-gradle) | ऑर्केस्ट्रेशन merge/close/CI: गेट ठीक होने पर merge, स्वचालित बंद टिकट, सीआई ट्रिगर। |

### विशिष्ट टूलिंग (N2)

| प्लगइन | भूमिका |
|
---|
---|
| [`com.cheroliv.jhipster.persistence`](https://github.com/cccp-education/jhipster-gradle-plugins) | जेएचपीस्टर परसिस्टेंस ऑर्केस्ट्रेशन (clean/generate/sync) `__codebase__/` में कोटलिन कोड खोए बिना। |
| [`com.cheroliv.jhipster.assistant`](https://github.com/cccp-education/jhipster-gradle-plugins) | आरजीएलएलएम के साथ जेएचपीस्टर एआई असिस्टेंट। |

### वेस्टीज (अक्षम प्रोजेक्ट) |

| प्लगइन | स्थिति |
|
---|
---|
| `com.cheroliv.magic-stick` | N2 — जेक्सबक्टू आईएसओ बिल्डर (doc साइट, प्लगइन नहीं) |
| `com.cheroliv.newpipe` | N2 — YouTube→MP3 एक्सट्रैक्टर (त्यागा गया) |
| `com.cheroliv.notebook` | N2 — कोलब ऑब्जर्वेबिलिटी (केवल अवधारणा) |
| `com.cheroliv.office-template` | N? — खाली टेम्पलेट (हटाने के लिए) |
---

## वातावरण और कार्यस्थल

### [`magic-stick`](https://github.com/cccp-education/magic-stick)

एक ग्रेडल कोटलिन डीएसएल बिल्ड स्क्रिप्ट जो एक बूटेबल एक्सबंटू आईएसओ के निर्माण का संगठन करता है — एक **लाइव यूएसबी** और **इंस्टॉलर** के रूप में कार्य करता है जो तीन उपयोग प्रोफ़ाइल के लिए आवश्यक टूलिंग से लैस है:

- **नॉमैडिक कार्यस्थल** — मेरा कंपलेट पोर्टेबल वातावरण यू-डिस्क पर।
- **एफटीएच टेलीकॉम तकनीशियन** — फील्ड टूलिंग उपयोग के लिए तैयार।
- **छात्र/प्रशिक्षणार्थी** — कोई पूर्व-इंस्टॉलेशन की आवश्यकता के बिना तत्काल ऑनबोर्डिंग।

इस प्रोजेक्ट का उपयोग इकोसिस्टम के दर्शन को प्रदर्शित करता है: कार्य वातावरण स्वयं भी एक **पुनरुत्पादनयोग्य, संस्करणयोग्य, दस्तावेजीकृत** कलाकृति है। प्रोजेक्ट का दस्तावेजीकरण [`education.cccp.bakery`](https://github.com/cccp-education/bakery-gradle) द्वारा उत्पन्न और प्रकाशित होता है [cccp.education/magic-stick](https://cccp.education/magic-stick/) पर — साबित करता है कि प्रकाशन पाइपलाइन उत्पादन में चल रही है।
---

## कोर स्टैक

Java · Kotlin · Gradle (Kotlin DSL) · JUnit 5 · Cucumber · Spring Boot · AsciiDoc · JBake · Reveal.js · PlantUML · JGit · Jackson · LangChain4j · Koog · Docker · PostgreSQL/pgvector · GitHub Actions · Xubuntu/Debian packaging।
---

## लिंक

- वेबसाइट: [cheroliv.com](https://cheroliv.com)
- प्रकाशित प्लगइन: [Maven Central — education.cccp](https://central.sonatype.com/namespace/education.cccp)
- `magic-stick`: [दस्तावेज़ीकरण](https://cccp.education/magic-stick/) · [रिपॉजिटरी](https://github.com/cccp-education/magic-stick)
---


