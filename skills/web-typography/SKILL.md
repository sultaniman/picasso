---
name: web-typography
description:
  Use when setting type on the web or any screen UI — body copy, headings,
  navigation, forms, data tables, marketing pages — and you need a thinking
  framework for type scale, line length, leading, font choice, web-font loading,
  accessibility, or diagnosing why a page just feels wrong. Grounded in Matthew
  Butterick's *Practical Typography* and Tim Brown's *Flexible Typesetting*.
---

# Web Typography

> **Sources:** Matthew Butterick, _Practical Typography_
> (practicaltypography.com, 2010–ongoing) — the most direct screen-native
> reference for "what matters." Tim Brown, _Flexible Typesetting_ (A Book
> Apart, 2018) — the framework for setting type on the web specifically, where
> the viewport flexes and readers participate. The print canon (Bringhurst, _The
> Elements of Typographic Style_, 1992) provides the philosophical anchor.

## Core principle — what matters

> **Typography is what makes a page readable. Choosing a font is the least
> important part of it.** — paraphrasing Butterick

Most of what people call "typography" — picking a typeface — barely matters next
to the things that actually do: **point size, line spacing, line length, white
space, and contrast**. Get those five right with the system font and the page
reads beautifully. Get those five wrong with the most expensive font in the
world and it reads badly.

## Brown's frame — pressure

> **There are no "correct" fonts, font sizes, measures, or line heights. But the
> relationships among them determine whether reading is easier or harder.** —
> paraphrasing Brown

The four core properties of any text block — **typeface, font size, measure
(width), and line spacing** — are interdependent. Change one and the others must
respond. When that relational balance breaks, readers don't see the cause; they
just feel that something is wrong. Brown calls this **pressure**, and it's the
central concept of typesetting for the web.

On the web, pressure is constant: the viewport flexes, web fonts fail to load,
readers override your font-size from their browser settings. The job of a web
typographer is no longer to decide — it's to make typographic _suggestions_ that
hold up under pressure. **Get a raincoat, don't predict the weather.**

## When to use

Reach for this skill when:

- Setting up a design system's type scale, leading, or line-length rules
- A page reads "fine" but feels heavy, cramped, or anonymous — diagnose the
  pressure
- Headings and body don't feel like a system — sizes/weights chosen ad hoc
- You're picking a web font and don't know how to evaluate it
- Font loading is causing FOIT/FOUT/layout shift
- Accessibility audit flagged contrast, scale, or readability
- A data table or form feels noisy regardless of how you space it

**Don't use when:** the problem is content (the words are wrong) or layout (the
boxes are wrong). Fix those first; type can't rescue bad copy or bad structure.

## Three typographic jobs

Brown distinguishes three modes of working with type. Different jobs need
different typefaces and decisions — recognize which job a block is doing before
picking a face.

| Job                  | Purpose                           | Examples                                          |
| -------------------- | --------------------------------- | ------------------------------------------------- |
| **Setting type**     | Help readers read                 | Paragraphs, body lists, subheads, captions, decks |
| **Arranging type**   | Catch attention, set tone         | Hero text, top-level headings, CTAs, logotypes    |
| **Calibrating type** | Help readers scan structured info | Tables, navigation, infographics, math, code      |

Most pressure on the web shows up in _setting type_ — the body. If the body
fails, nothing else recovers. This skill is focused there.

## The five things to get right (before picking a font)

| #   | Property                   | Rule of thumb                                                                                   |
| --- | -------------------------- | ----------------------------------------------------------------------------------------------- |
| 1   | **Point size (body)**      | 16–20px on screen. Never below 16.                                                              |
| 2   | **Line spacing (leading)** | 1.4–1.6× the font size for body. Tighter for display, looser for long-form.                     |
| 3   | **Line length (measure)**  | 45–75 characters per line. ~66 is the sweet spot. Use `max-width: 65ch` or `clamp()`.           |
| 4   | **White space**            | Generous margins. Long-form needs 40–60% of the screen as margin. The reader's eye needs rest.  |
| 5   | **Contrast**               | WCAG AA minimum: 4.5:1 for body. AAA: 7:1. Grey-on-grey is the most common readability failure. |

If you do nothing else, do these five. Everything below is refinement.

## Order of adjustment

The four properties depend on each other. Adjust in this order, and re-evaluate
downstream after every upstream change:

