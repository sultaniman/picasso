---
name: apple-hig
description:
  Use when designing, reviewing, or building Apple-platform UI (macOS, iOS,
  iPadOS) — navigation patterns, controls, layout, spacing, typography, system
  colors, SF Symbols, accessibility, or interaction patterns. Grounds decisions
  in the 1992 Macintosh HIG as primary authority.
---

# Apple HIG

> **Source:** _Macintosh Human Interface Guidelines_, Apple Computer, Inc.,
> Addison-Wesley, 1992. The primary authority for this skill; see `roots.md` for
> the full deep reference.

> **For macOS components:** `@apple-hig/macos.md` **For iOS/iPadOS components:**
> `@apple-hig/ios.md` **For 1992 HIG deep reference:** `@apple-hig/roots.md`

## The 12 Timeless Principles (1992 HIG)

The 1992 Macintosh HIG is the primary authority. These principles describe the
correct relationship between a human and a computer. Every design decision
should trace back to one or more of them.

| Principle                 | Core implication                                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Metaphors**             | Use familiar real-world concepts; extend where computer offers advantages; don't constrain by the metaphor's limits |
| **Direct Manipulation**   | Objects remain visible while acted upon; changes are immediate; animation shows action in progress                  |
| **See-and-Point**         | Noun-then-verb; all available actions visible in menus; no memorization required                                    |
| **Consistency**           | Visual + behavioral, within app, across apps, with user expectations; knowledge transfers freely                    |
| **WYSIWYG**               | No hidden features; no abstract commands; screen = output; don't force mental calculations                          |
| **User Control**          | User initiates and controls; computer does not "protect" by limiting choices; user is the agent                     |
| **Feedback & Dialog**     | Every action gets a response; explain delays; plain-language errors with a resolution path                          |
| **Forgiveness**           | Actions are reversible; users explore safely; undo always available; warn before irreversible                       |
| **Perceived Stability**   | Predictable, familiar environment; unavailable actions dimmed not removed; reference points constant                |
| **Aesthetic Integrity**   | Simple, organized, pleasant; graphics serve function; don't clutter; arbitrary symbols confuse                      |
| **Modelessness**          | Avoid modes; users do what they want when they want; modes need clear indicator and easy escape                     |
| **Knowledge of Audience** | Design for a specific user; scenarios, task analysis, prototypes, observation; not for yourself                     |

## Modern HIG — Accept vs Reject

**Accept** (extends the 1992 principles):

- **SF Symbols** — consistent icon language (Consistency principle)
- **Dynamic Type / system text styles** — WYSIWYG at all sizes; never hardcode
  font sizes
- **System semantic colors** — label/fill/background layers, Dark Mode support
- **44×44pt minimum touch targets** — User Control on iOS
- **Safe areas** — Perceived Stability on notched/Dynamic Island devices
- **VoiceOver labels, Reduce Motion** — Universal access (1992 HIG Chapter 2)
- **Proper modal hierarchy** — sheet vs popover vs alert (Modelessness)
- **Keyboard shortcuts on macOS** — efficiency for power users
- **NSVisualEffectView used subtly** — depth with restraint, not decoration

**Reject** (violates Aesthetic Integrity or User Control):

- **Liquid Glass / ultra-transparency everywhere** — decoration, not function
- **Corner radii >12pt for most controls** — squircle excess; obscures
  affordance
- **Heavy blur on every surface** — clutter; "keep graphics simple" (1992 Ch. 1)
- **Bouncy spring animations on every transition** — decoration; use only where
  Direct Manipulation requires physical response
- **Hero/oversized typography on every screen** — clutter; typography serves
  content, not spectacle
- **Hairline (0.5pt) borders as primary structure** — structure requires
  visibility
- **Floating elements without clear anchor** — violates Perceived Stability
- **Gradient overuse (decorative)** — arbitrary graphics confuse (1992 Ch. 1)
- **Neumorphism** — contradicts Direct Manipulation's clear visual affordance

## Platform Decision Rules

