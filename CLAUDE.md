# Sagittarius RAG — AI Rules

## Project in one paragraph

Sagittarius RAG provides a RAG (Retrieval-Augmented Generation) tool over the Mag knowledge base (KB),
a set of AI-generated `.md` files, for a bigger project. Consumers are humans via chat/UI.
Deliverables: RAG tool, KB template and rules (with an automatic check), a daily index update, an update workflow, documentation.

Read before working: [Clarify](Docs/Project-Management/Initiation-phase/Clarify/Clarify.md) (what and why) and
[Approach](Docs/Project-Management/Initiation-phase/Approach.md) (method, gates, risks and the reasoning behind them).

## Status

Early stage: Clarify (not yet approved) and Approach. The tech stack (language, vector store, LLM, embedding model, UI) is **not decided**.
Do not pick one silently. Propose options with trade-offs and record the choice in `Docs/Decisions/`.

## Repository layout

| Path | Purpose |
|------|---------|
| `Docs/Project-Management/Initiation-phase/` | Clarify and Approach documents |
| `Docs/Decisions/` | Decision records (use `_template.md`) |
| `kb/` | The knowledge base (`.md` files) and its template, `kb/_templates/` |
| `eval/` | Test questions and evaluation notes (`questions.md`) |
| `.claude/skills/` | Project skills (KB authoring, KB review, RAG evaluation) |
| `src/`, `tests/` | Created when the stack is decided |

## Rules

1. **Do not invent facts.** If something is not in the docs or the KB, say so and mark it `TODO` or `Unknown — need to ask <who>`.
2. **Privacy first.** Whether KB content may go to an external LLM or embedding API is unknown. Never send KB content to an external service, and never add a cloud provider, without explicit approval.
3. **No secrets in git.** Keys, tokens, internal IPs and customer data stay out of the repo; use `.env` (git-ignored) and document variable names only.
4. **AI-generated KB is unverified.** Treat KB content as a claim, not truth. New or changed KB files get `status: draft` until a human sets `status: verified`. Never set `verified` yourself.
5. **KB template is provisional.** `kb/_templates/kb-article.md` and `kb/README.md` are one candidate approach, not a decision. Use them for drafts, but do not assume a template is the answer; measure it against the baseline.
6. **Smallest end-to-end first.** Prefer the simplest working version, then improve based on evaluation results in `eval/`. Do not add frameworks, rerankers or services without a measured reason.
7. **Every claim about quality needs the test set.** Changes to chunking, retrieval or prompts are judged against `eval/questions.md`.
8. **Answers must cite sources and may say "I don't know".** This applies to the RAG design and to any prompt written for it.
9. **Record decisions.** Any choice with alternatives goes into `Docs/Decisions/` (what, options, reason, when to revisit).
10. **Keep docs in sync.** If work changes scope, constraints or acceptance criteria, update Clarify; if it changes the method, gates, risks or reasoning, update Approach; if it chooses between alternatives, record it in `Docs/Decisions/`.

## Conventions

- Docs are in English, Markdown, with tables and Mermaid diagrams where useful.
- Use `TODO` for unfilled items, never leave silent blanks.
- Commit messages: short imperative subject (e.g. `add kb template`).
- Do not commit or push unless asked.

## Skills

| Skill | Use when |
|-------|----------|
| `kb-authoring` | Writing a new KB file, or converting an existing one to the template |
| `kb-review` | Checking KB files for template compliance and likely factual problems |
| `rag-eval` | Adding test questions or evaluating retrieval and answers |
