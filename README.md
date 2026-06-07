# picasso

Claude Code skills for writing and design. Each skill packages a single body of
taste — usually grounded in a published authority — into a form Claude can
invoke on demand.

## Install

```sh
cp -R skills/* ~/.claude/skills/
```

Claude Code picks them up on the next session. To install a single skill, copy
just its directory.

## Skills

| Skill                                                                     | Source / lineage                                                 | Use it for                                       |
| ------------------------------------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------ |
| [apple-hig](skills/apple-hig)                                             | _Macintosh Human Interface Guidelines_ (1992)                    | macOS / iOS / iPadOS UI decisions                |
| [clean-software-docs](skills/clean-software-docs)                         | Zinsser, _On Writing Well_                                       | READMEs, ADRs, code comments, PR descriptions    |
| [effective-written-communication](skills/effective-written-communication) | Minto, _The Pyramid Principle_; Zinsser                          | Emails, Slack, PR replies, status updates        |
| [fluff-scan](skills/fluff-scan)                                           | Zinsser, "Clutter" chapter                                       | Reviewing docs for buzzwords and throat-clearing |
| [laws-of-simplicity](skills/laws-of-simplicity)                           | Maeda, _The Laws of Simplicity_ (2006)                           | Cutting bloat from designs, APIs, processes      |
| [technical-writing](skills/technical-writing)                             | Zinsser, _On Writing Well_ and _Writing to Learn_                | Articles, design docs, long-form explainers      |
| [web-typography](skills/web-typography)                                   | Butterick, _Practical Typography_; Brown, _Flexible Typesetting_ | Type scale, line length, font loading on screens |

## Structure

Each skill is a directory containing a `SKILL.md` with YAML frontmatter (`name`,
`description`) and optionally supporting reference files. Claude reads the
description to decide when the skill applies, then loads the full body on
invocation.

## License

MIT.
