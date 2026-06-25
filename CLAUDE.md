# CLAUDE.md

This file provides guidance to Claude Code when working with this repository.

## About this repository

This is a **book project** (replace with your book's description). The manuscript is written in **{{LANGUAGE}}** and covers **{{TOPIC}}**.

## Repository structure

- `chapters/chapter-NN.md` — individual chapter files in pt-BR (zero-padded, e.g., `chapter-01.md`). **Source of truth.**
- `chapters-en/chapter-NN.md` — English translation of each chapter (same naming convention).
- `book.md` / `book-en.md` — generated artifacts. Rebuilt by `scripts/generate-book.sh`. Do not edit directly.
- `scripts/` — build scripts (generate-book, build-pdf, build-epub, build-docx, split-chapters).
- `kdp-metadata.yaml` / `kdp-metadata-en.yaml` — Amazon KDP publishing metadata.
- `kdp-pdf.yaml` / `kdp-pdf-en.yaml` — PDF layout config (fonts, page geometry, LaTeX extras).
- `kdp-epub.yaml` / `kdp-epub-en.yaml` — EPUB layout config.
- `dist/` — generated output (book.pdf, book.epub, book.docx). Rebuilt by `make pdf` / `make epub` / `make docx`.
- `cover.jpg` / `cover-en.jpg` — cover images (optional; used for EPUB).

## Build scripts

```bash
# Rebuild book.md from all pt-BR chapter files
./scripts/generate-book.sh

# Rebuild book-en.md from all English chapter files
./scripts/generate-book.sh en

# Split book.md back into chapter files (migration only)
./scripts/split-chapters.sh
```

## PDF, EPUB, and DOCX builds

Requires `pandoc` and `xelatex` (TeX Live / MacTeX). Output lands in `dist/`.

```bash
make pdf          # → dist/book.pdf
make epub         # → dist/book.epub
make docx         # → dist/book.docx

make pdf BOOK_LANG=en    # → dist/book-en.pdf
make epub BOOK_LANG=en   # → dist/book-en.epub
make docx BOOK_LANG=en   # → dist/book-en.docx

make all          # pdf + epub (pt-BR)
make clean        # rm -rf dist
```

Layout parameters live in `kdp-pdf.yaml` (page size, margins, fonts, LaTeX header). Edit these only when changing publication layout, not for prose changes.

## Working with the manuscript

### Editing rules

- **Source of truth is `chapters/`.** Edit individual `chapter-NN.md` files. Run `./scripts/generate-book.sh` after editing if the generated file needs to be refreshed.
- **Markdown conventions:**
  - `#` for the book title
  - `##` for chapters
  - `###` for top-level sections inside a chapter
  - `####` for sub-sections
  - Em-dash `—` for parenthetical asides
  - En-dash `–` for ranges

### How to add a new chapter

1. Create `chapters/chapter-NN.md` (e.g., `chapter-03.md`). Begin with `## Capítulo N — Título`.
2. Run `./scripts/generate-book.sh` to rebuild `book.md`.
3. To add the English translation, create the equivalent in `chapters-en/chapter-NN.md`.

## Placeholders to replace before using this template

Search for `{{` in all files and replace:

| Placeholder | Description |
|---|---|
| `{{BOOK_TITLE}}` | Portuguese title |
| `{{BOOK_TITLE_EN}}` | English title |
| `{{BOOK_SUBTITLE}}` | Portuguese subtitle |
| `{{BOOK_SUBTITLE_EN}}` | English subtitle |
| `{{AUTHOR_NAME}}` | Author full name |
| `{{YEAR}}` | Publication year |
| `{{LANGUAGE}}` | Primary language of the manuscript |
| `{{TOPIC}}` | Book topic (one line) |
| `{{CHAPTER_TITLE}}` | Replace in chapter skeleton files |
