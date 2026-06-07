# Laws of Simplicity — Applied Examples

These translate Maeda's laws (originally written about consumer electronics,
design, and life) into the situations you actually encounter: code, APIs, UI,
docs, and process. Each entry pairs Maeda's own example with a software
analogue.

## Law 1 — Reduce (SHE: Shrink, Hide, Embody)

**Maeda's example.** The iPod. Apple kept stripping buttons until one click
wheel remained. The mirrored back makes the device _appear_ thinner than it is
(embody quality).

**Software analogues.**

- **Shrink a function signature.** A 9-parameter constructor → a `Config` struct
  with 3 required fields and sensible defaults; the surface is smaller, the call
  site lighter.
- **Hide a settings page.** A "Advanced" disclosure that defaults closed; the
  80% who don't need it never see it. (Hide, not delete.)
- **Embody after shrinking.** When you remove a verbose error code and replace
  it with one short message, _invest_ the remaining text — make it specific,
  actionable, human. A bare "Error" is reduction without embodiment, and it
  feels cheap.

**Anti-example.** Replacing a 5-step wizard with a single page that crams the
same 5 steps into one screen. That's not reduction — it's relocation.

## Law 2 — Organize (SLIP: Sort, Label, Integrate, Prioritize)

**Maeda's example.** SLIP-ing a to-do list with post-its: spread them out, find
clusters, label clusters, merge similar clusters, pull the vital few into a
"focus" set.

**Software analogues.**

- **Nav menu cleanup.** 23 menu items → write each on a post-it (or Figma
  sticky) → group → label groups → merge `Reports` and `Analytics` under one
  name → pull the 4 most-used items into a top-level "Today" group.
- **Settings page.** Group toggles by what they affect (Account / Notifications
  / Privacy / Advanced). The Pareto pull: surface the 3 that 80% of users
  actually touch.
- **Repository / package structure.** When `internal/handler/` has 30 flat
  files, SLIP them into `auth/`, `admin/`, `project/`, etc. — exactly the move
  described in the Observer project's layout convention.

**The "blurred gestalt" insight.** Sometimes the best grouping makes individual
items recede into a single perceived whole — like the iPod click wheel where the
four directional buttons and the center button melt into one control. Look for
places where four related controls could become one.

## Law 3 — Time (Shrink time, or hide/embody it)

**Maeda's example.** Progress bars. An Apple study found users perceive a task
as _faster_ when shown a progress bar — even if the actual elapsed time is
identical.

**Software analogues.**

- **Shrink time.** Optimistic UI updates: render the new state immediately while
  the request is in flight. Move work to a background job. Pre-compute.
- **Hide / embody time.** When you can't make it faster, make the wait
  tolerable: skeleton screens, progress bars with sub-steps, ambient progress
  indicators ("Saving…" → "Saved · 2s ago"). A frozen UI feels slower than a
  moving one even when it's literally faster.
- **Casino move (negative case).** Hiding time entirely — no save indicator, no
  last-modified timestamp — creates anxiety, not simplicity. People want to
  _see_ time flow.

**Rule of thumb.** If the wait is >1s and you can't shrink it, embody it. If the
wait is >10s, also tell the user what's happening underneath.

## Law 4 — Learn (BRAIN + RELATE-TRANSLATE-SURPRISE)

**Maeda's example.** The desktop metaphor (Xerox PARC, later Apple): RELATE to
the physical desk, TRANSLATE folders/trash into pixels, SURPRISE with copy-paste
and undo — things no physical desk can do.

**Software analogues.**

- **Library API design.** New library? Pick the closest known library's
  vocabulary (RELATE), map your concepts onto its mental model (TRANSLATE), then
  earn your existence by doing one thing it can't (SURPRISE).
- **Error messages.** BRAIN applied: state the basic problem, repeat the key
  fact in the action ("Email is invalid — fix the email field"), avoid
  desperation ("FATAL ERROR! CONTACT SUPPORT IMMEDIATELY"), inspire with an
  example of the correct input, repeat the rule in inline help.