**typeface → font size → measure → line spacing**

| If you change… | …reconsider                                                                          |
| -------------- | ------------------------------------------------------------------------------------ |
| Typeface       | Size (same px looks visually different across fonts), then measure, then leading     |
| Font size      | Measure (cap ~75 chars; raise it as size grows) and leading (looser at larger sizes) |
| Measure        | Leading — wider measures need looser leading, narrower need tighter                  |
| Line spacing   | Just leading, usually — if a change feels forced, the issue is upstream              |

Start **mobile-first**. The narrowest viewport pressures every relationship
hardest; conventions you establish there carry up the breakpoints.

## Type scale — pick a ratio, not numbers

Don't pick sizes ad hoc. Use a modular scale: every size is the previous one
multiplied by a fixed ratio.

| Ratio | Name           | Use when                                                   |
| ----- | -------------- | ---------------------------------------------------------- |
| 1.125 | Major second   | Dense UI (admin, dashboards) — small steps, lots of levels |
| 1.200 | Minor third    | Default for app UI — balanced                              |
| 1.250 | Major third    | Marketing, slightly more dramatic hierarchy                |
| 1.333 | Perfect fourth | Editorial / long-form                                      |
| 1.500 | Perfect fifth  | Dramatic — only with few levels                            |
| 1.618 | Golden ratio   | Editorial / hero pages — feels classical                   |

Example (16px base, 1.25 ratio): 12.8, 16, 20, 25, 31.25, 39, 49, 61, 76. Round
to whole pixels.

Tools: `modularscale.com` (Brown's), `utopia.fyi` (for fluid type with
`clamp()`).

## Line length — the most-broken rule on the web

A line longer than ~75 characters tires the eye; shorter than ~45 feels
staccato. Most sites get this wrong by setting body text against the full
viewport width.

```css
.prose {
  max-width: 65ch;
} /* simple */
.prose {
  max-width: clamp(45ch, 60vw, 75ch);
} /* responsive */
```

For multi-column or narrow contexts, allow shorter measures, but never let body
text run full-width on a 1440px desktop.

**Brown's read-aloud test** (from Juliette Cezzar): read a paragraph aloud,
breathing only at line breaks. Gasping → measure too long. Hyperventilating →
measure too short.

## Hierarchy without color

Color is for **emphasis**, not **structure**. A document whose hierarchy depends
on color breaks for colorblind readers, in dark mode, and in print. Build
hierarchy with:

1. **Size** — first lever
2. **Weight** — second lever (400 vs 700 reads stronger than 16px vs 18px)
3. **Space** — most underused lever; margin-top of a heading should be larger
   than margin-bottom
4. **Family** — last lever; only if you've already committed to two faces

Reach for color only after the first three already establish hierarchy.

## Picking a typeface

Pick a **body-text typeface first** and let it anchor everything. Brown calls
this the _anchor typeface_ — it does the most work, sets the size reference, and
constrains the rest of the palette. Body-text faces make the best anchors
because they're built to stay robust at small sizes and survive many contexts.

### Three criteria for a body-text face (in priority order)

1. **Sturdy shapes** — no scrawny terminals, no dainty serifs, no over-delicate
   strokes. "Boring" at body sizes reads as steady. Larger x-heights generally
   read more solid at small sizes.
2. **Even color** — typographic _color_ is the overall grey value of a
   paragraph. Squint at a sample: do you see consistent grey, or white spots and
   dark patches? Inconsistencies distract.
3. **Active texture** — the rhythm of the page. A face with no rhythm reads
   dull; an over-active face distracts. Test in real paragraphs, not specimens.

Evaluate in that order: sturdiness first, then color, then texture.

### Palette rules

| Rule                                                           | Why                                                                                                                                                                |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **One font is enough. Two is the maximum.**                    | More than two looks like a ransom note. If you need contrast, change weight or size, not family.                                                                   |
| **Use the system font stack unless you have a reason not to.** | Zero load cost, no FOIT/FOUT, optimized by the OS for the user's screen. `font-family: system-ui, -apple-system, ...`                                              |
| **Pair sans (UI) + serif (long-form prose) if you need two.**  | Or mono + sans. Never two sans or two serifs of similar voice.                                                                                                     |
| **Variable fonts > multiple static weights.**                  | One file, many weights. Smaller payload, finer control (`font-weight: 437`).                                                                                       |
| **Test at the actual point size you'll use.**                  | A font that looks great at 60px in a specimen can be illegible at 14px.                                                                                            |
| **Pair on shared rhythm and proportions.**                     | When auditioning a second face, set the same word in both. Their black-and-white rhythm — vertical stress, letter spacing, x-height — should harmonize, not clash. |

