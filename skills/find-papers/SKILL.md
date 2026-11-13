---
name: find-papers
description: Find academic papers on a topic with the Arabic Scholar tools, in Arabic, English or both. Use when the user asks for studies, papers, research, references or sources on a subject, or says "ابحث عن دراسات", "أبحاث عن", "مراجع عن", "أوراق علمية".
---

# Find papers

Search with the Arabic Scholar connector and report only papers the tools returned.

## Steps

1. **Settle the query.** Take the topic, the years and the language from the request. If the user wrote in Arabic, search in Arabic and in English: translate the key terms, because most international sources index English only. Ask a question only when the topic itself is unclear.
2. **Pick the tool.**
   - Arabic and international together: `search_all` with `scope: "all"`.
   - Arabic scholarship only: `search_all` with `scope: "arabic"`, or `search_arabic_papers` when the user names a platform.
   - International only: `search_papers`.
   - One named source: its own tool, for example `search_pubmed` or `search_arxiv`. `list_sources` gives the ids.
   - Pass `year` as `"2020-"`, `"2019-2023"` or `"2023"` when the user gives a period.
3. **Search twice at most before you report.** If the first call returns little, change the wording: fewer words, a synonym, or the other language. Do not repeat the same call.
4. **Report.** Give a table or a list with title, authors, year, source and link, in the order the user asked for (default: newest first). Say how many sources answered and name any source the result marks as failed.
5. **Offer the next step** in one line: read one of them (`read-paper`), cite them (`cite-sources`), or follow the citations with `get_citing_papers`.

## Rules

- Never add a paper from memory. If the tools found nothing, say so and suggest a wider query.
- Keep each paper's title in its original language. Do not translate a title without saying it is your translation.
- A paper without a DOI or a link is still valid if a tool returned it; show the record link it came with.
- Arabic names and titles vary in spelling (أ/ا, ة/ه, ي/ى). Try the other spelling before you conclude a paper is missing.
