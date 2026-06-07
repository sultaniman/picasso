# Web Typography — Applied Examples

Concrete applications by surface type. Each section shows the typography
decisions, the reasoning, and the trade-offs.

## Forms

Forms are mostly type — labels, inputs, helper text, errors. They get cluttered
fast.

**Settings that work for most forms:**

```css
.form {
  font-family:
    system-ui,
    -apple-system,
    "Segoe UI",
    sans-serif;
  font-size: 16px; /* 16+ prevents iOS Safari zoom on focus */
  line-height: 1.5;
}

.form label {
  font-size: 0.875rem;
  font-weight: 500;
  color: hsl(220 10% 30%);
}
.form input {
  font-size: 1rem;
  padding: 0.625rem 0.75rem;
  line-height: 1.4;
}
.form .helper {
  font-size: 0.8125rem;
  color: hsl(220 10% 45%);
  margin-top: 0.25rem;
}
.form .error {
  font-size: 0.8125rem;
  color: hsl(0 70% 45%);
  margin-top: 0.25rem;
}
```

**Why these choices:**

- **Input 16px:** iOS Safari zooms the viewport when a focused input is < 16px.
  Always 16+ for inputs.
- **Label 14px (0.875rem):** smaller than the input it labels — visually
  subordinate, lets the input dominate.
- **Helper/error at 13px:** secondary information, but never below 13. Below
  that it's hostile.
- **Line-height 1.4 on the input:** tighter than body because the input is a
  single line.
- **Error in a saturated red, label in a desaturated dark grey:** color carries
  semantic weight (red = problem), greys carry hierarchy.

**Tabular numerals for numeric inputs** (so digits don't shift width as the user
types):

```css
.form input[type="number"],
.form input[inputmode="numeric"] {
  font-variant-numeric: tabular-nums;
}
```

## Dashboards and data tables

Dashboards live or die by typography. The data is the content; everything else
supports it.

```css
.table {
  font-size: 14px; /* dense */
  font-variant-numeric: tabular-nums; /* digits align */
  line-height: 1.4;
}

.table th {
  font-weight: 600;
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: hsl(220 10% 45%);
}
.table td {
  font-weight: 400;
  color: hsl(220 15% 20%);
}

.table .num {
  text-align: right;
  font-feature-settings: "tnum" 1;
}
.table .total {
  font-weight: 600;
}
```

**Why:**

- **14px body in dashboards** is acceptable (not for prose) because users scan,
  not read.
- **`tabular-nums` is non-negotiable** for any column of numbers. Without it,
  "1,234.56" wobbles as digits change.
- **Tiny uppercase headers with letter-spacing:** the "small caps" convention
  reads as metadata, not content. Use sparingly.
- **Right-align numeric columns** so digits stack. Left-align text.
- **Weight, not color, for totals.** Totals read as more important even in
  greyscale.

**For sparkline / metric labels:**

```css
.metric-label {
  font-size: 11px;
  text-transform: uppercase;
  letter-spacing: 0.06em;
  font-weight: 500;
  color: hsl(220 10% 50%);
}
.metric-value {
  font-size: 28px;
  font-weight: 600;
  font-variant-numeric: tabular-nums;
  line-height: 1;
  letter-spacing: -0.01em;
}
```

Large numerals get _negative_ letter-spacing because at display sizes the
default tracking looks loose.

## Long-form prose (articles, docs, ADRs)

The opposite of a dashboard. Generous everything.

```css
.prose {
  font-family: Charter, Georgia, "Bitstream Charter", serif;
  font-size: 1.125rem; /* 18px */
  line-height: 1.7;
  max-width: 65ch;
  color: hsl(220 15% 15%);
}

.prose h1 {
  font-size: 2.5rem;
  line-height: 1.1;
  margin-top: 0;
  margin-bottom: 1.5rem;
  letter-spacing: -0.015em;
}
.prose h2 {
  font-size: 1.75rem;
  line-height: 1.2;
  margin-top: 3rem;
  margin-bottom: 0.75rem;
}
.prose h3 {
  font-size: 1.25rem;
  line-height: 1.3;
  margin-top: 2rem;
  margin-bottom: 0.5rem;
}
.prose p {
  margin-block: 0 1em;
}
.prose p + p {
  text-indent: 1.5em;
  margin-top: 0;
} /* book-style */

.prose blockquote {
  border-left: 2px solid currentColor;
  padding-left: 1rem;
  color: hsl(220 10% 35%);
  font-style: italic;
}
```

**Why:**

- **Serif for long-form** is a defensible choice on screen now that high-DPI
  displays render serifs cleanly. Charter and Georgia were drawn for screen.
- **18px / 1.7 leading / 65ch:** the Butterick triangle. Readers settle in.
- **Margin-top on h2 much larger than margin-bottom:** the heading is more
  attached to the section _below_ than the section above.
- **Indented continuation paragraphs:** optional book convention — saves
  vertical space and visually groups text. Works for editorial; skip for
  technical docs.

## Marketing / hero pages

Different rhythm — bigger swings, more contrast.

```css
.hero h1 {
  font-size: clamp(2.5rem, 6vw, 5rem); /* fluid */
  line-height: 1.05;
  letter-spacing: -0.02em; /* tighten at display sizes */
  font-weight: 700;
  max-width: 18ch; /* short measure for hero */
  text-wrap: balance; /* even line breaks */
}

.hero .lede {
  font-size: clamp(1.125rem, 2vw, 1.5rem);
  line-height: 1.5;
  max-width: 50ch;
  color: hsl(220 10% 40%);
}
```

**Why:**