- **Onboarding.** Repetition isn't lazy — Maeda watched a Swiss typography
  master give the same intro lecture each year and only on the third visit
  realized he was saying it _simpler_ each time. Your README's first paragraph
  should be saying the same thing as the docs landing page, just shorter.

**Watch out for.** The "surprise" step is culture-dependent. The original Mac
trash icon was unrecognizable to Japanese users who'd never seen a ribbed metal
trash can. Metaphors leak.

## Law 5 — Differences (rhythm)

**Maeda's example.** "Taa taa ti ti taa" — the rhythm of long, short, short,
long. Pure simplicity all the way through is boring; pure complexity is
exhausting. Good designs _alternate_.

**Software analogues.**

- **Page layouts.** A dashboard with 12 equally-weighted cards has no rhythm.
  Promote one to hero size, demote three to dense rows, and the eye knows where
  to start.
- **API surface.** A library where every function takes one argument and returns
  one value is simple but lifeless; a library where every function takes 6
  options is exhausting. The good ones alternate — terse for common cases,
  expressive when you need it.
- **Prose.** Long paragraph, short paragraph. Long sentence. Short. Then a list:
  - like this
  - because the rhythm changes
  - and the eye gets a rest.

**Rule of thumb.** Before you call something "simple," ask what complexity it
sits against. If the answer is "nothing," the simplicity won't read as
simplicity — it'll read as flat.

## Law 6 — Context (periphery is not peripheral)

**Maeda's example.** A Paris flat with white walls, white sushi plate, white
furniture — the food _tasted different_ because the ambient context framed it.
White space, ambient light, ambient sound: the background changes the
foreground.

**Software analogues.**

- **Empty states.** The background — what the page looks like _before_ it has
  content — sets the tone for every state after. A blank list with no empty
  state is colder than a blank list with a one-line "Nothing yet — add your
  first."
- **Page transitions and motion.** A spinner is foreground. A subtle background
  shift while a panel slides in is context — it tells you the system is alive
  without demanding attention.
- **Code review.** The PR diff is foreground. The CI status, the related ticket,
  the previous related PRs — that's the periphery. Reviewers who only read the
  diff miss the context that determines whether the change is right.

**The white space test.** "Don't write on this page." Maeda's literal challenge
— and most readers feel an urge to fill the blank. Resist the same urge in your
UI. Empty space invites attention to what's there.

## Law 7 — Emotion (more is better than less)

**Maeda's example.** Apple's iPod accessories: cases, skins, decals. The device
is cold, minimal, "nude electronics." Users immediately dress it. They want
emotion in their objects.

**Software analogues.**

- **Microcopy.** "404 Not Found" → "We looked everywhere. This page isn't here."
  One has a heartbeat, one doesn't. Both are technically correct.
- **Empty state illustrations.** Not decoration — emotional context. A friendly
  drawing in an empty state changes how users feel about the absence of data.
- **Animation, sound, haptics.** The "click" of a Razr phone. The "thunk" of a
  typewriter tab. The little bounce when you pull-to-refresh. These cost almost
  nothing technically and pay a lot in _aichaku_ — Japanese for "love-fit," the
  attachment users develop for objects that feel like they were made for them.

**Tension with Law 1.** Yes — Law 7 explicitly says it contradicts the
reductionist impulse of Law 1. Resolve it via "feel, and feel for": start by
being sensitive to your own emotional response to the design, then design for
the user's. _Form follows function_ gives way to _feeling follows form_.

## Law 8 — Trust (in simplicity we trust)

**Maeda's example.** _Omakase_ — "I leave it up to you" at a sushi bar. The chef
chooses; you eat. The simplicity is total, but it depends entirely on trust in
the master.

**Software analogues.**

- **Smart defaults.** Auto-saving documents, auto-detecting file format,
  recommending the next track — every one is a small _omakase_. They simplify by
  removing choices, but they only work if the recommendation is reliably good.
- **Undo as trust insurance.** Trust is fragile. _Undo_ is the price of asking
  users to trust your defaults. Email's "Undo Send" is the canonical move: we'll
  send instantly (simple), and you have 30 seconds to take it back (trust net).
- **The "Trust me" warning.** When a tool says "trust me, this is fine" without
  showing its work, users learn to distrust it. Show the receipt — surface what
  the system did, even when it acted on the user's behalf.

