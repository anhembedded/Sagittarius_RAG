# Knowledge Base (KB)

This folder holds the Mag knowledge base used by the RAG. Files here are indexed daily.
The rules below make files good input for retrieval and easy to update.
They are **one candidate approach** (to be measured against the as-is baseline, see `Docs/Project-Management/Initiation-phase/Approach.md` §6), not a decision; the project may end up with different or lighter rules. They are **starting hypotheses**; they will be tuned in the proof of concept (Approach, Gate 3).

## How to add or update a file

1. Copy `_templates/kb-article.md` to the right place (e.g. `kb/firmware/build-and-flash.md`).
2. Fill the front-matter and sections. Delete sections that do not apply.
3. Leave `status: draft`. A reviewer sets `verified` after checking the content.
4. Open a pull request. The automatic check (when available) validates the rules.

## Rules

| # | Rule | Level |
|---|------|-------|
| 1 | One topic per file, one idea per section | Required |
| 2 | File starts with front-matter containing `title`, `type`, `owner`, `status`, `last_verified`, `tags` | Required |
| 3 | One H1 (the title), then H2/H3 sections; no skipped levels | Required |
| 4 | Each section is self-contained: name the subject, avoid "see above" / "as mentioned" | Required |
| 5 | Section length about 150–500 words; split longer ones | Recommended |
| 6 | File names are lowercase, hyphenated, stable (`build-and-flash.md`); do not rename without need | Required |
| 7 | Headings are stable and descriptive (they become citation anchors) | Required |
| 8 | Steps are numbered lists; commands are in fenced code blocks with the language | Recommended |
| 9 | Keep tables small; add a sentence saying what the table shows | Recommended |
| 10 | No secrets, keys, customer data or internal IPs | Required |
| 11 | State versions, dates and assumptions explicitly | Recommended |
| 12 | Link to related files with relative links | Recommended |

## Front-matter fields

| Field | Values | Meaning |
|-------|--------|---------|
| `title` | text | Same as the H1 |
| `type` | `how-to` / `concept` / `reference` / `decision` / `troubleshooting` | Kind of content |
| `owner` | name or team | Who keeps it correct |
| `status` | `draft` / `verified` / `deprecated` | `verified` only after human review |
| `last_verified` | `YYYY-MM-DD` or `never` | Date of last human check |
| `source` | `ai-generated` / `human` / `mixed` | How it was produced |
| `tags` | list | Topics for filtering |

## Status lifecycle

`draft` → (human review) → `verified` → (content changes) → `draft` → …
`deprecated` files stay for history but should not be answered from.

## Folder layout

```text
kb/
  README.md
  _templates/        # templates, not indexed
  <area>/            # e.g. firmware/, screen/, process/   (TODO: decide areas)
```

Files starting with `_` and this README are not part of the KB index.
