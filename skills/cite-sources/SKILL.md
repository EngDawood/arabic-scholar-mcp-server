---
name: cite-sources
description: Format references and check that references are real with the Arabic Scholar tools. Use when the user asks to cite a paper, build a reference list or bibliography, convert between APA, MLA, Chicago, Harvard and BibTeX, or verify references, or says "وثّق", "توثيق المراجع", "قائمة المراجع", "تحقق من المرجع".
---

# Cite sources

A citation comes from the paper's record, never from memory.

## Format one paper

1. Get an identifier. A DOI or an arXiv id is best. For a paper on Dar Almandumah use its record id or record URL. With only a title, search (`search_all`) and confirm authors and year first.
2. Call `cite_paper` with `doi`, `arxiv_id` or `mandumah_id`, and the `styles` wanted: `apa`, `mla`, `chicago`, `harvard`, `bibtex`. For a Mandumah record `mandumah_get_citation` also works.
3. Give the citation exactly as returned. If the user's style has a rule the tool's output does not follow (for example APA 7 for Arabic names), fix that one point and say what you changed.

## Build a reference list

Run the steps above for each paper, then sort by the style's rule (APA: by first author's family name; Arabic references before or after the English ones, as the user's institution asks). List separately any item you could not find, with the reason.

## Verify references

For each reference the user gives:

1. Look it up: `get_paper_by_doi` if it has a DOI, otherwise search by title.
2. Compare title, authors, year and journal with the record.
3. Report one of: **found and matches**, **found with differences** (list them), **not found**.

"Not found" means the tools did not find it. It does not prove the reference is invented. Say that, and suggest checking the publisher's site or the library.

## Rules

- Never invent a DOI, a page range, a volume or an issue. Leave out what the record does not have.
- Do not change the spelling of an Arabic author's name to match another source.
