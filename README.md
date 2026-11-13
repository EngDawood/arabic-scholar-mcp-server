# الباحث العربي · Arabic Scholar

إضافة لـ Claude تبحث في الأوراق العلمية العربية والدولية وتقرؤها وتوثّقها. صُنعت لطلاب الدراسات العليا والباحثين الذين يعملون على الإنتاج العلمي العربي ويحتاجون الأدبيات الدولية إلى جانبه.

A Claude plugin that finds, reads and cites academic papers in Arabic and English. It is made for graduate students and researchers who work with Arabic scholarship and need the international literature beside it.

[English](#english) · [العربية](#العربية)

---

## العربية

### ما الذي تضيفه

- **موصّل الباحث العربي**: خادم MCP بعيد، كل أدواته للقراءة فقط. يبحث في المستودعات العربية (دار المنظومة، ASJP، شمعة، المكتبة الرقمية السعودية، بنك المعرفة المصري، ومجلات جامعية عربية) وفي 18 مصدراً دولياً مفتوحاً (arXiv وPubMed وCrossref وDOAJ وغيرها)، ويعثر على ملفات PDF مفتوحة الوصول، ويقرأ النص الكامل، ويوثّق المراجع.
- **أربع مهارات** تعلّم Claude استخدام هذه الأدوات كما يستخدمها باحث:

| المهارة | متى تُستخدم |
|---|---|
| `find-papers` | للبحث عن دراسات في موضوع، بالعربية أو الإنجليزية أو بهما معاً |
| `read-paper` | للحصول على النص الكامل لورقة واحدة وتلخيصها |
| `cite-sources` | لتوثيق المراجع بصيغ APA وMLA وChicago وHarvard وBibTeX، أو للتحقق من أن المرجع حقيقي |
| `previous-studies` | لكتابة مسودة «الدراسات السابقة» في رسالة أو خطة بحث من دراسات حقيقية |

### أمثلة

- ابحث عن دراسات عربية عن أثر التعلم الإلكتروني في التحصيل الدراسي بعد 2020 ورتّبها حسب السنة.
- اعثر على أحدث الأوراق مفتوحة الوصول في معالجة اللغة العربية، ثم اقرأ أفضل واحدة ولخّص منهجها.
- وثّق هذا البحث بصيغة APA 7: 10.1038/s41586-021-03819-2
- اكتب لي الدراسات السابقة لبحث عن القيادة التحويلية في المدارس السعودية من عشر دراسات حقيقية.

### ما تلتزم به المهارات

- لا تذكر دراسة من الذاكرة. كل دراسة في الإجابة أعادتها إحدى الأدوات في المحادثة نفسها.
- لا تخترع رقم DOI ولا صفحات ولا مجلداً. ما لا يذكره السجل يُترك.
- حين لا توجد نسخة مفتوحة من البحث تقول ذلك وتعطي رابط الناشر، ولا تبحث عنه في مواقع تنشر النسخ بلا إذن.
- ما تكتبه مسودة تراجعها أنت. تحقق من كل دراسة في مصدرها قبل التسليم.

### التثبيت

الإضافة في طريقها إلى دليل Claude. حتى تُدرج، حمّلها من هذا المستودع في Claude Code:

```bash
git clone https://github.com/EngDawood/arabic-scholar-mcp-server
```

```bash
claude --plugin-dir ./arabic-scholar-mcp-server
```

**الحالة: نسخة أولية.** عنوان الموصّل العام قيد الإعداد، وسيُحدَّث في ملف `.mcp.json` قبل الإدراج في الدليل. المهارات تعمل الآن مع أي موصّل يقدّم الأدوات نفسها.

### ما الذي تشغّله وترسله

الإضافة لا تشغّل أي برنامج على جهازك. لا hooks فيها ولا سكربتات، ومهاراتها تعليمات مكتوبة بصيغة Markdown.

الموصّل خادم بعيد. حين يطلب Claude إحدى أدواته تُرسل مدخلات الأداة فقط (مثل نص البحث أو رقم DOI أو رابط PDF) إلى خادم الباحث العربي، فيستعلم من المصادر الأكاديمية ويعيد النتائج. لا يُرسل شيء آخر من محادثتك أو ملفاتك.

لا تحتاج حساباً ولا مفتاحاً للبدء. للاستخدام المجاني حد يومي وحد في الدقيقة.

### الخصوصية والدعم

سياسة الخصوصية وشروط الاستخدام والدليل وجهة الدعم منشورة في موقع الباحث العربي بالعربية والإنجليزية (`/privacy` و`/terms` و`/docs` و`/support`). لطلب مصدر جديد أو للإبلاغ عن مشكلة في الإضافة افتح issue في هذا المستودع.

---

## English

### What the plugin adds

- **The Arabic Scholar connector.** A remote MCP server whose tools are all read-only. It searches Arabic repositories (Dar Almandumah, ASJP, SHAMAA, the Saudi Digital Library, the Egyptian Knowledge Bank, Arab university journals) and 18 open international sources (arXiv, PubMed, Crossref, DOAJ and others), finds open-access PDFs, reads full text and formats citations.
- **Four skills** that teach Claude to use those tools the way a researcher would:

| Skill | Use it when you want to |
|---|---|
| `find-papers` | Find papers on a topic in Arabic, English or both |
| `read-paper` | Get the full text of one paper and a summary of it |
| `cite-sources` | Format references in APA, MLA, Chicago, Harvard or BibTeX, or check that a reference is real |
| `previous-studies` | Draft the previous-studies (الدراسات السابقة) section of a thesis or proposal from real papers |

### Example prompts

- Find Arabic studies on the effect of e-learning on academic achievement since 2020, sorted by year.
- Find recent open-access papers on Arabic NLP, then read the best one and summarise its method.
- Cite this paper in APA 7: 10.1038/s41586-021-03819-2
- Write the previous-studies section for a study on transformational leadership in Saudi schools, from ten real studies.

### What the skills hold to

- No paper from memory. Every paper in an answer was returned by a tool in the same conversation.
- No invented DOI, page range or volume. What the record lacks is left out.
- When a paper has no open copy, the skill says so and gives the publisher link. It does not look on sites that share copies without permission.
- The output is a draft for you to revise. Check each study against its source before you submit.

### Install

The plugin is on its way to the Claude directory. Until it is listed, load it from this repository in Claude Code:

```bash
git clone https://github.com/EngDawood/arabic-scholar-mcp-server
```

```bash
claude --plugin-dir ./arabic-scholar-mcp-server
```

**Status: preview.** The public connector address is being set up and will be updated in `.mcp.json` before the directory listing. The skills work now with any connector that offers the same tools.

### What it runs and sends

The plugin runs no code on your computer. It has no hooks and no scripts. Its skills are Markdown instructions.

The connector is a remote server. When Claude calls one of its tools, only the tool's inputs (for example your search text, a DOI or a PDF link) are sent to the Arabic Scholar server, which queries the academic sources and returns the results. Nothing else from your conversation or your files is sent.

You need no account or key to start. Free use has a daily limit and a per-minute limit.

### Privacy and support

The privacy policy, terms of use, documentation and support contact are on the Arabic Scholar website, in Arabic and in English (`/privacy`, `/terms`, `/docs` and `/support`). To ask for a new source or report a problem with the plugin, open an issue in this repository.

## License

MIT. See `LICENSE`.
