# Apple HIG — 1992 Roots

> Source: _Macintosh Human Interface Guidelines_, Apple Computer Inc.,
> Addison-Wesley, 1992 (ISBN 0-201-62216-5). Short quotes attributed by chapter.
> All other content paraphrased.

## Chapter 1 — The 12 Principles (Expanded)

### Metaphors

Ground new concepts in familiar real-world objects so users arrive with a ready
set of expectations. The Macintosh desktop, folders, and trash can are all
extensions of the same root metaphor — office life — and each new metaphor
should fit coherently within that frame. Crucially, a metaphor suggests a use
but need not replicate the physical limitations: a folder can hold far more than
paper ever could. Strike a balance between the metaphor's implied constraints
and the computer's actual capabilities.

### Direct Manipulation

Objects must remain visible while the user acts on them, and the impact of every
operation must appear immediately. Moving an icon, dragging a selection,
clicking to reposition a cursor — all show instant results without requiring the
user to imagine an intermediate state. "Animation, when used sparingly, is one
of the best ways to show a user that a requested action is being carried out."
(Ch. 1) Reserve animation for reassurance during lengthy operations, not
decoration.

### See-and-Point

Both core interaction paradigms share the same assumption: users can see what
they're doing and point at what they see. The noun-then-verb form governs both:

- _Select-then-act_: click an object, then choose a command from the menus.
- _Drag-to-target_: drag an object onto another object whose action is
  self-evident (e.g., drag to Trash).

For drag-to-target to work, objects must look like what they do in the real
world.

### Consistency

Consistency lets users transfer knowledge across applications. Ask five
questions: Is the product consistent (1) within itself, (2) with earlier
versions, (3) with Macintosh interface standards, (4) in its use of metaphors,
(5) with people's expectations? The hardest is the fifth, because audiences
vary. Weight consistency decisions against your specific target audience.

### WYSIWYG

Avoid hiding features behind abstract commands. Menus exist so users can see
their choices instead of memorizing command names. Where progressive disclosure
is needed (a "stepped interface"), reveal more choices through a predictable
mechanism rather than hiding them permanently. Screen and print output must
match; the user should never need to mentally project what a document will look
like printed.

### User Control

"Allow the user, not the computer, to initiate and control actions." (Ch. 1) The
computer must not remove choices in the name of protecting the user — that puts
the machine in control. When an action risks data loss, provide a warning alert
so the user can confirm and proceed; this protects without removing agency.

### Feedback & Dialog

Keep users informed at every step: confirm input was received, show progress for
long operations, explain why delays occur, and tell users how to escape the
current situation. Error messages must be plain-language and actionable — a raw
error code ("ID = 13") is useless; a message explaining what ran out of memory
and how to avoid it is helpful.

### Forgiveness

Build in reversibility so users feel safe exploring. "Create safety nets for
people so that they feel comfortable learning and using your product." (Ch. 1)
Always warn before irretrievable data loss. Importantly: if an app generates
frequent alert boxes, that is a signal of bad program design, not bad users —
good feedback and clear options should make errors rare.

### Perceived Stability

Users need stable reference points to cope with complexity. The desktop provides
a two-dimensional anchor; the menu bar, window borders, and consistent graphic
elements maintain the illusion of a persistent environment. When actions are
unavailable, dim them — never remove them. It is perception of stability that
matters, not strict physical permanence.

### Aesthetic Integrity

Keep display graphics simple and organized. Limit the number of elements and
their behaviors. Controls must look like their behavior: push buttons appear to
push in, sliders slide. Do not use arbitrary symbols whose meaning is clear only
to the designer; extend the graphic language through representation, analogy, or
metaphor. Give users control over their environment's appearance so they can
express individuality.

### Modelessness

Strive for modeless features that let users do whatever they want, whenever they
want. Acceptable mode categories are:

- Long-term modes (e.g., each application is itself a mode)
- Short-term "spring-loaded" modes (held via continuous user action, e.g.,
  Shift-extend)
- Alert modes (user must resolve an exceptional state before proceeding — keep
  minimal)
- Modes that emulate a familiar real-world modal situation (e.g., choosing a
  drawing tool)
- Modes that change only attributes, not behavior (e.g., bold text entry)
- Modes that block most operations to emphasize the exceptional state (e.g., a
  fatal-error dialog)

### Knowledge of Audience

Identifying and deeply understanding the target audience is among the most
important first steps in design. Create day-in-the-life scenarios, visit real
workplaces, analyze the steps users take for each task, and design to facilitate
those tasks. Involve real users throughout development — test prototypes with
people who match your audience description and listen to their feedback. Design
with people and their capabilities in mind, not computers and their
capabilities.

---

## Chapter 2 — Universal Access & Worldwide Compatibility

### Universal Access

Build accessibility in from the start rather than retrofitting it. Approximately
43 million Americans had some form of disability as of 1992. Design solutions by
disability category:

- **Physical disability** — provide both mouse and keyboard paths for every
  task; remove physical barriers (e.g., latched disk drives) that impede people
  with limited hand/arm use.
- **Visual disability** — support zoom/large-text features; never use color as
  the sole cue; make color choices user-configurable so people select what works
  for their vision.
- **Hearing disability** — supplement all auditory cues with visible
  equivalents; never rely on sound alone; allow system beep to be replaced with
  a visual flash.
- **Speech or language disability** — do not communicate directly with hardware
  in ways that block augmentative/assistive input software from emulating mouse
  and keyboard.
