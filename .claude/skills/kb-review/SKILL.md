---
name: kb-review
description: Review Sagittarius KB .md files for template compliance and likely factual problems (unverified AI content, contradictions, stale info, secrets). Use when asked to check, audit or verify files under kb/. Does not mark files verified.
---

# KB review

Review one file, a folder, or the whole `kb/`. Rules come from `kb/README.md`.

## Checks

**A. Template compliance**
- Front-matter has `title`, `type`, `owner`, `status`, `last_verified`, `tags`, `source`; values are valid.
- `title` matches the single H1; heading levels do not skip.
- Sections are self-contained (no "see above"/"as mentioned"), roughly 150–500 words.
- File name is lowercase, hyphenated; relative links resolve.
- Code blocks have a language; steps are numbered.

**B. Privacy**
- No keys, tokens, passwords, customer data or internal IPs/hostnames. Report location only; do not repeat the secret.

**C. Likely factual problems** (AI-generated content is unverified)
- Specific claims that cannot be checked from the repo or provided sources (commands, versions, paths, numbers, names).
- Contradictions with other KB files, duplicated topics, outdated dates or versions.
- Vague or placeholder text presented as fact.

## Output

A table per file, ordered by severity:

| Severity | Location (file#heading) | Issue | Suggested fix |
|----------|-------------------------|-------|---------------|

End with counts (files checked, issues by severity) and a list of **questions for a human reviewer** (things only they can confirm).

## Rules

- Report; edit only if asked. Fixes that change meaning need a human decision.
- **Never set `status: verified` or `last_verified`.** Only a human does, after checking the content.
- Do not guess to fill gaps; say "cannot verify".