**The dial.** _How much do you need to know about the system?_ ↔ _How much does
the system know about you?_ Most "simple" experiences trade some of one for the
other. Be explicit about which side you're paying with.

## Law 9 — Failure (some things can never be made simple)

**Maeda's example.** A flower. Tax law. Distributed systems. Some domains have
irreducible complexity, and trying to flatten them produces dangerous
simplifications.

**Software analogues.**

- **Permission systems.** Dual-level RBAC (platform*role × project_role ×
  sensitivity flags — the Observer project's model) is \_less* simple than a
  single-role system, but the simpler model can't express what humanitarian work
  actually requires. Recognizing this is engineering maturity, not failure.
- **Date / time / timezones.** Every attempt to "just make it simple" produces
  bugs. Use a library; respect the complexity.
- **Internationalization.** Plurals in Russian. Right-to-left text. Cyrillic vs.
  Latin. You can simplify the API around it; you cannot simplify the problem.

**The return on failure (ROF).** When you've spent days trying to simplify
something and it's still complex, the answer might be "this is one of those
things." Stop, document why, and ship the necessary complexity well — rather
than a deceptively simple version that breaks.

## Law 10 — The One

**Subtract the obvious, add the meaningful.**

This is the closing pass. After all the other laws, ask: _what is the one thing
this is for?_ If three remaining elements support that one thing, they earn
their place. If two are decorative and one is load-bearing, you've found your
cuts.

For Observer specifically:

- A form view's "one thing" is usually "record this person's data correctly the
  first time." Anything that doesn't serve that — extra navigation, dense help
  text, decorative section dividers — is a cut.
- A report's "one thing" is usually "answer this donor's question without
  ambiguity." Anything that adds context without changing the answer is a cut.

## The three keys — applied

### Away (offload)

- Move CSV exports to a background job. The page stays light; the work happens
  far away.
- Use a CDN. Move the static asset far away, geographically.
- Server-render the first paint; hydrate later. The user sees content while the
  JS arrives from far away.

### Open (let others extend)

- A documented HTTP API beats a dozen built-in views you'll never have time to
  build.
- An export format (CSV, JSON) lets users do the analysis you'd otherwise have
  to build a screen for.
- A plugin point or webhook lets the ecosystem ship the long tail of
  integrations you don't have capacity for.

### Power (use less)

- Lazy-load. Don't fetch what you don't show.
- Cache aggressively at the edges; recompute only when the inputs change.
- For mobile/PWA: every megabyte you ship is paid for by every user's battery
  and data plan.

## A worked example: simplifying a "person" detail page

Suppose the page has: 47 fields in a single tall form, 6 tabs at the top, a
sidebar with audit history, a floating action button, a banner with the project
name, and a breadcrumb.

**Law 1 (Reduce).** Of the 47 fields, 12 are required, 22 are filled in <10% of
records, 13 are derived from others. Hide the 22 behind an "Additional details"
disclosure. Compute and read-only display the 13 derived. → 12 visible fields.

**Law 2 (Organize).** SLIP the 12: Identity (4), Contact (3), Household link
(2), Status (3). Label each group. Don't promote any one — they're all required.

**Law 3 (Time).** Auto-save on field blur. Show "Saved · 2s ago." The user no
longer feels the form as a long commitment.

**Law 6 (Context).** The audit sidebar is peripheral but valuable — keep it, but
collapse it by default so the foreground (the form) breathes.

**Law 7 (Emotion).** Replace the bare "Saved" with "Saved · 2s ago" and a subtle
check-fade. Tiny, but humans love acknowledgment.

**Law 8 (Trust).** Add inline validation. Add an "Undo" toast for destructive
actions. Trust is built on reversibility.

**Law 10.** What is the _one_ thing? Recording this person accurately. Banner
with project name? Cut — the user knows what project they're in. Floating action
button on a form page? Cut — its action is just "Save" which is already inline.
Breadcrumb? Keep — context. Six tabs? Reduce to three: Person, Cases, Documents.

Result: same data captured, half the screen weight, faster perceived save, fewer
mistakes.
