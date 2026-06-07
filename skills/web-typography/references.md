# References

## Primary sources (the two anchors)

**Matthew Butterick — _Practical Typography_** (practicaltypography.com,
2010–ongoing). Free, online, screen-native. Opinionated and immediately
practical. Butterick designs fonts and writes software; his perspective is
exactly the one you want for web work. The site itself is a typography demo. The
single best recommendation for engineers and designers setting type on the web.

**Tim Brown — _Flexible Typesetting_** (A Book Apart No. 27, 2018, ~205 pp.).
The framework for setting type on a medium that flexes. Brown's central concept
is **pressure** — the interdependent relationships between typeface, font size,
measure, and line spacing, and how the web disrupts them. Six chapters: _What Is
Typesetting?_ (introduces pressure and the three jobs — setting, arranging,
calibrating), _Preparing Text and Code_, _Selecting Typefaces_ (the anchor
typeface; sturdy shapes, even color, active texture), _Shaping Text Blocks_
(familiar x-height method, modular scale, CSS locks for dynamic leading),
_Crafting Compositions_, _Relieving Pressure_ (a pattern language for diagnosing
what's wrong). Brown created `modularscale.com` and contributed to `utopia.fyi`.

## Strong web-specific companions

| Book                               | Author            | Year | Angle                                                                       |
| ---------------------------------- | ----------------- | ---- | --------------------------------------------------------------------------- |
| _On Web Typography_                | Jason Santa Maria | 2014 | A Book Apart — short, designer-friendly intro                               |
| _Web Typography_                   | Richard Rutter    | 2017 | Self-published; explicitly translates Bringhurst into CSS — the bridge book |
| _Designing for the Web_            | Mark Boulton      | 2009 | Older but still relevant; grid + type fundamentals for web                  |
| _The Elements of Content Strategy_ | Erin Kissane      | 2011 | Adjacent — content shape determines type needs                              |

## Foundational / general typography (print canon, useful as anchor)

| Book                                            | Author                | Year                                     | Notes                                                                                                                                          |
| ----------------------------------------------- | --------------------- | ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| _The Elements of Typographic Style_             | Robert Bringhurst     | 1992 (rev. 1996, 2002, 2004, 2008, 2013) | "The typographer's bible." Philosophical anchor for all the above. Mostly print-oriented but principles transfer.                              |
| _Thinking with Type_                            | Ellen Lupton          | 2004 (rev. 2010)                         | Most accessible academic intro. Free companion: **thinkingwithtype.com**                                                                       |
| _Stop Stealing Sheep & Find Out How Type Works_ | Erik Spiekermann      | 1993 (3rd ed. 2014)                      | System-thinking lens — Spiekermann co-designed Meta, FF Info; perspective maps directly to UI design tokens. Adobe hosts the 3rd ed. **free**. |
| _Detail in Typography_                          | Jost Hochuli          | 1987 (English 2008)                      | Microtypography — letterspacing, wordspacing, kerning. Very short, very precise.                                                               |
| _Designing Type_                                | Karen Cheng           | 2005                                     | How letterforms work — useful for evaluating typefaces.                                                                                        |
| _Notes on the Synthesis of Form_                | Christopher Alexander | 1964                                     | Adjacent — pattern thinking. Cross-referenced by Maeda's _Laws of Simplicity_.                                                                 |

## Modernist / classical anchors (read for principles, not specifics)

- **Jan Tschichold — _The New Typography_** (1928). Modernist foundation.
- **Jan Tschichold — _Treasury of Alphabets and Lettering_** (1952).
- **Josef Müller-Brockmann — _Grid Systems in Graphic Design_** (1981).
  Swiss-grid practitioner's reference.
- **Emil Ruder — _Typography: A Manual of Design_** (1967). Basel School
  pedagogy.

## Platform / vendor authorities (current, not books)

These are the canonical references for UI typography on specific platforms —
keep them bookmarked:

| Platform                       | Resource                                                                                                       |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Apple platforms                | _Human Interface Guidelines — Typography_ — `developer.apple.com/design/human-interface-guidelines/typography` |
| Material Design (Android, web) | _Material 3 — Typography_ — `m3.material.io/styles/typography`                                                 |
| Microsoft Fluent               | _Fluent UI — Typography_ — `developer.microsoft.com/fluentui`                                                  |
| Web standards                  | **web.dev** typography and font sections; **MDN** CSS Fonts module reference                                   |
| Variable fonts                 | `v-fonts.com` — catalog and live demos                                                                         |
| Font services                  | Google Fonts (`fonts.google.com`), Adobe Fonts, Fontshare (free), Use & Modify (free)                          |

## Free / authorized PDFs and online editions

| Source                                              | Where                                                | Notes                                                                         |
| --------------------------------------------------- | ---------------------------------------------------- | ----------------------------------------------------------------------------- |
| Butterick — _Practical Typography_                  | practicaltypography.com                              | Full content free; pay-what-you-want for the PDF                              |
| Lupton — _Thinking with Type_                       | thinkingwithtype.com                                 | Author-maintained companion site with the full content                        |
| Spiekermann — _Stop Stealing Sheep_ (3rd ed.)       | Adobe Type — search "Stop Stealing Sheep Adobe PDF"  | Publisher-authorized free PDF                                                 |
| Reichenstein essay — _Web Design is 95% Typography_ | ia.net/topics/the-web-is-all-about-typography-period | The foundational essay                                                        |
| Robin Rendle — _The Type Guide_                     | typographyguide.com                                  | Free curated learning                                                         |
| **No free version (paid only):**                    |                                                      | Bringhurst, Brown, Rutter, Santa Maria, Hochuli, Tschichold, Müller-Brockmann |

Do not link to unauthorized scans.

## Tooling

| Tool                                                                            | Purpose                                                    |
| ------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| **Modular Scale** — modularscale.com                                            | Generate type-scale steps from a base size and a ratio     |
| **Utopia** — utopia.fyi                                                         | Fluid type and space calculators with `clamp()` output     |
| **Type Scale** — typescale.com                                                  | Visual type-scale playground                               |
| **WhatTheFont** — myfonts.com/WhatTheFont                                       | Identify a typeface from an image                          |
| **Fontdrop** — fontdrop.info                                                    | Inspect any font file's metrics, glyphs, OpenType features |
| **Fonts in Use** — fontsinuse.com                                               | Curated catalog of typography in the wild                  |
| **Variable Fonts** — v-fonts.com                                                | Catalog with live axis controls                            |
| **Contrast checkers** — `webaim.org/resources/contrastchecker`, Chrome DevTools | WCAG AA/AAA verification                                   |
| **Accessibility** — axe DevTools, Lighthouse                                    | Audit type-related a11y issues                             |

## Recommended typefaces (free, screen-tuned)

For UI / body / headings on the web, these are safe defaults:

| Family                             | Designer                          | License                       | Notes                                                                        |
| ---------------------------------- | --------------------------------- | ----------------------------- | ---------------------------------------------------------------------------- |
| **System UI stack**                | Various                           | System                        | `system-ui, -apple-system, "Segoe UI", sans-serif` — free, fast, OS-tuned    |
| **Inter**                          | Rasmus Andersson                  | OFL                           | Designed for screens. Variable. Most-used modern UI sans.                    |
| **IBM Plex Sans / Serif / Mono**   | IBM, Bold Monday                  | OFL                           | Distinctive corporate face; complete family                                  |
| **Source Sans 3 / Source Serif 4** | Adobe                             | OFL                           | Adobe's open family; well-hinted                                             |
| **Charter**                        | Matthew Carter                    | Public-domain-ish (Bitstream) | Drawn for laser printers in 1987; renders beautifully on screen at body size |
| **JetBrains Mono**                 | JetBrains                         | OFL                           | Excellent monospace for code                                                 |
| **Recursive**                      | Stephen Nixon / Arrow Type        | OFL                           | Variable family that flexes between sans, mono, casual                       |
| **Fraunces**                       | Phaedra Charles & Flavia Zimbardi | OFL                           | Variable display serif; modern, characterful                                 |
| **Public Sans**                    | US Web Design System              | OFL                           | Conservative, accessible, drawn for civic UI                                 |

For commercial work where a distinctive face matters: **Fontshare** (free, by
Indian Type Foundry), **Use & Modify** (curated open fonts), or commercial
foundries (**Klim**, **Grilli**, **Pangram Pangram**, **Lineto**).

## Quick scan: which book for which question

| Question                                              | Best source                                                     |
| ----------------------------------------------------- | --------------------------------------------------------------- |
| What size, leading, and measure should body text use? | Butterick — _Typography in Ten Minutes_                         |
| How do I build a responsive type scale?               | Brown — _Flexible Typesetting_; utopia.fyi                      |
| How does Bringhurst's measure rule translate to CSS?  | Rutter — _Web Typography_                                       |
| How do I pick a typeface?                             | Butterick — _Web fonts_ chapter; Lupton — _Thinking with Type_  |
| What's the right `font-display` value?                | web.dev — Font best practices                                   |
| How do I subset a web font?                           | web.dev; Glyphhanger CLI                                        |
| What does "good" type even look like?                 | Spiekermann — _Stop Stealing Sheep_; Fonts in Use               |
| What about non-Latin scripts?                         | Google Fonts knowledge base; Khaled Hosny's Amiri docs (Arabic) |

## Where this skill applies less well

- **Print typography** — most rules carry, but print has its own concerns (CMYK,
  paper stock, ink spread, optical sizing for physical print). Reach for
  Bringhurst directly.
- **E-ink devices** — different rendering model (no anti-aliasing, low refresh).
  Kindle / reMarkable have their own guidelines.
- **Cross-platform native apps** — defer to platform-specific guidance
  (`apple-hig`, Material Design) for SF Pro, Roboto, etc., where the platform's
  type system already encodes most decisions.

## Cross-skill pointers

| When you're working on…            | Use alongside web-typography                                                                       |
| ---------------------------------- | -------------------------------------------------------------------------------------------------- |
| Apple-platform native UI           | `apple-hig` — SF Pro, Dynamic Type, Apple-specific tracking tables                                 |
| Cutting type to find hierarchy     | `laws-of-simplicity` — Law 1 (Reduce), Law 5 (rhythm: simple ↔ complex), Law 10 (subtract obvious) |
| Writing the actual words being set | `technical-writing` (Zinsser) or `clean-software-docs` for engineering prose                       |
| Reviewing UI copy for fluff        | `fluff-scan` — pairs naturally with type discipline                                                |
| Choosing between visual mockups    | `mockup-driven-design-exploration` — uses type as one tie-breaker                                  |
| Building React components          | `modern-react` — for the implementation side once type is decided                                  |
