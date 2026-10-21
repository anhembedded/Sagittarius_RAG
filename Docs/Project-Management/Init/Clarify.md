# Clarify — Sagittarius RAG

> Purpose of this file: write down *why* we build this and *what done looks like*, before writing code.
> Fill every `TODO`. If an answer is unknown, write "Unknown — need to ask <who>".

---

## 1. Why does this project exist?

My team works on project **Mag**. Over time we have written a lot of `.md` files
(design notes, how-tos, decisions, etc.). This knowledge exists, but it is hard to find.

We want to build a **RAG (Retrieval-Augmented Generation) tool** so people can ask
questions in natural language and get answers based on these `.md` files, with links
to the source.

Main goal: **make onboarding faster and more reliable** — a new member can find answers
by themselves instead of waiting for a senior teammate.

## 2. What is the current problem?

Describe the pain today, with real examples if possible.

- TODO: How does a new member find information today? (ask in chat, read folders, ask a mentor…)
- TODO: How long does onboarding take now? Where do new members get stuck?
- TODO: How much time do senior members spend answering repeated questions?
- TODO: Are the docs outdated, duplicated, or spread across many places?

Example questions a newcomer asks today (collect 5–10 real ones — they become the test set):

1. TODO: e.g. "How do I build and flash the firmware for Mag?"
2. TODO: e.g. "Why did we choose X instead of Y?"
3. TODO

## 3. Who are the users?

| User type | What they need | How often |
|-----------|----------------|-----------|
| New team member | TODO | TODO |
| Existing team member | TODO | TODO |
| TODO | | |

## 4. Knowledge source (the `.md` files)

- Where are the files? (git repo / shared drive / Confluence export…): TODO
- How many files and total size (approx.): TODO
- How often are they updated?: TODO
- Do they contain anything confidential (keys, customer data, internal IPs)?: TODO
- Other formats we may add later (PDF, code, images, diagrams)?: TODO

## 5. Scope

**In scope (v1):**
- TODO: e.g. Answer questions from `.md` files only
- TODO: e.g. Show source file + section for every answer

**Out of scope (not now):**
- TODO: e.g. Editing or writing docs automatically
- TODO: e.g. Answering questions outside Mag docs

## 6. Success criteria

How will we know it works? Make it measurable.

- TODO: e.g. ≥ 80% of the test questions in section 2 get a correct answer with the right source
- TODO: e.g. Answer time < 10 seconds
- TODO: e.g. New member onboarding time reduced from X days to Y days
- TODO: e.g. When the answer is not in the docs, the tool says "I don't know" instead of guessing

## 7. Constraints

- Budget (LLM API cost, hosting): TODO
- Must run locally / on-premise, or cloud is OK?: TODO
- Allowed LLM / embedding providers: TODO
- Access control (who can use it, do some docs need restricted access?): TODO
- Interface: CLI / web UI / chat bot (Slack, Teams…) / IDE plugin: TODO
- Deadline: TODO

## 8. Risks & open questions

| Risk / question | Impact | Owner | Status |
|-----------------|--------|-------|--------|
| Docs are outdated → tool gives wrong answers | High | TODO | Open |
| Sensitive info leaks to an external LLM API | High | TODO | Open |
| TODO | | | |

## 9. Stakeholders

| Name | Role | Responsibility |
|------|------|----------------|
| Nathan Tran | TODO | TODO |
| TODO | | |
