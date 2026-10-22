---
name: kb-authoring
description: Write a new Sagittarius KB .md file, or convert an existing/AI-generated file to the KB template. Use when asked to create, rewrite, split or restructure knowledge-base content under kb/.
---

# KB authoring

Produce KB files that follow `kb/README.md` and `kb/_templates/kb-article.md`. Read both first.

## Steps

1. **Identify the topic and reader.** One topic per file. If the source covers several topics, plan several files.
2. **Gather facts only from provided sources** (existing files, docs, user answers). Do not invent commands, versions, paths or names. Where a fact is missing, write `TODO: <what is missing>` in the text.
3. **Copy the template** to `kb/<area>/<stable-hyphenated-name>.md`.
4. **Fill the front-matter.** Always `status: draft` and `last_verified: never`. Set `source` honestly (`ai-generated` if you wrote or converted it). Never set `verified`.
5. **Write self-contained sections.** Name the subject in each section; avoid "see above". Keep sections about 150–500 words; split when longer. Use numbered steps and fenced code with a language.
6. **Check privacy.** Remove secrets, keys, customer data and internal IPs; replace with placeholders such as `<API_KEY>`.
7. **Link related files** with relative links, and make sure headings are descriptive (they are citation anchors).
8. **Self-check** against the rules table in `kb/README.md`, then list for the user: what was written, every `TODO`, and any claim you could not source.

## When converting an existing file

- Keep the meaning; restructure, do not add new facts.
- Preserve the original file name unless it breaks the naming rule; if renamed, say so (links may break).
- Report content that looks contradictory, outdated or unverifiable instead of silently fixing it.
