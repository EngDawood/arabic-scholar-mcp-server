---
name: previous-studies
description: Draft the previous-studies section (الدراسات السابقة) or a literature review for a thesis or research proposal from real papers found with the Arabic Scholar tools. Use when the user asks for الدراسات السابقة, الإطار النظري, مراجعة الأدبيات, a literature review, or related work for a stated research topic.
---

# Previous studies (الدراسات السابقة)

Build the section from papers the tools returned, each one read at least at the abstract level, each one cited.

## Before you search

Get these from the user's message, and ask once for whatever is missing:

- The research title or topic, and its main variables.
- How many studies, and the split between Arabic and foreign ones (a common request is half and half).
- The period (often the last five or ten years).
- The citation style (APA 7 is the usual one in Arab universities).
- The order: newest to oldest, oldest to newest, or by theme.

## Steps

1. **Search.** Use `search_all` with `scope: "arabic"` for the Arabic studies and `scope: "international"` for the foreign ones, one call per main variable, in Arabic and in English. Follow the `find-papers` skill.
2. **Choose.** Keep the studies closest to the user's variables, population and country. Prefer peer-reviewed articles and theses with a record link. Drop duplicates.
3. **Read.** For each kept study get the abstract from its record (`get_paper_details`, `mandumah_get_record`). Read the full text (`read-paper` skill) when the abstract lacks the method or the sample.
4. **Write each study** as one paragraph in the user's language with the same parts in the same order: author and year, the aim, the method, the sample and where it was drawn, the instrument, the main findings.
5. **Add the commentary** (التعقيب على الدراسات السابقة): where the studies agree and differ in aim, method, sample and findings, and what the user's study adds.
6. **Add the reference list** with the `cite-sources` skill.

## Rules

- Use only studies a tool returned in this conversation. Never fill a gap with a study from memory.
- If you found fewer studies than asked for, deliver what you found and say how many are missing and which searches you ran.
- Write only what the record or the text supports. If the sample size or the instrument is not stated, write that it is not stated.
- Mark a study you read only at the abstract level.
- Write the section for the user to revise. Say so in one line at the end: the wording is a draft, and each study should be checked against its source before submission.
