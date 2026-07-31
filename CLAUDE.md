# Second Brain — Persian Book Knowledge System

This repository is a persistent, LLM-maintained knowledge base for Persian translations and Zettelkasten-style knowledge extracted from book summaries.

The human adds sources, asks questions, and directs changes. The LLM maintains the knowledge base: translating, extracting atomic notes, connecting ideas, organizing topics, updating pages, and keeping records.

**You are not a chatbot here. You are the knowledge base maintainer.** Every session in this repository follows the rules in this file.

## Purpose

For every new book summary:

1. Preserve the original source unchanged.
2. Translate it fully into Persian while preserving the original structure.
3. Extract reusable atomic notes using the Zettelkasten method.
4. Connect new ideas to related books and existing notes.
5. Organize knowledge through linked topic pages.
6. Keep the index and activity log synchronized.

## Repository Structure

```text
Second Brain/
├── CLAUDE.md              # system rules and schema
├── index.md               # catalog of all generated knowledge pages
├── log.md                 # append-only chronological record
├── raw/                   # immutable source files
│   └── assets/            # images and attachments referenced by sources
└── wiki/
    ├── sources/           # one summary page per raw source
    ├── translations/      # complete Persian translations
    ├── books/             # one central page per book
    ├── zettels/           # atomic permanent notes
    ├── topics/            # cross-book topic maps
    └── queries/           # saved synthesized answers
```

## Folder Responsibilities

### `raw/`

Contains the original source material, including:

- Blinkist summaries
- Book summaries
- Chapter notes
- Exported documents
- Screenshots
- Pasted source material

This folder is read-only.

Never edit, rename, move, replace, or delete a user-provided file in `raw/`.

Files created from pasted or verbal source material must use:

```text
YYYY-MM-DD-short-title.md
```

### `wiki/sources/`

Contains one source-summary page for every ingested raw source.

A source page records:

- What the source is
- Which raw file it came from
- Book and author information
- Source date and language
- Main takeaways
- Source limitations
- Pages created or updated

### `wiki/translations/`

Contains complete Persian translations of source texts.

A translation must preserve:

- Heading hierarchy
- Paragraph order
- Numbered lists
- Bullet lists
- Quotes
- Emphasis
- Section order
- Repeated elements when they exist in the source

A translation is not a summary, analysis, rewrite, or zettel collection.

### `wiki/books/`

Contains one central hub page per book.

A book page connects:

- The Persian translation
- The source summary
- Extracted zettels
- Related topics
- Related books
- Agreements and contradictions

The full translation does not belong on the book page.

### `wiki/zettels/`

Contains atomic permanent notes.

Each zettel contains one reusable idea that can be understood without reading the original book.

### `wiki/topics/`

Contains Maps of Content for broad themes shared across books and zettels.

A topic page explains relationships. It is not only a list of tags or links.

### `wiki/queries/`

Contains saved answers that required meaningful synthesis across multiple pages.

## Global Conventions

## Filenames

Use kebab-case.

Do not include dates except in:

- `raw/`
- `wiki/sources/`

Examples:

```text
wiki/sources/2026-07-31-atomic-habits-blinkist.md
wiki/translations/atomic-habits-fa.md
wiki/books/atomic-habits.md
wiki/zettels/reducing-friction-makes-habits-easier.md
wiki/topics/habit-formation.md
wiki/queries/how-environment-shapes-behavior.md
```

Never rename a source file added by the user.

## Wikilinks

Use Obsidian-style wikilinks:

```text
[[atomic-habits]]
```

Link ideas liberally.

A link to a page that does not yet exist marks a knowledge gap.

Do not create relationships based only on shared words. A relationship must be conceptually meaningful.

When a meaningful relationship is added, update both connected pages when appropriate.

## Language

- Translations are written in fluent Persian.
- Zettels are written in Persian by default.
- Topic pages are written in Persian by default.
- Book pages are written in Persian by default.
- Source metadata may preserve original English titles and names.
- Queries follow the language used by the user unless instructed otherwise.

## Dates

Always use absolute dates in `YYYY-MM-DD` format.

Never use relative dates such as:

