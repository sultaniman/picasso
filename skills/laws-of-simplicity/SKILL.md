---
name: laws-of-simplicity
description:
  Use when a design, interface, API, doc, process, or feature feels bloated,
  cluttered, or hard to use, and you need a thinking framework for what to cut
  and what to keep. Grounded in John Maeda's *The Laws of Simplicity* (MIT
  Press, 2006).
---

# Laws of Simplicity

> **Source:** John Maeda, _The Laws of Simplicity: Design, Technology, Business,
> Life_, MIT Press, 2006 (~100 pages). Grew out of Maeda's MIT SIMPLICITY
> Consortium and his blog of the same name.

## Core principle

> **Simplicity is about subtracting the obvious, and adding the meaningful.** —
> Law 10, _The One_

Simplicity is not minimalism for its own sake. It is the disciplined practice of
removing what does not earn its place, while preserving — or amplifying — what
does. Complexity and simplicity are not opposites; they need each other (Law 5).
The work is finding the right rhythm between them.

## When to use

Reach for this skill when:

- A UI, screen, or component has accumulated controls/options/states and feels
  heavy
- An API or function signature has grown parameters faster than its callers
- A doc, error message, or onboarding flow feels long but doesn't seem cuttable
- You're choosing between two designs and "simpler" is the tie-breaker but not
  yet defined
- A feature is technically correct but users complain it's confusing, slow, or
  untrustworthy
- You're tempted to add a setting/toggle rather than make a decision

**Don't use when:** the problem is correctness (broken code), security, or a
missing capability. Simplicity is a quality lens, not a substitute for
engineering rigor.

## The ten laws — quick reference

| #   | Law             | One-line gist                             | Apply when                                                |
| --- | --------------- | ----------------------------------------- | --------------------------------------------------------- |
| 1   | **Reduce**      | Simplest path is thoughtful reduction.    | Anything has too many features/buttons/options            |
| 2   | **Organize**    | Many appear fewer when grouped well.      | You can't reduce further but it still feels busy          |
| 3   | **Time**        | Saved time feels like simplicity.         | Users wait, scroll, click, or load too much               |
| 4   | **Learn**       | Knowledge makes everything simpler.       | Users hit a wall the first time                           |
| 5   | **Differences** | Simplicity needs complexity to exist.     | Everything looks the same; nothing stands out             |
| 6   | **Context**     | The periphery is not peripheral.          | The thing works in isolation but feels off in situ        |
| 7   | **Emotion**     | More emotion is better than less.         | The result is correct but feels cold or sterile           |
| 8   | **Trust**       | In simplicity we trust.                   | Users hesitate, double-check, or won't commit             |
| 9   | **Failure**     | Some things can't be made simple.         | You've burned days chasing simplicity that won't come     |
| 10  | **The One**     | Subtract the obvious, add the meaningful. | Closing pass — does every remaining thing earn its place? |

## The three keys (technology lens)

| Key       | Gist                                      | Apply when                                                  |
| --------- | ----------------------------------------- | ----------------------------------------------------------- |
| **Away**  | More feels like less when moved far away. | Offload work to remote/managed/background                   |
| **Open**  | Openness simplifies complexity.           | A closed system is the bottleneck — open APIs, OSS, plugins |
| **Power** | Use less, gain more.                      | Energy/resource budgets are the actual constraint           |

## How to apply — the SHE / SLIP / BRAIN moves

Maeda gives operational moves under three laws. They're the most directly usable
tools in the book.

### Law 1 (Reduce) — **SHE**

1. **Shrink** — make it smaller / lighter / thinner; lowers expectations, earns
   forgiveness when it falls short.
2. **Hide** — conceal complexity behind a door, menu, or progressive disclosure;
   reveal on demand.
3. **Embody** — invest the remaining surface with perceived quality (materials,
   craft, copy, motion) so "less" feels valuable, not cheap.

Order matters: you can only hide once you've removed what's genuinely removable;
you can only get away with embodiment if shrinking and hiding came first.

### Law 2 (Organize) — **SLIP**

1. **Sort** — lay out every item; find natural groupings.
2. **Label** — name each group; if no name fits, use an arbitrary code.
3. **Integrate** — collapse groups that overlap; fewer groups is better.
4. **Prioritize** — pull the vital few (Pareto 80/20) into a focus set that gets
   the most attention.

This is a literal post-it / whiteboard exercise. It applies to nav menus, form
fields, dashboard widgets, settings pages, taxonomy.

### Law 4 (Learn) — **BRAIN**

1. **Basics** — assume the position of the first-time learner.
2. **Repeat** — repetition is not lazy; it conditions understanding.
3. **Avoid** desperation — a gentle, inspired start beats "shock and awe."
4. **Inspire** with examples.
5. **Never** forget to repeat yourself.

Also: **RELATE → TRANSLATE → SURPRISE** — the metaphor pattern (desktop / folder
/ trash). Anchor in something known, map it to the new thing, then surprise with
what only the new thing can do.

## The rhythm test (Law 5)

Before declaring something "simple enough," ask: _what is the complexity it sits
against?_ A flat field of simplicity is boring; a flat field of complexity is
exhausting. Good designs alternate — like a song. If your screen / doc / API
surface has no rhythm at all, the simplicity won't read as simplicity.

## Closing pass — Law 10 questions

Before shipping a simplification, run these:

1. What is the **one** thing this should do? Does everything else support that
   one thing, or distract from it?
2. What did I **subtract**? Was it actually obvious (not load-bearing)?
3. What did I **add** that's meaningful? (Subtraction without addition often
   leaves a hole, not simplicity.)
4. If I had to remove one more thing, what would it be? Why am I not removing
   it?

## Anti-patterns

- **Reduce-only.** Stripping features without embodying quality elsewhere →
  cheap, not simple.
- **Hide everything.** Three levels of menus is not simplicity; it's relocation.
  The user still pays.
- **Organize then stop.** Good groupings without prioritization → cleaner
  clutter, still cluttered.
- **Speed at all costs.** Sometimes the answer isn't "faster," it's "make the
  wait tolerable" (progress bars, ambient cues, Law 3).
- **Sterile minimalism.** Forgetting Law 7 — the result is "correct" and
  joyless. Users feel nothing for it.
- **Chasing simplicity that won't come.** Law 9: some domains (tax law, medical
  triage, distributed consensus) resist simplification. Recognize and stop
  sooner.

## Red flags you're rationalizing complexity

| Excuse                                           | Reality                                                                             |
| ------------------------------------------------ | ----------------------------------------------------------------------------------- |
| "Power users need this option."                  | Power users adapt. Defaults shape everyone's experience.                            |
| "We can't remove it — someone's using it."       | Measure. Often "someone" is < 1% and the cost falls on 99%.                         |
| "Adding a setting is the safe choice."           | Settings are deferred decisions. The cost is paid by every future reader of the UI. |
| "It's already there — leaving it costs nothing." | It costs attention every time someone scans the screen.                             |
| "Simpler would feel too plain."                  | Maybe — see Law 7 (embody emotion) before adding back features.                     |

## See also

- `examples.md` — concrete applications, including software/design parallels and
  notes for backend & frontend work.
- `references.md` — the source bibliography Maeda credits, plus cross-skill
  pointers (clean-software-docs, fluff-scan, mockup-driven-design-exploration,
  apple-hig).
