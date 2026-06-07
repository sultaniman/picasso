---
name: clean-software-docs
description:
  Use when writing or editing software engineering documentation — READMEs, API
  references, ADRs, runbooks, code comments, PR descriptions, changelogs, error
  messages. Strips fluff, buzzwords, throat-clearing, and marketing-style
  framing. Audience is engineers; precision wins over warmth.
---

# Clean Software Documentation

> **Lineage:** William Zinsser's _On Writing Well_ (1976) — specifically the
> "Simplicity" and "Clutter" chapters — applied to engineering documentation.
> Same audience-respect ethos, different shape: README, ADR, error message, PR
> description instead of essay.

## Core principle

**Docs are an interface to the code.** A developer reads them while interrupted,
in a hurry, with the source open in another tab. Every sentence costs them time.
If a sentence doesn't change what they do next, delete it.

**The code is the source of truth.** The doc's job is to tell the reader what
the code does, why it exists, how to use it, and what will surprise them —
nothing else. No backstory, no philosophy, no apologies, no congratulations.

## What to cut, ruthlessly

| Cut this                                                            | Because                                                  |
| ------------------------------------------------------------------- | -------------------------------------------------------- |
| "This document describes..." / "In this section we will..."         | The heading already said it                              |
| "It is important to note that..." / "Please be aware that..."       | If it's important, just state it                         |
| "Easy", "simple", "powerful", "elegant", "blazing-fast", "seamless" | Marketing words; tell me the actual property             |
| "Robust", "scalable", "production-ready"                            | Unfalsifiable; replace with a measurable claim or delete |
| "Leverage", "utilize", "facilitate", "orchestrate"                  | `Use`, `use`, `help`, `run`                              |
| "In order to"                                                       | `to`                                                     |
| "A number of" / "various" / "several"                               | Give the number, or drop the qualifier                   |
| Restating what the code obviously does                              | The code is right there                                  |
| Background on why you chose the file structure                      | Belongs in an ADR, not the README                        |
| Long preamble before the install command                            | The install command is what they came for                |

## Structure: invert the pyramid

Lead with the one thing the reader most likely needs. Then broaden.

A README in order:

1. **One sentence** — what this is. Concrete noun, not a metaphor. ("A Postgres
   connection pool for Node." not "A delightful database companion.")
2. **Install / quickstart** — copy-pasteable, runnable as-is
3. **Minimal working example** — 5–15 lines, real code
4. **Reference** — flags, options, types
5. **Behavior the reader would not guess** — defaults, side effects, ordering,
   concurrency, limits
6. **Troubleshooting** — actual errors and what they mean
7. Everything else (contributing, license, history)

If the reader can't run the thing within 30 seconds of opening the README, the
README failed.

## Code comments

**Default: no comment.** Well-named identifiers do the explaining. A comment is
justified only when _removing it would confuse a future reader who can read code
fluently_.

Write a comment when:

- The **why** is non-obvious — a hidden constraint, a workaround for a specific
  bug, a subtle invariant, an ordering requirement, a performance trick that
  looks dumb
- The behavior would surprise a careful reader — "yes, the loop runs once; don't
  'fix' it"
- An external contract is being honored — RFC citation, vendor quirk, hardware
  limit
- A `TODO` or `FIXME` with concrete context (ideally a ticket reference)

Don't write a comment that:

- Restates the code in English
- Says "added for the X flow" or "used by Y" — rots immediately, belongs in
  git/PR
- Apologizes for the code
- Marks removed code (`// removed validateFoo`) — just remove it; git keeps
  history

One short line is almost always enough. Multi-line comment blocks are a smell.

## API documentation

For each function, document in this order:

1. **One-line summary** — what it does, in the imperative ("Returns…", "Sends…",
   "Cancels…")
2. **Parameters** — types, required/optional, allowed values, units
3. **Returns / yields**
4. **Errors / exceptions** — what gets thrown, when, and what the caller should
   do
5. **Side effects** — writes, mutations, IO, blocking, network
6. **Example** — one real, runnable invocation

Skip prose like "This helper function is designed to…". The signature already
says it's a function.

## ADRs and design docs

State the decision first. Justify second.

```
# ADR-007: Use Postgres advisory locks for cron leader election

Decision: One row in `cron_leader` table; workers acquire pg_advisory_lock(id).
Rejected: Redis (extra dependency), Zookeeper (operational cost), file lock (no HA).
Trade-off: Tied to Postgres; if we ever multi-region, revisit.
```

The reader who skims should know the answer. The reader who reads gets the
reasoning.

## PR descriptions and commit messages

Two sections, nothing more:

- **What changed** — one or two bullets, present tense, concrete
- **Why** — the trigger; link to issue if relevant

Skip "test plan" boilerplate unless there's something non-obvious to test. Skip
restating the diff in English. The reviewer can read the diff.

Commit subject: imperative, ≤72 chars. Body wraps at 72. No emojis unless the
project asks for them.

## Error messages

A good error message tells the user:

1. **What went wrong** — specific, not "an error occurred"
2. **What state caused it** — the offending value, the path, the missing config
3. **What to do next** — the fix, or where to look

Bad: `ConfigError: invalid value` Better:
`ConfigError: PORT must be 1–65535, got "eighty"; set it in .env or pass --port`

## Buzzword blacklist

These signal marketing creep. If one appears in your draft, find what concrete
property it was hiding, and write that instead.

`seamless`, `effortless`, `blazing-fast`, `lightning-fast`, `cutting-edge`,
`next-gen`, `world-class`, `best-in-class`, `delightful`, `magical`,
`intuitive`, `simply`, `just`, `leverage`, `unlock`, `empower`, `revolutionary`,
`paradigm`, `synergy`, `holistic`, `robust`, `scalable`, `production-grade`,
`enterprise-ready`, `rich set of`, `under the hood`, `out of the box`.

A few of these are recoverable in context (e.g. _out of the box_ in install
docs). When in doubt, delete.

## Quick edit pass

Before merging docs changes:

- [ ] Could a stranger run the quickstart and have it work?
- [ ] Did I cut every sentence that doesn't change what the reader does?
- [ ] Did I cut every word that doesn't change what the sentence means?
- [ ] Are claims falsifiable? ("Handles 10k concurrent connections" beats
      "highly scalable.")
- [ ] Did I delete every "easy", "simple", "just"?
- [ ] Do code comments explain _why_, not _what_?
- [ ] Does each section's first sentence tell me whether I need to read the
      rest?

## Bad → good

| Bad                                                                                | Good                                                 |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------- |
| "This powerful CLI tool simplifies your workflow by leveraging modern APIs"        | "Renames files in bulk using regex."                 |
| "It is important to note that the function may throw"                              | "Throws `NotFound` if the user doesn't exist."       |
| "We use Postgres for reasons of scalability and reliability"                       | "Postgres: we need SQL joins and we already run it." |
| "Simply install with npm"                                                          | "Install: `npm i foo`"                               |
| "// increment counter" on `counter++`                                              | (delete the comment)                                 |
| "// retry up to 3 times because the upstream service is flaky around midnight UTC" | (keep — non-obvious WHY)                             |
