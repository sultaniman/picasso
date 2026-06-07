# References

## Primary source

**Maeda, John.** _The Laws of Simplicity: Design, Technology, Business, Life._
MIT Press, 2006. ISBN 978-0-262-13472-9. ~100 pages.

The book is organized as: Ten Laws + Three Keys + a closing "Life" page. Each
Law is a cluster of micro-essays with a one-line summary. Maeda intentionally
capped the page count at 100 to respect Law 3 (Time).

## The ten laws (Maeda's exact wording)

1. **Reduce** — _The simplest way to achieve simplicity is through thoughtful
   reduction._
2. **Organize** — _Organization makes a system of many appear fewer._
3. **Time** — _Savings in time feel like simplicity._
4. **Learn** — _Knowledge makes everything simpler._
5. **Differences** — _Simplicity and complexity need each other._
6. **Context** — _What lies in the periphery of simplicity is definitely not
   peripheral._
7. **Emotion** — _More emotions are better than less._
8. **Trust** — _In simplicity we trust._
9. **Failure** — _Some things can never be made simple._
10. **The One** — _Simplicity is about subtracting the obvious, and adding the
    meaningful._

## The three keys (technology lens)

1. **Away** — _More appears like less by simply moving it far, far away._
2. **Open** — _Openness simplifies complexity._
3. **Power** — _Use less, gain more._

## Mnemonic acronyms from the book

- **SHE** (Law 1, Reduce) — Shrink, Hide, Embody.
- **SLIP** (Law 2, Organize) — Sort, Label, Integrate, Prioritize.
- **BRAIN** (Law 4, Learn) — Basics, Repeat, Avoid (desperation), Inspire, Never
  (forget to repeat).
- **RELATE-TRANSLATE-SURPRISE** (Law 4, Learn) — the metaphor pattern.
- **ROE** (Law 7, Emotion) — Return On Emotion.
- **ROF** (Law 9, Failure) — Return On Failure.

## Books Maeda credits as inspiration (his "BOOKS" page)

| Section             | Book                                | Author                      | Year |
| ------------------- | ----------------------------------- | --------------------------- | ---- |
| Simplicity = Sanity | _The Tipping Point_                 | Malcolm Gladwell            | 2002 |
| Reduce              | _The Paradox of Choice_             | Barry Schwartz              | 2005 |
| Organize            | _Notes on the Synthesis of Form_    | Christopher Alexander       | 1964 |
| Time                | _Toyota Production System_          | Ohno Taiichi                | 1988 |
| Learn               | _Motivation and Personality_        | Abraham Maslow              | 1970 |
| Differences         | _The Innovator's Solution_          | Clay Christensen            | 2003 |
| Context             | _Six Memos for the Next Millennium_ | Italo Calvino               | 1993 |
| Emotion             | _Emotional Design_                  | Donald Norman               | 2003 |
| Trust               | _The Long Tail_                     | Chris Anderson              | 2006 |
| Away                | _Technics and Civilization_         | Lewis Mumford               | 1963 |
| Open                | _The Wisdom of Crowds_              | James Surowiecki            | 2004 |
| Power               | _Cradle to Cradle_                  | W. McDonough & M. Braungart | 2002 |
| Life                | _Disabling Professions_             | Ivan Illich                 | 1978 |

Maeda's own earlier books: _Maeda@Media_ (2001), _Creative Code_ (2004), _Design
by Numbers_ (MIT Press, 1999).

## Web companion

The book references `lawsofsimplicity.com` as its companion site (active as of
publication in 2006; verify before linking — sites of that vintage often go dark
or redirect).

## Key terms from the book worth knowing

- **Aichaku** (愛着, ai-chaku) — Japanese for "love-fit." The emotional
  attachment a person can feel for an object. Law 7.
- **Omakase** (おまかせ) — "I leave it up to you." The sushi-bar move where the
  chef chooses. Law 8's central metaphor for trust-based simplification.
- **Konjo** (根性, kon-joe) — the Master's pride / grit. The internal force that
  makes omakase work. Law 8.
- **Gestalt / gestaltung** — German for "form" / "design"; the mind's ability to
  fill in the blank and perceive grouped wholes. Central to Law 2.
- **Lean back** — Bang & Olufsen's design philosophy of relaxation-as-quality,
  used in Law 8 as a contrast to the "lean in / engage" mode.

## Cross-skill pointers

The Laws overlap with several other skills in this directory. Pick the more
specific one when its scope fits:

| When you're working on…                   | Use this skill alongside laws-of-simplicity                                                                  |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Apple platform UI specifically            | `apple-hig` — same simplicity ethos, but grounded in the 1992 Macintosh HIG and Apple-specific patterns.     |
| UI copy (errors, empty states, microcopy) | `clean-software-docs` for engineer-facing text; `darkroom-copy` for the Darkroom-specific neutrality rules.  |
| Long-form technical writing               | `technical-writing` (Zinsser) — Law 1 (Reduce) is essentially Zinsser's "clutter" chapter applied to design. |
| Reviewing prose for fluff                 | `fluff-scan` — Law 10 in editing form: subtract the obvious.                                                 |
| Picking between competing visual designs  | `mockup-driven-design-exploration` — uses simplicity as one of several tie-breakers, not the only one.       |
| Frontend production work                  | `frontend-design:frontend-design` for execution; this skill for the _what to cut_ judgment.                  |

## Where this skill applies less well

- **Tax/legal/regulatory domains** — Law 9 (Failure) explicitly warns against
  forcing simplicity here.
- **Safety-critical code** — explicit, redundant, "boring" is often correct.
  Don't apply Law 1 to error-handling in a way that hides failure modes.
- **Internal tools used by 3 experts** — the simplicity gains often don't
  justify the redesign cost; Law 10's "one thing" might already be served.

## Quick scan: which law for which symptom

| Symptom                                       | Most likely law |
| --------------------------------------------- | --------------- |
| Too many features / buttons / options         | 1 (Reduce)      |
| Cluttered but everything seems necessary      | 2 (Organize)    |
| Users complain about wait / scroll / clicks   | 3 (Time)        |
| First-run friction; users get stuck           | 4 (Learn)       |
| Everything looks the same; nothing stands out | 5 (Differences) |
| Works in isolation, feels off in production   | 6 (Context)     |
| Correct but cold / sterile / forgettable      | 7 (Emotion)     |
| Users hesitate or won't commit to actions     | 8 (Trust)       |
| You've spent a week and it's still complex    | 9 (Failure)     |
| Closing pass before ship                      | 10 (The One)    |
| Slow page; heavy bundle                       | Key: Away       |
| Closed system is the bottleneck               | Key: Open       |
| Resource budget is the actual constraint      | Key: Power      |
