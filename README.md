# Arabic Scholar MCP Server

[![MCP](https://img.shields.io/badge/MCP-Compatible-blue)](https://modelcontextprotocol.io/)
[![Arabic](https://img.shields.io/badge/Language-Arabic-green)](https://search.mandumah.com)
[![Firecrawl](https://img.shields.io/badge/Powered%20by-Firecrawl-orange)](https://firecrawl.dev)

**By [Eng. Dawood Saleh](https://x.com/dawo5d)**

MCP server for searching Arabic academic research, articles, and dissertations from multiple sources including Mandumah (4M+ records), ASJP, SHAMAA, and other open-access repositories.

خادم MCP للبحث في الأبحاث والمقالات الأكاديمية العربية من مصادر متعددة: المنظومة (أكثر من 4 مليون سجل)، منصة ASJP، شمعة، ومستودعات الوصول الحر الأخرى.

## Table of Contents

- [Arabic Scholar MCP Server](#arabic-scholar-mcp-server)
  - [Table of Contents](#table-of-contents)
  - [Quick Start](#quick-start)
  - [Installation](#installation)
    - [Claude.ai (Web)](#claudeai-web)
    - [Claude Desktop](#claude-desktop)
    - [Claude Code CLI](#claude-code-cli)
    - [Other MCP Clients](#other-mcp-clients)
  - [Tools](#tools)
  - [Examples](#examples)
    - [بحث بسيط](#بحث-بسيط)
    - [بحث مع فلاتر](#بحث-مع-فلاتر)
    - [تفاصيل بحث معين](#تفاصيل-بحث-معين)
    - [اقتباس أكاديمي](#اقتباس-أكاديمي)
    - [مراجعة أدبية](#مراجعة-أدبية)
    - [البحث عن PDF مجاني 🆕](#البحث-عن-pdf-مجاني-)
  - [Search Parameters](#search-parameters)
    - [Content Types](#content-types)
  - [Limitations](#limitations)
  - [FAQ](#faq)
  - [Troubleshooting](#troubleshooting)
  - [Links](#links)

## Quick Start

**متطلبات:** حساب Claude Pro/Max/Team + مفتاح Firecrawl مجاني

1. احصل على مفتاح Firecrawl من [firecrawl.dev/app/api-keys](https://www.firecrawl.dev/app/api-keys)

2. في Claude.ai: **Settings** → **Connectors** → **Add custom connector**

3. أضف الرابط (استبدل `YOUR-KEY`):
   ```
   https://arabic-scholar-mcp.engdawood.workers.dev/mcp?api_key=fc-YOUR-KEY
   ```

4. **(اختياري)** لتفعيل البحث عن PDF مجاني، أضف مفتاح Exa من [exa.ai](https://exa.ai):
   ```
   https://arabic-scholar-mcp.engdawood.workers.dev/mcp?api_key=fc-YOUR-KEY&exa_api_key=YOUR-EXA-KEY
   ```

جاهز! جرب: *"ابحث في المنظومة عن الذكاء الاصطناعي في التعليم"*

---

## Installation

### Claude.ai (Web)

الطريقة الموضحة في Quick Start أعلاه.

### Claude Desktop

أضف في ملف `claude_desktop_config.json`:

**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "arabic-scholar": {
      "command": "npx",
      "args": [
        "mcp-remote",
        "https://arabic-scholar-mcp.engdawood.workers.dev/mcp?api_key=fc-YOUR-KEY&exa_api_key=YOUR-EXA-KEY"
      ]
    }
  }
}
```

### Claude Code CLI

أضف في ملف `.mcp.json`:

```json
{
  "mcpServers": {
    "arabic-scholar": {
      "type": "http",
      "url": "https://arabic-scholar-mcp.engdawood.workers.dev/mcp",
      "env": {
        "Firecrawl-API-Key": "fc-YOUR-KEY",
        "Exa-API-Key": "YOUR-EXA-KEY"
      }
    }
  }
}
```

### Other MCP Clients

```
https://arabic-scholar-mcp.engdawood.workers.dev/mcp?api_key=fc-YOUR-KEY&exa_api_key=YOUR-EXA-KEY
```

---

## Tools

| Tool | الوصف |
|------|-------|
| `mandumah_search` | البحث في الأبحاث الأكاديمية العربية مع فلاتر متعددة |
| `mandumah_get_record` | عرض تفاصيل سجل معين (ملخص، مؤلفين، كلمات مفتاحية) |
| `mandumah_get_citation` | الحصول على اقتباس أكاديمي بصيغة APA أو MLA |
| `mandumah_list_filters` | عرض خيارات الفلاتر المتاحة (نوع المحتوى، اللغة، إلخ) |
| `find_paper_pdf` | 🆕 البحث عن نسخ PDF مجانية في ASJP، SHAMAA، ResearchGate، Google Scholar وغيرها |

---

## Examples

> **ملاحظة:** اذكر "Arabic Scholar" أو "mandumah" في طلبك لضمان استخدام الأداة.

### بحث بسيط

```
ابحث في Arabic Scholar عن التعليم الإلكتروني
```

### بحث مع فلاتر

```
ابحث عن رسائل دكتوراه عربية في الذكاء الاصطناعي من 2020 إلى 2024
```

### تفاصيل بحث معين

```
أعطني تفاصيل السجل رقم 1048275
```

### اقتباس أكاديمي

```
اجلب لي اقتباس APA للبحث رقم 1048275
```

### مراجعة أدبية

```
ابحث عن أحدث 10 أبحاث محكّمة عن التعلم العميق بالعربية، ثم لخص لي توجهاتها
```

### البحث عن PDF مجاني 🆕

```
ابحث عن PDF مجاني لبحث "تطبيقات الذكاء الاصطناعي في المكتبات"
```

> يبحث في مستودعات متعددة: ASJP، SHAMAA، Al Manhal، ResearchGate، Academia.edu، Google Scholar

---

## Search Parameters

| Parameter | الوصف | مثال |
|-----------|-------|------|
| `query` | كلمات البحث | `"الذكاء الاصطناعي"` |
| `content_types` | نوع المحتوى | `["articles", "dissertations"]` |
| `languages` | اللغة | `["Arabic", "English"]` |
| `date_from` / `date_to` | نطاق السنوات | `"2020"` / `"2024"` |
| `peer_reviewed` | محكّم فقط | `true` |
| `sort` | الترتيب | `"year_desc"` |

### Content Types

| English | العربية |
|---------|---------|
| articles | بحوث ومقالات |
| dissertations | رسائل جامعية |
| conference_papers | بحوث المؤتمرات |
| book_reviews | عروض كتب |

---

## Limitations

الأداة توفر معلومات ببليوغرافية شاملة (metadata) للأبحاث الأكاديمية:

| متاح ✅ | غير متاح ❌ |
|------|----------|
| العنوان (عربي/إنجليزي) | النص الكامل للأبحاث |
| أسماء المؤلفين | ملفات PDF (إلا عبر أداة find_paper_pdf) |
| الملخص/المستخلص | |
| الكلمات المفتاحية | |
| معلومات النشر (مجلة، سنة، مجلد، عدد) | |
| البحوث المشابهة | |

**للوصول للنص الكامل:**
- استخدم أداة `find_paper_pdf` للبحث عن نسخ مجانية
- أو احصل على اشتراك في [منصة المنظومة](https://mandumah.com) للوصول الكامل

---

## FAQ

**كيف أحصل على مفتاح Firecrawl؟**
> سجّل مجاناً في [firecrawl.dev/app/api-keys](https://www.firecrawl.dev/app/api-keys) - تحصل على 500 طلب شهرياً.

**ما هو مفتاح Exa ولماذا أحتاجه؟**
> مفتاح Exa مطلوب فقط لأداة `find_paper_pdf` للبحث عن PDF مجاني. احصل عليه من [exa.ai](https://exa.ai). باقي الأدوات تعمل بدونه.

**هل أحتاج اشتراك لاستخدام الأداة؟**
> لا، الأداة توفر معلومات ببليوغرافية شاملة مجاناً. للنص الكامل، استخدم أداة `find_paper_pdf` أو احصل على اشتراك.

**لماذا لازم أذكر اسم الأداة؟**
> Claude يحتاج يعرف أي أداة يستخدم. اذكر "Arabic Scholar" أو "mandumah" في طلبك.

**كم عدد النتائج في كل بحث؟**
> 20 نتيجة لكل صفحة. استخدم `page` للتنقل بين الصفحات.

**هل يدعم البحث بالإنجليزية؟**
> نعم، يدعم العربية والإنجليزية وعدة لغات أخرى.

---

## Troubleshooting

| المشكلة | الحل |
|---------|------|
| "Invalid API Key" | تأكد أن المفتاح يبدأ بـ `fc-` بدون مسافات |
| نتائج فارغة | جرب كلمات بحث أقصر أو فلاتر أقل |
| الأدوات لا تظهر (Desktop) | أعد تشغيل التطبيق وتأكد من صيغة JSON |

---

## Links

| | |
|---|---|
| المنظومة | [search.mandumah.com](https://search.mandumah.com) |
| مفتاح Firecrawl | [firecrawl.dev/app/api-keys](https://www.firecrawl.dev/app/api-keys) |
| مفتاح Exa (اختياري) | [exa.ai](https://exa.ai) |
| حالة الخادم | [Health Check](https://arabic-scholar-mcp.engdawood.workers.dev/health) |

---

**المطور:** [Eng. Dawood Saleh](https://x.com/dawo5d)