| Question                             | macOS                                                                         | iOS / iPadOS                            |
| ------------------------------------ | ----------------------------------------------------------------------------- | --------------------------------------- |
| Navigate between sections?           | Sidebar (source list) or toolbar tabs                                         | Tab bar or navigation stack             |
| Present transient contextual action? | Popover anchored to control                                                   | Popover (iPad) or action sheet (iPhone) |
| Present task requiring completion?   | Sheet (non-resizable) or panel                                                | Sheet with detents (.medium / .large)   |
| Present destructive confirmation?    | Alert: Cancel + Destructive buttons                                           | Alert or action sheet                   |
| Surface persistent tools?            | Toolbar (below title bar)                                                     | Toolbar (above keyboard) or nav bar     |
| When to use a modal view?            | Only when task requires full attention and is short-lived                     | Same — never modal for main navigation  |
| Sidebar vs Inspector?                | Sidebar: navigation/source; Inspector: attributes of selection                | No direct equivalent — use form sheets  |
| Go beyond system components?         | Only when system component cannot express the concept; document the deviation | Same                                    |

## Quick Reference

### Spacing

Base unit: **4pt**. Common multiples: 4, 8, 12, 16, 20, 24, 32, 44, 64.

### Typography (SF Pro)

| Style       | Size | Weight   | Role                          |
| ----------- | ---- | -------- | ----------------------------- |
| Large Title | 34pt | Regular  | Top-level screen titles (iOS) |
| Title 1     | 28pt | Regular  | Primary headings              |
| Title 2     | 22pt | Regular  | Section headings              |
| Title 3     | 20pt | Regular  | Subsection headings           |
| Headline    | 17pt | Semibold | Content headings              |
| Body        | 17pt | Regular  | Primary content               |
| Callout     | 16pt | Regular  | Secondary content             |
| Subheadline | 15pt | Regular  | Supporting text               |
| Footnote    | 13pt | Regular  | Captions, supplemental        |
| Caption 1   | 12pt | Regular  | Labels, metadata              |
| Caption 2   | 11pt | Regular  | Smallest readable text        |

SF Pro Text for ≤19pt; SF Pro Display for ≥20pt. Always use Dynamic Type — never
hardcode sizes.

### System Color Semantics

| Token                              | Use                                                         |
| ---------------------------------- | ----------------------------------------------------------- |
| `label`                            | Primary text                                                |
| `secondaryLabel`                   | Supporting text                                             |
| `tertiaryLabel`                    | Tertiary info (timestamps, third-level labels)              |
| `quaternaryLabel`                  | Disabled text                                               |
| `placeholderText`                  | Text field placeholder text                                 |
| `systemFill`                       | Thin translucent fill — selected rows, control highlights   |
| `secondarySystemFill`              | Grouped content fill                                        |
| `systemBackground`                 | Window/view background                                      |
| `secondarySystemBackground`        | Grouped/card background                                     |
| `tertiarySystemBackground`         | Inset grouped content                                       |
| `separator`                        | Divider lines                                               |
| `opaqueSeparator`                  | Dividers requiring opacity                                  |
| `tintColor` / `.accentColor`       | Primary interactive color — buttons, links, selected states |
| `systemGroupedBackground`          | Parent background for grouped/settings-style views          |
| `secondarySystemGroupedBackground` | Row/cell background inside grouped views                    |

### Control Sizes

**macOS:** Large, Regular (default), Small, Mini **iOS:** Default (44pt height),
Small, Mini (SwiftUI only — UIKit does not expose Mini for most controls)

**Touch target minimum (iOS):** 44×44pt — even if visual size is smaller, the
hit area must reach 44×44pt. **macOS:** No fixed minimum; aim for ≥ 16×16pt.

## Common Mistakes

- **Alert for non-critical info** → use inline feedback, banner, or status bar —
  alerts interrupt workflow
- **Custom navigation when system nav suffices** → fight the framework, lose;
  users trust system patterns
- **Fixed font sizes** → always use Dynamic Type; users set their own preferred
  size
- **Unlabeled icon-only buttons** → always provide `accessibilityLabel`
  (VoiceOver) and tooltip (macOS)
- **Wrong modal choice** → sheet for reversible tasks; full-screen cover for
  immersive; alert only for decisions requiring immediate response
- **Ignoring safe areas** → content clips at notch or Dynamic Island
- **Frequent alert boxes** → 1992 HIG Ch. 1: "frequent alert boxes are a good
  indication that something is wrong with the program design"
- **Modes without clear indicator** → if a mode is necessary, show it clearly
  near the affected object and make escape trivial