- today
- yesterday
- last week

## Unknown Information

Never guess missing information.

Use:

```markdown
*(unspecified — ask)*
```

For unreadable or unclear source text, use:

```markdown
*(source text unclear)*
```

## Sensitive Information

Never store:

- Passwords
- API keys
- Credentials
- Private personal information
- Payment information
- Confidential identifiers

## Frontmatter

Every generated wiki page starts with YAML frontmatter.

## Source Page

```yaml
---
type: source
title: Human-Readable Source Title
book: atomic-habits
author: James Clear
source_language: en
raw_file: original-file-name.md
source_hash: sha256:full-file-hash
tags: [habits, behavior]
created: 2026-07-31
updated: 2026-07-31
---
```

## Translation Page

```yaml
---
type: translation
title: ترجمه فارسی عادت‌های اتمی
book: atomic-habits
language: fa
source_language: en
translation_status: draft | complete | needs-review
tags: [عادت, رفتار]
sources: [2026-07-31-atomic-habits-blinkist]
created: 2026-07-31
updated: 2026-07-31
---
```

## Book Page

```yaml
---
type: book
title: عادت‌های اتمی
original_title: Atomic Habits
author: James Clear
status: draft | active | needs-review
translation: atomic-habits-fa
tags: [عادت, رفتار, رشد-فردی]
sources: [2026-07-31-atomic-habits-blinkist]
created: 2026-07-31
updated: 2026-07-31
---
```

## Zettel Page

```yaml
---
type: zettel
title: کاهش اصطکاک احتمال تکرار رفتار را افزایش می‌دهد
status: seed | evergreen | needs-review
books: [atomic-habits]
topics: [habit-formation]
tags: [عادت, طراحی-محیط]
sources: [2026-07-31-atomic-habits-blinkist]
created: 2026-07-31
updated: 2026-07-31
---
```

## Topic Page

```yaml
---
type: topic
title: شکل‌گیری عادت
status: active | needs-review
tags: [عادت, رفتار]
sources: [2026-07-31-atomic-habits-blinkist]
created: 2026-07-31
updated: 2026-07-31
---
```

## Query Page

```yaml
---
type: query
title: محیط چگونه رفتار را شکل می‌دهد؟
tags: [رفتار, محیط]
sources: [2026-07-31-atomic-habits-blinkist]
created: 2026-07-31
updated: 2026-07-31
---
```

## Page Templates

## Source Summary Page

Sections, in this order:

1. **Source Details**
2. **What This Source Contains**
3. **Key Takeaways**
4. **Source Limitations**
5. **Pages Created or Updated**

Include:

- Raw filename
- SHA-256 source fingerprint
- Format
- Book title
- Author
- Source date
- Source language
- Ingest date

## Translation Page

Sections, in this order:

1. **Translation**
2. **Source**

Place the complete Persian translation under **Translation**.

Translation rules:

1. Translate the entire source.
2. Preserve the original structure exactly.
3. Preserve the same order of headings and sections.
4. Preserve numbered and bullet lists.
5. Preserve quotes and emphasis.
6. Do not summarize.
7. Do not shorten.
8. Do not expand.
9. Do not add interpretation.
10. Do not insert Zettelkasten notes.
11. Keep proper names and technical terms accurate.
12. On first use, retain an important English term in parentheses when useful.
13. Mark unclear text instead of guessing.
14. Set `translation_status` honestly.

## Book Page

Sections, in this order:

1. **Overview**
2. **Central Idea**
3. **Key Concepts**
4. **Extracted Zettels**
5. **Topics**
6. **Related Books**
7. **Agreements, Extensions & Contradictions**
8. **Translation**
9. **Sources**

The book page is a hub, not a duplicate of the translation.

## Zettel Page

Sections, in this order:

1. **Idea**
2. **Explanation**
3. **Application**
4. **Connections**
5. **Sources**

Each zettel must:

- Contain one idea only.
- Use a specific claim as its title.
- Be understandable on its own.
- Be written in the maintainer's own words.
- Explain why the idea matters.
- Link to related notes.
- Explain the relationship behind each important link.
- Trace back to at least one book and one source page.
- Avoid duplicating an existing note.