- **`clamp()` for fluid size:** scales smoothly between phone and desktop
  without breakpoints.
- **Negative tracking at display sizes:** big text looks loose with default
  tracking. Tighten by 1–2%.
- **Short `max-width` (18ch) on hero h1:** two-line headlines read more
  decisively than one impossibly-long line.
- **`text-wrap: balance`:** even line breaks across the title. Currently
  Chrome + Safari; gracefully ignored elsewhere.
- **Lede in a lighter weight and lighter color:** subordinated but still
  prominent.

## Buttons and CTAs

```css
.btn {
  font-family: inherit;
  font-size: 0.9375rem; /* 15px — slightly under body */
  font-weight: 500;
  line-height: 1; /* tight inside a button */
  letter-spacing: 0;
  padding: 0.625rem 1rem;
}

.btn--lg {
  font-size: 1rem;
  padding: 0.875rem 1.5rem;
}
.btn--sm {
  font-size: 0.875rem;
  padding: 0.5rem 0.75rem;
}
```

**Why:**

- **`line-height: 1` inside a button:** the box defines vertical space via
  padding; line-height inside would fight it.
- **Weight 500, not 700:** UI buttons read as actions, not headings. Bold
  buttons are aggressive.
- **No uppercase by default.** Uppercase reduces readability and dates fast. Use
  sparingly (e.g., a small "ENTERPRISE" badge).

## Dark mode

Dark-mode typography needs adjustment, not a simple color flip.

```css
@media (prefers-color-scheme: dark) {
  .prose {
    color: hsl(220 15% 88%); /* not pure white — fatigues */
    background: hsl(220 15% 10%);
  }
  .prose .helper {
    color: hsl(220 10% 65%);
  }

  /* Reduce font-weight by ~50: dark-on-light text looks heavier */
  .prose {
    font-weight: 380;
  } /* if using variable font */
  /* Or: */
  .prose {
    font-weight: 400;
  }
  .prose strong {
    font-weight: 600;
  } /* not 700 — too heavy on dark */
}
```

**Why:**

- **Pure white on pure black is hostile.** The high contrast causes "halation" —
  letters bloom and blur. Use off-white (88–92% lightness) on near-black.
- **Reduce weight in dark mode.** A 400-weight glyph reads heavier on dark
  backgrounds. Variable fonts make this easy (`font-weight: 380`). With static
  fonts, downshift `<strong>` from 700 to 600.
- **Saturated greys.** A perfectly neutral grey looks dead on dark mode. Add
  5–10% saturation toward blue or warm.

## Internationalization

Different languages need different typography.

**Cyrillic and Latin in one site (Russian + English):**

```css
@font-face {
  font-family: "Inter";
  src: url("inter-latin.woff2") format("woff2");
  unicode-range: U+0000-024F; /* Latin + extended */
}
@font-face {
  font-family: "Inter";
  src: url("inter-cyrillic.woff2") format("woff2");
  unicode-range: U+0400-04FF; /* Cyrillic */
}
```

The browser downloads only the subset it needs per page.

**For Kyrgyz (Latin transliteration):** standard Latin subset covers it. For
Cyrillic Kyrgyz, the Cyrillic subset above is enough — no special characters
beyond Russian.

**Right-to-left (Arabic, Hebrew):**

- Use logical properties: `margin-inline-start`, not `margin-left`.
- Set `dir="rtl"` on the root.
- Most modern type families ship RTL-capable subsets; test rendering before
  shipping.

**CJK (Chinese, Japanese, Korean):**

- File sizes are large (thousands of glyphs) — system fonts are usually the
  right choice unless brand-critical.
- Line-height needs to be larger (1.6–1.8) — ideographs are tall.
- Don't justify CJK on the web; the browser justification engine handles it
  badly.

## Accessibility — Dynamic Type / browser font-size

```css
:root {
  font-size: 100%;
} /* honor the user's preference */
body {
  font-size: 1rem;
  line-height: 1.5;
}
/* never: html { font-size: 16px; } — that overrides the user */
```

**Why:** users who've set a 20px default font-size in their browser have done so
for a reason (often vision). `100%` lets that propagate. `16px` overrides their
accessibility setting silently.

**Testing:** in Chrome / Firefox, set the page zoom to 200%. The page should
reflow, not clip. Run an axe or Lighthouse pass for contrast.

**For dyslexic readers:**

- Leading at 1.6–1.8.
- Letter-spacing +0.02 to +0.05em on body.
- Avoid pure justification.
- Avoid italic for body text.
- Off-white background (`hsl(40 30% 96%)`) reads more easily than pure white for
  some readers.

## A worked example: simplifying a "noisy" admin UI

Before: a settings page where every label is bold, three font sizes are used
inconsistently, sub-labels are 11px in pale grey, line-height is 1.2, and the
page reads as a wall of small text.

**Type pass:**

1. **Body to 15px with line-height 1.5.** Up from 13px / 1.2. The page now
   breathes.
2. **One scale:** 12, 14, 15, 18, 24. Five sizes total, replacing the eight that
   crept in.
3. **Labels at 14px, weight 500.** Down from 14px / 700. Bold-everywhere reads
   as noise.
4. **Sub-labels at 13px (was 11px), color `hsl(220 10% 45%)` (was a
   barely-visible pale grey).** Contrast goes from 2.8:1 (fails AA) to 5.1:1
   (passes AA).
5. **`tabular-nums` on every numeric column.** Digits stop wobbling.
6. **`max-width: 60ch` on the section descriptions.** Body text no longer runs
   the full 1200px width.

No new font loaded. No new color introduced. Just type discipline.
