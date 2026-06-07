---
name: fluff-scan
description:
  Use when reviewing or editing technical documentation, design specs, ADRs,
  READMEs, code comments, or commit messages — especially when the audience is
  domain experts and the prose contains buzzwords, marketing language, vague
  intensifiers, throat-clearing phrases, or restatements of the obvious.
---

# Fluff Scan

> **Lineage:** operationalizes the "Clutter" and "Simplicity" chapters of
> William Zinsser's _On Writing Well_ (1976) into a categorized scan-and-approve
> workflow. The cutting half of the same discipline that `technical-writing`
> uses for authoring.

Detect and remove fluff from technical writing aimed at domain experts. Audience
assumption: the reader is a fluent practitioner of the topic. Cut anything that
doesn't carry information, instruction, or constraint.

## Workflow

1. **Scan** the target file(s).
2. **Report** every issue as a categorized bullet list (format below). Do not
   edit yet.
3. **Ask** the user: "Apply all / apply selected (numbers) / skip?"
4. **Apply** only what the user approves. If selected, list which numbers were
   applied; if skipped, leave the file untouched.

Never edit before step 4. The user must see the issues first.

## What to flag

| Category                | Examples                                                                                                                                           |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `buzzword`              | production-grade, world-class, best-in-class, battle-tested, robust, seamless, cutting-edge, enterprise-class, industry-standard, mission-critical |
| `marketing`             | unlock value, deliver substantial impact, drive transformation, journey, paradigm shift, next-generation, future-proof                             |
| `intensifier`           | significantly, substantially, dramatically, vastly, absolutely, truly, extremely (when unquantified)                                               |
| `throat-clear`          | It should be noted that, It is worth mentioning, As you may know, Specifically (as a sentence-leader with no following specificity), Of course     |
| `wordy`                 | in order to → to; for the purposes of → to/for; in the event that → if; due to the fact that → because; utilize → use; leverage → use              |
| `self-praise`           | clean code, idiomatic, elegant, sensible default (when self-applied)                                                                               |
| `editorial`             | "this is the right call", "the obvious choice", "that would be an anti-pattern" (state the rule, not the verdict)                                  |
| `restate-obvious`       | claims a domain expert already knows ("indexes speed up reads", "JSON is human-readable")                                                          |
| `unquantified`          | "high performance", "low latency", "fast" without numbers, "scalable" without a target                                                             |
| `preamble`/`conclusion` | intro paragraphs that summarize the doc; conclusion paragraphs that restate the goals                                                              |
| `hedge`                 | could potentially, may possibly, in some cases (when no case is given)                                                                             |

## What NOT to flag

- Technical terms used precisely: "double-submit cookie", "Argon2id", "TOTP" —
  these are jargon, not buzzwords.
- Quantified claims: "reduces p99 latency by 40%", "supports 10k RPS" — keep.
- Code, identifiers, file paths, error messages.
- Domain vocabulary the project explicitly preserves (check `CLAUDE.md` /
  project memory before flagging anything that looks like project-specific
  terminology).
- A single technical adjective that carries information: "asymmetric
  encryption", "idempotent endpoint".
- Brevity sacrifices: do not flag a line just to make it shorter when the result
  loses precision.

## Output format

One bullet per issue, in file order. Keep each bullet on one line.

```
- L<n> [category] "<exact fragment>" — <one-clause why> → "<rewrite>"  (or → DELETE)
```

Examples:

```
- L7 [buzzword] "production-grade, scalable" — stacked adjectives carry no info → DELETE
- L11 [wordy] "In order to" — bloated → "To"
- L24 [self-praise] "clean, idiomatic Go interface" — self-praise → "Go interface"
- L48 [restate-obvious] "This ensures clear ownership and avoids accidental collisions" — known to anyone reading this → DELETE
```

End the report with a single line:

```
TOTAL: <n> issues across <m> categories
```

## Multi-file scans

When given a directory or glob, output a separate section per file with its own
bullets and totals, then a final overall total. Do not merge issues across files
into a single list.

## After applying

If the user approves edits, apply them as exact-string replacements. After
applying, print:

```
APPLIED: <n> edits to <file>
SKIPPED: <numbers> (per user)
```

Do not run a second scan automatically — the user invokes again if they want.

## Calibration rules

- **Default audience: domain expert.** If the user names a different audience
  ("for new hires", "for non-engineers"), relax the `restate-obvious` and jargon
  rules accordingly.
- **Translation docs.** When scanning a non-English file, apply the same
  categories using equivalent words in that language. Do not rewrite into
  English.
- **Code comments.** Apply `wordy`, `throat-clear`, `restate-obvious` strictly.
  Do not flag terse comments that name a non-obvious WHY.
- **Commit messages.** Be aggressive on `marketing`, `buzzword`, `self-praise`.
  Don't comment on commit-message style conventions (prefix schemes, casing,
  length) — that's a project preference, not fluff.

## Common mistakes

| Mistake                                             | Fix                                                                                                                     |
| --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Flagging precise jargon as buzzword                 | Check the `What NOT to flag` table; if it carries technical meaning, leave it.                                          |
| Editing before the user approves                    | Re-read the workflow. Step 2 is report, step 4 is edit.                                                                 |
| Auto-applying "all" without naming what was applied | Always print the `APPLIED:` summary so the user can review.                                                             |
| Inventing line numbers                              | If the tool you used doesn't surface line numbers, re-read the file with line numbers (e.g. `cat -n`) before reporting. |
| Suggesting a longer rewrite                         | If the rewrite is not shorter or clearer, the original wasn't fluff. Drop the bullet.                                   |

## See also

- `laws-of-simplicity` — the framing behind this skill. Fluff-scan is Law 1
  (Reduce) and Law 10 (subtract the obvious) applied to prose.
- `technical-writing` — use when _authoring_ technical prose, not just cutting
  it (Zinsser-based).
- `clean-software-docs` — same fluff-cutting ethos extended to broader
  engineering docs (READMEs, ADRs, error messages, PR descriptions).