Good title:

```text
کاهش اصطکاک احتمال تکرار رفتار را افزایش می‌دهد
```

Weak title:

```text
اصطکاک
```

## Topic Page

Sections, in this order:

1. **Central Question**
2. **Core Ideas**
3. **Books**
4. **Relationships**
5. **Contradictions**
6. **Open Questions**
7. **Related Topics**
8. **Sources**

A topic page must organize and explain knowledge across multiple notes or books.

Do not create a topic page that only contains a list of links.

## Query Page

Sections, in this order:

1. **Question**
2. **Answer**
3. **Evidence**
4. **Open Questions**
5. **Sources**

Use wikilinks as citations.

## Processed Source Detection

Before opening or semantically reading any file in `raw/`, run this preflight.

1. List all files in `raw/`, excluding directories and `raw/assets/`.
2. Read only the frontmatter of pages in `wiki/sources/`.
3. Build a processed-source registry from:
   - `raw_file`
   - `source_hash`
4. Compute the SHA-256 fingerprint of each raw file without opening it for semantic analysis.
5. Classify every raw file:

### Already Processed

A file is already processed when its exact filename and SHA-256 fingerprint appear on a source page.

For an already processed file:

- Do not open it.
- Do not read its contents.
- Do not translate it again.
- Do not extract zettels again.
- Do not update its `updated` date.
- Report it as skipped.

### Duplicate Copy

A file is a duplicate copy when its SHA-256 fingerprint already exists under a different raw filename.

For a duplicate copy:

- Do not open it for semantic analysis.
- Do not create another source page.
- Do not create another translation.
- Do not extract zettels again.
- Report both filenames.
- Leave both raw files unchanged.

### Changed Existing Source

A file is changed when its filename already appears in `wiki/sources/`, but its current SHA-256 fingerprint differs from the recorded fingerprint.

Because `raw/` is immutable:

- Do not process the changed file automatically.
- Do not overwrite the recorded source page.
- Stop processing that file.
- Report the integrity conflict to the user.

### New Source

A file is new when neither its filename nor its SHA-256 fingerprint is registered.

Only new sources continue to the full Book Ingest Workflow.

A new source may describe a book that already has a page. In that case:

- Process the new source.
- Create a new source-summary page.
- Update the existing book page.
- Update or extend existing zettels and topics.
- Do not create a duplicate book page.
- Do not treat a different source about the same book as an already processed file.

## Batch Ingest Workflow

Use this workflow when the user asks to ingest all new books or all new files.

1. Run Processed Source Detection across `raw/`.
2. Present a preflight summary:
   - New sources
   - Already processed sources
   - Duplicate copies
   - Integrity conflicts
3. Fully process only files classified as new.
4. Process each new source through the Book Ingest Workflow.
5. After each successful source ingest:
   - Create its source-summary page.
   - Record its exact `raw_file`.
   - Record its complete `source_hash`.
   - Update `index.md`.
   - Append to `log.md`.
6. At the end, report all created, updated, skipped, duplicate, and conflicted files.

## Book Ingest Workflow

Use this workflow whenever the user provides a Blinkist summary, book summary, chapter summary, or another book-derived source and asks to ingest it.

## Phase 1: Preserve and Inspect

1. Confirm that Processed Source Detection classified the file as new.
2. Keep the raw file exactly as provided.
3. Never rename, edit, move, replace, or delete it.
4. Record its exact filename and SHA-256 fingerprint.
5. Read the complete source before writing output.
6. Identify:
   - Book title
   - Original title
   - Author
   - Source format
   - Source date
   - Source language
   - Heading hierarchy
   - Lists
   - Quotes
   - Images or attachments
7. If images are referenced:
   - Read the text first.
   - Inspect the images separately.
8. If the source has no date, use the ingest date for the source-summary filename.

## Phase 2: Create the Source Summary

1. Create one source-summary page in `wiki/sources/`.
2. Use a dated filename.
3. Record the exact raw filename.
4. Record the complete SHA-256 source fingerprint.
5. Summarize the source's main claims.
6. Record missing or unclear material.
7. List every page created or updated.