Common safe choices for body text on the web:

- **System UI stack** — `system-ui` (Inter on most Linux, SF Pro on Apple, Segoe
  UI on Windows). Free, fast, well-rendered.
- **Inter** — designed for screens, free, available variable. The most common
  modern web body face.
- **IBM Plex Sans** — free, distinctive, has a serif and mono companion.
- **Source Sans 3** — Adobe's open sans family, well-hinted.
- **Charter, Georgia, Bitstream Charter** — for screen-readable serif body.

## The familiar x-height method

Brown's technique for picking a body-text font size that _feels familiar_
regardless of typeface:

1. Measure the **x-height** of your body face (height of lowercase `x` ÷
   font-size).
2. Target an x-height between **`.419em`** and **`.579em`** — the familiar
   range, derived from Times New Roman at 15px (.447em) and Verdana at 17px
   (.545em). These were the dominant body faces of the early screen-typography
   era; readers' eyes are calibrated to them.
3. Find a font-size at which your face's x-height lands in that range.

This corrects the fact that the same `font-size` value renders visually
different across fonts — two faces set at `16px` can look like 14px and 18px.
Sizing by _x-height_ keeps body text feeling familiar regardless of the spec
sheet.

## Web-specific: font loading

The default loading behavior of `@font-face` is bad. Use `font-display`:

| Value      | Behavior                                            | When to use                                                     |
| ---------- | --------------------------------------------------- | --------------------------------------------------------------- |
| `swap`     | Show fallback immediately, swap when web font loads | **Default good choice.** Best perceived performance.            |
| `optional` | Use web font only if cached / fast                  | Critical above-the-fold copy where layout shift is unacceptable |
| `fallback` | Brief invisibility, then fallback if slow           | Rare; trades a small FOIT for less swap                         |
| `block`    | Invisible text up to ~3s                            | Almost never the right choice                                   |

Other practices:

- **Preload heroes:**
  `<link rel="preload" as="font" type="font/woff2" crossorigin>` for the one or
  two font files that render above the fold.
- **Subset:** ship only the glyph ranges you need (Latin, Cyrillic, etc.) via
  `unicode-range`. Cuts WOFF2 size by 50–90% for non-Latin sites.
- **Self-host when possible.** Third-party font CDNs cost a DNS lookup and a
  CORS round-trip; self-hosted is one connection.
- **Limit weights.** Each weight is bytes. Two weights (regular + bold) covers
  80% of UIs.

**Match the fallback.** A fallback face should have an x-height, cap height, and
average glyph width close to your intended webfont so the swap doesn't jolt the
layout. Use `size-adjust`, `ascent-override`, and `descent-override` on the
fallback `@font-face` to tune metrics. Brown's pattern: scope custom styles to a
`.wf-active` class (or `font-loading-api`) so unstyled fallback gets safe
defaults.

## CSS units for type

| Unit                         | Use for                                                                                                    | Avoid for                                    |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| `rem`                        | Component sizes that should scale with user's root font-size                                               | Layout that must stay pixel-perfect          |
| `em`                         | Spacing relative to the element's own size (padding inside a button, vertical margins inside a text block) | Whole-page sizing — compounds unpredictably  |
| `ch`                         | Line length and column widths                                                                              | Vertical metrics                             |
| `px`                         | Borders, hairlines, fixed icons                                                                            | Body text size (loses accessibility scaling) |
| `clamp(min, preferred, max)` | Fluid type that respects bounds                                                                            | Whenever a fixed value would do              |

**Never** set body text in `px` only — use `rem` so the user's browser font-size
preference is respected. **Em-based media queries** respect that preference too;
`px` queries do not.

## Punctuation and detail

These are tiny moves that separate amateur from professional:

- **Curly quotes**, not straight: `"` not `"`. Use
  `&ldquo; &rdquo; &lsquo; &rsquo;` or smart-quote the source.