- **Seizure disorder** — avoid strobing or rapidly flickering screen elements;
  photosensitive users are at risk from repetitive flashing animations (modern
  standard: WCAG 2.1 §2.3 — no more than 3 flashes per second for large areas).

### Worldwide Compatibility

Plan for localization from day one; retrofitting script support is far more
costly. Key rules:

- Store all user-visible strings in resources so they can be translated without
  touching code.
- Budget 50% text growth when translated from U.S. English; dialog boxes must
  accommodate this.
- Support right-to-left layouts (Arabic, Hebrew); control alignment reverses
  with text direction.
- Avoid culture-specific graphics (holidays, seasons, animals with local
  symbolic meaning).
- Use Script Manager APIs for dates, numbers, and sorting — never hard-code
  Roman assumptions.
- Do not hard-code Chicago/Geneva as system fonts; non-Roman scripts require
  different fonts.

---

## Chapter 3 — Design Process

### The 80% Solution

Design to meet the needs of at least 80% of your users. Designing for power
users (the top 20%) typically produces an interface the majority cannot use.
Involving a broad range of users in the design process is the most reliable way
to find the 80% solution.

### Feature Cascade

Every feature adds size, slows execution, increases interface complexity, adds
documentation burden, and multiplies potential errors. Weigh each feature's
benefit against all those costs. Resist market-pressure temptations to add
features that aren't fully resourced.

### Managing Complexity

The best approach to easy-to-use software is keeping the design as simple as
possible. The challenge users want is solving their problems — not learning to
use your interface. Simplify wherever you can.

### Progressive Disclosure

Present the most common choices initially; hide advanced options behind a
predictable mechanism. The canonical pattern is a **More Choices** button in the
lower-left corner of a dialog box. Clicking it expands the dialog (growing
downward, not symmetrically) and relabels the button **Fewer Choices**. When the
user collapses the dialog, keep it in its expanded position — do not snap it
back.

### Preferences

A preference is a setting the user changes infrequently and that persists across
sessions. If users need to change a setting many times per work session,
implement it as a menu item or other easily accessible, modeless control — not a
preference. Avoid large preference dialogs stuffed with settings that are really
special cases of built-in behavior.

### Extending the Interface

Extend the standard interface only when a genuine need cannot be met by existing
elements. Four rules: (1) create new elements for entirely new features, (2)
modify existing elements minimally when they almost meet the need, (3) never
copy other platforms' UI elements or behaviors, (4) design extensions so they
convey meaning through representation, analogy, or metaphor — not arbitrary
imagery.

---

## Chapter 9 — Color

- **Design for black-and-white first**, then colorize. This guarantees the
  design works on all monitors and for users with color-deficient vision.
- **Never use color as the only distinguishing cue.** Always provide redundant
  cues: shape, label, position, or pattern.
- **Limit the number of colors.** Fewer colors mean less screen-table flashing
  and less visual clutter.
- **Colors look best against neutral gray.** Keep surrounding areas gray or
  black-and-white so accent colors pop.
- **Beware of light blue.** It is the hardest color to distinguish; avoid it for
  text, thin lines, and small shapes. Adjacent colors that differ only in the
  amount of blue are also problematic. Exception: blue is ideal for unobtrusive
  elements like grid lines.
- **Small objects need high contrast.** Color differences in small areas must be
  obvious, not subtle, especially when they convey significant information.
- **Color for categorization.** When using color to code information categories,
  limit color use elsewhere in the app. Offer users 4–7 distinct colors
  initially, with the ability to change or expand the set.

---

## Chapter 10 — Input Behaviors

### Mouse Actions

| Action       | Definition                                                                                                   |
| ------------ | ------------------------------------------------------------------------------------------------------------ |
| Click        | Press and release mouse button while stationary; effect is immediate.                                        |
| Double-click | Two rapid clicks in time and space; a shortcut, never the only path to an action.                            |
| Press        | Hold button down while stationary; repeats the effect of clicking (e.g., scroll arrow scrolls continuously). |
| Drag         | Press, move to new position, release; used for selecting, moving, resizing, or choosing menu items.          |

### Keyboard

Two key categories:

- **Character keys** — letters, numbers, punctuation, Space. Special
  non-printing characters: Enter (signals completion of a data entry area),
  Return (inserts line break; also dismisses dialog if default button exists),
  Tab (advances to next field or tab stop), Delete/Backspace (removes selection
  or preceding character), Clear (removes without Clipboard), Escape ("let me
  out" — cancels dialog or stops operation in progress).
- **Modifier keys** — alter interpretation of other keys or mouse actions:
  - **Shift** — uppercase/extend selection/constrain graphics movement.
  - **Caps Lock** — uppercase alphabetic only; no effect on symbol keys.
  - **Option** — international characters and special symbols; also modifies
    drag (e.g., copy on drag).
  - **Command** — keyboard equivalents for menu commands; not a character.
  - **Control** — reserved for terminal emulation and user-defined macro
    shortcuts.
- **Arrow keys** — move insertion point in text/arrays; fine-nudge selected
  objects in graphics (1 px). Shift+arrow extends selection. Never duplicate
  scroll-bar function.

### Pointer Feedback

The pointer changes shape only to convey meaningful information about available
actions or the current context — never randomly. Standard shapes: arrow (general
controls), I-beam (text insertion), crosshairs (drawing/stretching), plus sign
(array selection), wristwatch (lengthy operation in progress). For operations
taking more than a few seconds, supplement the wristwatch with a progress
indicator showing elapsed and total time.