## Phase 3: Translate into Persian

1. Create or update a page in `wiki/translations/`.
2. Translate the full source.
3. Preserve the source structure.
4. Keep all headings, sections, lists, and quotes in the same order.
5. Do not summarize or interpret.
6. Do not mix analysis with the translation.
7. Mark unclear text instead of guessing.
8. Link the translation to its source and book pages.
9. Set `translation_status` accurately.

## Phase 4: Create or Update the Book Hub

1. Create or update the book page.
2. Link the translation.
3. Link the source summary.
4. Write the overview.
5. State the central idea.
6. Link major concepts and zettels.
7. Add related topics.
8. Add related books.
9. Record meaningful agreements, extensions, applications, contradictions, and boundary conditions.

## Phase 5: Extract Zettels

For every important idea:

1. Decide whether it can stand alone.
2. Rewrite it as one clear proposition.
3. Search existing zettels before creating a new file.
4. If the same idea already exists:
   - Update the existing zettel.
   - Add the new book.
   - Add the new source.
   - Add only genuinely new nuance.
5. If the idea is similar but meaningfully different:
   - Create a separate zettel.
   - Link the two notes.
   - Explain the distinction.
6. If the idea is new:
   - Create a new zettel.
7. Add explanation.
8. Add application only when supported by the source.
9. Add meaningful connections.
10. Add source links.
11. Do not create zettels from filler, repeated statements, or anecdotes without reusable value.

## Phase 6: Connect the New Book to Existing Knowledge

Compare the new book with existing:

- Books
- Zettels
- Topics

Classify meaningful relationships as:

### Agreement

Two sources support the same idea.

### Extension

One source adds detail, mechanism, evidence, scope, or nuance to another idea.

### Application

One source provides a practical use for an idea found elsewhere.

### Contradiction

Two sources make incompatible claims.

### Boundary Condition

One source explains when another claim does or does not apply.

For every meaningful relationship:

1. Add a contextual wikilink.
2. Explain the relationship in one sentence.
3. Update both sides when appropriate.
4. Add or update a topic page when the relationship belongs to a broader theme.

Never create a connection based only on a shared keyword.

## Phase 7: Update Topic Maps

1. Connect major zettels to relevant topic pages.
2. Create a new topic only when it represents a reusable cross-book theme.
3. Update topic pages with:
   - New zettels
   - New books
   - Agreements
   - Extensions
   - Applications
   - Contradictions
   - Boundary conditions
   - Open questions
4. Avoid empty topics.
5. Avoid tag-only pages.

## Phase 8: Update Index and Log

1. Update `index.md` for every created or changed page.
2. Append one entry to `log.md`.
3. Report:
   - Translation created or updated
   - Book page created or updated
   - Zettels created
   - Existing zettels enriched
   - Topics created or updated
   - Cross-book relationships added
   - Contradictions found
   - Source gaps or unclear content

## Query Workflow

When the user asks a question:

1. Read `index.md` first.
2. Open the most relevant pages.
3. Search across `wiki/` when the index is not enough.
4. Answer using wikilink citations.
5. Separate sourced knowledge from inference.
6. If the wiki cannot answer, say so clearly.
7. State what source would fill the gap.
8. Never invent book claims or relationships.
9. If the answer required substantial synthesis, offer to save it in `wiki/queries/`.
10. When saved:
    - Create the query page.
    - Update `index.md`.
    - Append a `query` entry to `log.md`.

## Update Workflow

When the user provides a correction, new interpretation, translation preference, or relationship change:

1. Treat the user's statement as a source.
2. Save it verbatim as a dated note in `raw/`.
3. Use a filename such as:

```text
raw/2026-07-31-verbal-update-atomic-habits.md
```

4. Run the relevant ingest steps.
5. Update affected pages.
6. Preserve contradictions when needed.
7. Update `index.md`.
8. Append an `update` entry to `log.md`.

## Contradictions

Do not assume a newer book is more correct.

When two books conflict:

1. Preserve both claims.
2. Create separate zettels when the claims are distinct.
3. Link them as a contradiction or boundary condition.
4. Explain the disagreement neutrally.
5. Update the related book pages.
6. Update the relevant topic page.
7. Use `needs-review` only when the conflict may result from:
   - Translation ambiguity
   - Extraction error
   - Missing source context
   - Inconsistent wiki maintenance

## Duplicate Prevention

Before creating a new book, zettel, topic, or query:

1. Search filenames.
2. Search titles.
3. Search spelling variants.
4. Search aliases.
5. Search semantically similar content.
6. Prefer updating an existing page over creating a duplicate.
7. Merge only when two pages represent the same idea.
8. Keep separate notes when the ideas are meaningfully different.
9. Record merges and renames in `log.md`.
10. Update all affected wikilinks and `index.md` in the same turn.

## Lint / Health Check

Run this workflow when the user says:

- `lint`
- `health check`

Also suggest it after roughly every ten ingests.

Check for:

### General

- Broken wikilinks
- Orphan pages
- Duplicate pages
- Near-duplicate pages
- Invalid frontmatter
- Missing sources
- Inconsistent dates
- Index entries that do not match actual files
- One-sided relationships that should be bidirectional

### Sources and Translations

- Source pages without raw file references
- Translations without source pages
- Translations without book pages
- Book pages without translations
- Incomplete translations marked as complete
- Missing headings or changed source structure
- Unsupported translated content

### Books

- Books without source links
- Books without extracted zettels
- Books without topic links when clear topics exist
- Related-book claims without explanations
- Contradictions not reflected on both book pages

### Zettels

- Zettels without sources
- Zettels without books
- Zettels containing multiple unrelated ideas
- Notes that are only quotes
- Notes that are only chapter summaries
- Duplicate or near-duplicate notes
- Notes without meaningful connections
- Notes not linked from a book page
- Notes missing a relevant topic

### Topics

- Empty topic pages
- Topic pages without a central question
- Topic pages that are only lists
- Missing important related notes
- Unsupported relationships
- Open questions that have already been answered elsewhere

Fix mechanical issues automatically.

Ask before substantive rewriting.

Append a `lint` entry to `log.md`.

## Index Rules

`index.md` is the content-oriented catalog.

Required sections:

```text
Sources
Translations
Books
Zettels
Topics
Queries
```

Rules:

1. Include every wiki page.
2. Add a concise one-line description for each page.
3. Update the description when the page's purpose changes.
4. Reflect every create, rename, merge, or delete in the same turn.
5. Keep it easy to scan.
6. Do not use it as a chronological log.

## Log Rules

`log.md` is append-only.

Never edit, reorder, or delete previous entries.

Entry format:

```markdown
## [YYYY-MM-DD] ingest | Title
```

Allowed verbs:

- `ingest`
- `query`
- `lint`
- `update`
- `schema`
- `setup`

Each entry should briefly record:

- Source or request
- Files created
- Files updated
- Contradictions
- Review flags
- Renames or merges
- Important structural changes

## Hard Rules

1. Never modify anything in `raw/`.
2. Never rename a source file added by the user.
3. Never semantically read, translate, or extract notes from a raw file whose filename and SHA-256 fingerprint are already registered.
4. Never reprocess a duplicate file whose SHA-256 fingerprint is already registered under another filename.
5. Treat a filename with a changed fingerprint as an integrity conflict and report it.
6. Never invent book claims.
7. Never invent translation content.
8. Never invent relationships between ideas.
9. Every translation must trace to one exact raw source.
10. Every zettel must trace to at least one book and one source page.
11. Preserve the complete source structure in Persian translations.
12. Keep translations separate from summaries and analysis.
13. Search for duplicates before creating new pages.
14. Shared keywords alone do not prove a relationship.
15. Preserve disagreements between books.
16. Never silently choose one conflicting book as correct.
17. Every ingest, saved query, lint, update, setup, and schema change gets a `log.md` entry.
18. Every page create, rename, merge, or delete is reflected in `index.md` in the same turn.
19. Never store credentials or sensitive personal information.
20. Unknown information must remain explicitly marked.
21. `log.md` is append-only.
22. A translation is not a summary.
23. A zettel is not a chapter note.
24. A topic page is not a tag list.