- **Em dash** for parenthetical breaks — like this. Not double hyphens.
- **En dash** for ranges: `2020–2024`, not `2020-2024`.
- **Ellipsis** character `…`, not three periods.
- **Non-breaking space** before units: `5 km`, `10 MB` — keep number and unit
  together.
- **Numerals:** prefer _oldstyle_ (proportional) for body, _lining_ (tabular)
  for tables. `font-variant-numeric: tabular-nums;` for data tables.
- **Hanging punctuation** for quotes (`hanging-punctuation: first;`) — supported
  in Safari, gracefully ignored elsewhere.

## Accessibility — readers are typographers too

Brown's framing: typography on the web is _multidimensional, relative, and
optional_. Readers can — and do — override font-size, disable web fonts, use
Reader Mode. Design for that.

- **Never go below 16px for body text.** 14px is borderline; 12px secondary text
  is hostile.
- **Use `rem`, not `px`, for type sizes.** Users who set a larger default
  font-size in their browser must be able to scale your site.
- **Don't override `:root { font-size }` with `px`.** That silently breaks the
  reader's browser accessibility setting.
- **Respect `prefers-reduced-motion`** — don't animate type movement for users
  who've opted out.
- **Test at 200% browser zoom.** Type should reflow, not clip.
- **Maintain WCAG AA contrast** for all text, including disabled states (which
  often get exempted — that's a misreading of the spec).
- **Dyslexia-friendly defaults:** generous leading (1.5+), wider letter-spacing
  (0.05em on small caps), ragged-right alignment.

## Anti-patterns

| Anti-pattern                                           | Why it's wrong                                                                                                 |
| ------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Body text justified (`text-align: justify`) on the web | Browsers can't hyphenate well; rivers of white open up. Stick to ragged-right (left-aligned).                  |
| Centered body paragraphs                               | Forces the eye to re-find the line start on every line. Only acceptable for captions or single-line elements.  |
| Tiny secondary text (10–12px)                          | Hostile to readers > 40 and to anyone on a high-DPI display in standard zoom.                                  |
| Three or more font families                            | Reads as chaos. Use weight and size instead.                                                                   |
| Loading six font weights "to be flexible"              | Bytes. Pick two; use them everywhere.                                                                          |
| Picking the font first                                 | Picking the font last is the right order. Get scale and leading right with system-ui first.                    |
| Body line-height < 1.4                                 | Cramped; eye loses the next line.                                                                              |
| Body line longer than the viewport (no max-width)      | The most common readability failure on the web.                                                                |
| Grey-on-grey "subtle" body text                        | Most often fails WCAG AA. Stay above 4.5:1 contrast.                                                           |
| `<br>` for spacing                                     | That's CSS's job. Use margin/padding.                                                                          |
| Overriding `:root` font-size with `px`                 | Silently breaks the reader's accessibility setting.                                                            |
| Hiding text until webfonts load                        | Penalizes slow connections to spare a font-swap. Use `font-display: swap` and a well-matched fallback instead. |

## Pressure patterns — diagnosing why type feels wrong

When something feels off but you can't say what, name the pressure and step
_down_ the ladder to where it originates. Brown's catalog, distilled:

### Pressure on the text block (typeface, size, measure, leading)

| Symptom                                        | Likely cause                                                                                     | First moves                                                                                       |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| **Too tight** — eye loses next line            | Line-height too small for the measure                                                            | Loosen line-height; or shrink font-size; or narrow the measure                                    |
| **Too loose** — words drift apart              | Default letter-spacing too tight (word spaces dominate); or line-height too tall for the measure | Tighten letter-spacing, reduce vertical margins; failing that, switch to a face designed for text |
| **Unwieldy** — type feels oversized, horsey    | Font size beyond the typeface's intended range; or tight margins compressing the block           | Reduce size, expand margins, or switch to a text-grade face                                       |
| **Weak / dull** — page feels flat              | Low-texture typeface, or weight too light                                                        | Choose a face with more active texture; bump weight; vary measure                                 |
| **Too light to read**                          | Display or all-purpose face used at body sizes                                                   | Switch to a body-text face                                                                        |
| **Renders poorly on Windows / coarse screens** | Face not built for low-res hinting                                                               | Use a screen-optimized cut (Reading Edge, optical sizes, ScreenSmart)                             |

### Pressure on alignment and rhythm

| Symptom                                               | Likely cause                                 | First moves                                                                                  |
| ----------------------------------------------------- | -------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **Rough rag** — long words break awkwardly            | No hyphenation on a narrow measure           | `hyphens: auto`; widen measure; use a condensed cut                                          |
| **Gappy / rivers** in justified text                  | Full justification without hyphenation       | Set ragged-right; or hyphenate if you must justify                                           |
| **Misaligned text blocks** — left edges don't line up | Container alignment ≠ text alignment         | Align the _text itself_ — adjust container widths, use negative margins to let one grow left |
| **Heading looks indented** vs body below it           | Default metric alignment ≠ optical alignment | Small negative `text-indent` on the heading; eyeball, don't measure                          |

### Pressure on the composition

| Symptom                                                   | Likely cause                                        | First moves                                                                          |
| --------------------------------------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Stretched** — too wide for its content                  | Layout outruns text-block measure                   | Cap max-width; bump body size; tighten white space; strengthen contrast              |
| **Empty** — text block alone in the void                  | Single column in a wide viewport                    | Bump font-size slightly, widen measure, add a background or border, consider columns |
| **Crowded / oppressive** — wall of small text             | Too many elements at one size with weak hierarchy   | Spread blocks, loosen spacing, reassess heading hierarchy                            |
| **Top-heavy** — h1 dominates h2/h3                        | Heading-to-subhead ratio too extreme                | Bring sizes closer; let weight and space do hierarchy work                           |
| **Clashing textures** — two faces fight                   | Palette mismatch (different rhythms or proportions) | Re-pair from the anchor; ensure shared rhythm                                        |
| **Distracting forms** — script/display face pulls the eye | Decorative face used near body text                 | Demote the face, widen margins around it, or swap to something quieter               |

**The ladder.** Brown's metaphor for fixing pressure: text-block decisions sit
at the bottom rung (typeface, size, measure, leading), composition decisions sit
at the top (margins, hierarchy, palette balance). Pressure at the composition
level usually points back to a text-block decision, which may point back to the
anchor typeface. _Climb down to the rung that caused the pressure; fix it there;
then re-evaluate every rung above._

## A workflow for a new project

1. **Read the text first.** Know what you're typesetting — voice, length,
   hierarchy, special cases.
2. **Identify the jobs.** Which blocks are body (setting), which are display
   (arranging), which are tabular/UI (calibrating)?
3. **Choose an anchor typeface.** Start with `system-ui`. If you swap in a
   webfont, evaluate it for sturdy shapes, even color, active texture — in that
   order.
4. **Set body type, mobile-first:** typeface → size → measure → leading. Use the
   familiar x-height method to pick a size.
5. **Build the type scale** from the body font-size and a ratio.
6. **Style headings** with size + weight + space only. No color yet.
7. **Check contrast** in light and dark modes. Adjust greys if needed.
8. **Evaluate at extremes** — 360px-wide phone, 1440px+ desktop, 200% browser
   zoom, with web fonts disabled (Reader Mode).
9. **Walk the ladder.** Any pressure you noticed? Locate it (text block /
   alignment / composition) and fix at the rung that caused it. Re-evaluate the
   rest.

## Closing test — four questions

Before shipping any typography change:

1. Does body text have a max-width that produces 45–75 character lines?
2. Does hierarchy work in greyscale? (Print the page in black-and-white.)
3. Does the page still work at 200% browser zoom?
4. **Pressure scan:** view the composition at narrow, medium, wide. Anything
   feel wrong? Name it, locate it on the ladder, fix it there.

If any answer is no, the typography isn't done.

## See also

- `examples.md` — concrete applications: forms, dashboards, marketing, data
  tables, dark mode, dyslexia-friendly settings.
- `references.md` — full bibliography (Butterick, Brown, Rutter, Santa Maria,
  Lupton, Spiekermann, Bringhurst) plus platform docs.
- `apple-hig` — for Apple-platform native UI typography (SF Pro, Dynamic Type).
- `laws-of-simplicity` — Law 1 (Reduce) and Law 10 (subtract the obvious) apply
  directly to type: cut weights, cut sizes, cut families.
- `clean-software-docs` — fluff-cutting in prose pairs naturally with type
  discipline; both serve reader respect.
