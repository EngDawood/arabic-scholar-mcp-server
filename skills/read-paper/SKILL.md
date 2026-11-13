---
name: read-paper
description: Get the full text of one academic paper with the Arabic Scholar tools and summarise or answer questions from it. Use when the user gives a DOI, a title, an arXiv id or a PDF link and asks to read, summarise, explain or extract something, or says "اقرأ البحث", "لخّص الدراسة", "ما منهج هذه الدراسة".
---

# Read a paper

Work from the paper's own text. A summary written from the abstract alone must say so.

## Steps

1. **Identify the paper.** With a DOI use `get_paper_by_doi`. With an arXiv id, a PMID or a DOI use `get_paper_details`. With only a title, search for it first (`search_all`) and confirm the match by authors and year before you go on.
2. **Find a readable copy.**
   - `find_open_access_pdf` for a DOI.
   - `find_pdf_anywhere` for a title or a page URL, and for Arabic papers.
   - `get_pdf_url` for a record page on an Arabic repository.
3. **Read it.** Call `read_paper` with the `pdf_url` (or the `doi`). The text comes in parts: when the result says more remains, call again with `offset` set to where the last part ended. Read the whole paper before you summarise methods or results.
4. **Answer.** For a summary give: the question, the method, the sample or data, the main findings, the limits the authors state. Mark page or section where you can.

## When there is no open copy

Say that no legal open-access copy was found, give the publisher or record link, and offer a summary from the abstract, labelled as such. Do not look for the paper on sites that share copies without permission.

## When the text is garbled

`read_paper` warns when an Arabic PDF is a scan or has broken text. Tell the user, quote nothing from the damaged parts, and work from the abstract and the readable pages.
