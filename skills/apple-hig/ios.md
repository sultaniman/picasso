# Apple HIG — iOS / iPadOS Components

> Reference: Apple Human Interface Guidelines (developer.apple.com/design) Use
> when working on iOS/iPadOS UIKit or SwiftUI.

---

### Navigation Bar

**When to use:** Primary navigation within a hierarchical flow (drill-down into
detail views). **When not to use:** Top-level navigation between app sections
(use tab bar); flat content without hierarchy. **Key rules:**

- Title: current screen's name, centered (iOS default) or leading (large title
  style)
- Large title collapses to standard title on scroll
- Back button is automatic in UINavigationController; label is the previous
  screen's title (trim if long)
- Trailing items: ≤ 2–3 actions, rightmost is primary
- System colors and fonts — don't customize navigation bar appearance unless
  branding requires it **Common mistakes:** Navigation bar for flat content;
  custom back button that breaks gesture navigation; more than 3 trailing items.

### Tab Bar

**When to use:** Top-level navigation between 2–5 independent sections of the
app. **When not to use:** More than 5 tabs; within a detail view (use nav bar
for navigation inside sections). **Key rules:**

- 2–5 tabs; iOS 18+ `UITabBarController` handles overflow automatically with a
  customizable sidebar/tab overflow
- Tab icons use SF Symbols; selected tab shows tint color
- Badges (red dot with number) for unread counts only — not for status
- Tab bar always visible when in a top-level section
- Do not use tab bar and sidebar simultaneously on iPhone **Common mistakes:**
  More than 5 visible tabs; hiding the tab bar in top-level views; using tabs
  for navigation within a section.

### Navigation Stack (Push/Pop)

**When to use:** Drill-down into detail — master list → item detail →
sub-detail. **When not to use:** Presenting unrelated content; switching between
independent sections. **Key rules:**

- Push: slides new view in from the right; pop: slides back from right to left
- Back gesture: swipe from left edge (system behavior — don't disable)
- Maximum depth: if you need more than 3–4 levels of hierarchy, reconsider the
  IA
- Each screen has a single focused purpose **Common mistakes:** Disabling
  swipe-back gesture; deep stacks that are difficult to navigate; pushing
  unrelated content.

### Search Bar

**When to use:** Filtering a long list of items within a screen. **When not to
use:** Global app search (use a dedicated search tab or scope); navigation.
**Key rules:**

- Integrate with `UISearchController`; results update live as user types
- Cancel button dismisses search and restores original list
- Scope bar (below search bar) for filtering by category when needed
- Placeholder text describes what is searchable **Common mistakes:** Search that
  only works on submit (not live); no Cancel button.

### Sheets (Bottom Sheet / Half Sheet)

**When to use:** Transient tasks that don't require full navigation context
(share sheet, settings for current item, form completion). **When not to use:**
Navigation; permanent information; replacing a full screen that should be
pushed. **Key rules:**

- Detents: `.medium` (half-height), `.large` (full-height), or custom via
  `.custom { _ in height }` / `.fraction(0.4)` (iOS 16+)
- Drag indicator at top center; user can dismiss by swiping down (unless
  `isModalInPresentation = true`)
- `isModalInPresentation = true` only when unsaved data would be lost on dismiss
  — always confirm before dismissing
- Don't nest sheets (sheet from a sheet) **Common mistakes:** Full-screen sheet
  when `.medium` would suffice; nested sheets; blocking dismissal without
  warning.

### Action Sheet

**When to use:** Presenting 3+ choices for an action, especially destructive
ones (delete, share options on iPhone). **When not to use:** 2 choices (use an
alert); non-action choices; on iPad (use a popover instead). **Key rules:**

- Anchored to the triggering control or bottom of screen on iPhone
- Destructive action: red text, positioned above Cancel
- Cancel always present and at the bottom
- On iPad: present `UIAlertController(.actionSheet)` via
  `popoverPresentationController` — **must set `sourceView`/`sourceRect` or
  `barButtonItem`**, otherwise crashes at runtime **Common mistakes:** Action
  sheets on iPad without popover; missing Cancel; destructive action at the top.

### Alert

**When to use:** Critical information requiring immediate user decision or
acknowledgement (irreversible action, error blocking progress). **When not to
use:** Informational updates; status; non-critical choices — use inline
feedback, banners, or toast. **Key rules:**

- Title: brief statement of the situation
- Message: explanation of consequence
- Buttons: ≤ 2 for alerts; 3+ choices go in an action sheet
- Destructive button: red text; Cancel: always present for reversible decisions
- Never use "OK" as a button label for a consequential action — use a
  descriptive verb **Common mistakes:** Alert for informational messages;
  "OK/Cancel" as labels; more than 2 buttons in an alert.

### List / Table View

**When to use:** Displaying a scrollable list of items — settings, messages,
contacts, any flat or grouped list. **When not to use:** Grid layout (use
collection view); very few items that fit without scrolling (use a static
stack). **Key rules:**

- Styles: plain (continuous), inset grouped (cards, modern), grouped (separated
  sections)
- Cell height: minimum 44pt; use dynamic height for variable content
- Swipe actions: leading (non-destructive, like "Mark Read"), trailing
  (destructive, like "Delete")
- Pull-to-refresh for content that updates
- Accessory views: disclosure indicator (→) for drill-down; checkmark for
  selection; detail button (ⓘ) for info **Common mistakes:** Cells shorter than
  44pt; swipe-to-delete as the only delete path; no empty state for empty lists.

### Collection View

**When to use:** Grid layouts, photo galleries, app grids, any 2D content
arrangement. **When not to use:** Simple linear lists (use table view); when
layout doesn't benefit from a grid. **Key rules:**

- Use compositional layout (`UICollectionViewCompositionalLayout`) for complex
  grids
- Cell size: consistent within a section; adapt for Dynamic Type and size
  classes
- Support selection with visual highlight; multi-select with checkmark badges
- Provide context menu on long press for quick actions **Common mistakes:**
  Fixed cell sizes that don't adapt to text size; no selection state.

### Toggle (Switch)

**When to use:** Binary on/off settings that take effect immediately. **When not
to use:** Settings that require confirmation before applying (use a button +
confirmation); non-boolean choices. **Key rules:**

- Label on the left; toggle on the right (in a table cell)
- Change takes effect immediately — no Save button needed
- Don't use for temporary/session state — use for persistent preferences
  **Common mistakes:** Toggle requiring a Save action; using toggle for
  multi-state choices.

### Slider

**When to use:** Continuous value selection within a range (volume, brightness,
opacity). **When not to use:** Discrete values with clear steps (use stepper);
values that need precision input (use a text field). **Key rules:**

- Horizontal orientation standard; vertical only for audio mixing contexts
- Show current value if precision matters
- Minimum and maximum icons/labels clarify the scale
- Touch target: thumb must be ≥ 44×44pt **Common mistakes:** No labels for
  min/max; thumb too small to hit accurately.

### Stepper

**When to use:** Incrementing/decrementing a discrete value in small steps
(quantity, number of copies, number of days). **When not to use:** Large ranges
(use slider); text input values (use text field). **Key rules:**

- Display current value in a label adjacent to the stepper — the stepper shows
  only + and -
- Disable the minus button at minimum value; disable the plus button at maximum
  **Common mistakes:** Stepper without a visible current-value label; stepper
  for continuous ranges.

### Picker / Date Picker

**When to use:** Selecting from a constrained set of values (date, time,
duration, or small custom list). **When not to use:** Large lists (use a table
view with search); free-form input (use text field). **Key rules:**

- Inline style (calendar) for date pickers in forms — no need to tap to expand
- Wheels style for time or duration; use compact style to save space
- Date picker defaults to current date; time picker defaults to current time
  **Common mistakes:** Wheel-style date picker taking up half the screen when
  inline would suffice.

### Segmented Control

**When to use:** Switching between 2–5 views or filter modes within a screen.
**When not to use:** Navigation between top-level sections (use tab bar); more
than 5 segments. **Key rules:**

- All segments visible simultaneously; no scrolling within the control
- Selection change is immediate
- Common placement: navigation bar (filter), above a list (view mode switch)
  **Common mistakes:** More than 5 segments; using in place of the tab bar.

### Toolbar

**When to use:** Surface secondary actions relevant to the current screen —
especially above the keyboard or at the bottom of a view. **When not to use:**
Primary navigation (use tab bar); actions that belong in the navigation bar.
**Key rules:**

- Bottom toolbar (`UIToolbar` / SwiftUI `.toolbar(items:)` with `.bottomBar`
  placement) for actions tied to the current content
- Keyboard toolbar: use
  `.toolbar { ToolbarItemGroup(placement: .keyboard) { ... } }` in SwiftUI for
  actions that appear above the keyboard
- Items use SF Symbols icons; include accessibility labels
- Don't put more than 5 items; use `.flexible Spacer` to separate groups
  **Common mistakes:** Putting nav-level actions in a bottom toolbar; toolbar
  items without accessibility labels.

### Context Menu

**When to use:** Long-press on a cell, image, or interactive element to reveal
contextual actions without leaving the current screen. **When not to use:**
Primary access to actions — context menus are discoverable shortcuts, not the
only path (WYSIWYG). **Key rules:**

- Use `UIContextMenuInteraction` (UIKit) or `.contextMenu { }` modifier
  (SwiftUI)
- Menu items use SF Symbols; destructive items use `.destructive` role (shown in
  red)
- Provide a preview of the item being acted on when appropriate
  (`UIContextMenuConfiguration.previewProvider`)
- Every action in a context menu must be reachable another way (tap, swipe,
  button) **Common mistakes:** Context-menu-only actions with no other access
  path; no item preview for media-heavy content.

### Gestures

**When to use:** Gestures are layered on top of tap-based interactions — never
the only path to an action. **When not to use:** Gesture-only actions (WYSIWYG
violation — always provide a tap alternative). **Key rules:**

- **Tap** — primary activation; must always work for any tappable element
- **Double-tap** — zoom in/toggle zoom level; don't use for primary actions
- **Long press** — reveal context menu; drag handle for reordering;
  secondary/discoverable only
- **Swipe left/right** — swipe actions in lists; navigate between pages; dismiss
  sheets
- **Swipe down** — dismiss sheets; pull-to-refresh at top of scroll views
- **Pinch** — zoom in/out on zoomable content
- Don't override system gestures; don't require gestures as the only path to an
  action **Common mistakes:** Gesture-only actions with no tap alternative;
  overriding swipe-back navigation.

### Safe Areas and Layout Margins

**When to use:** Always — safe areas are mandatory for correct layout on all
iPhone/iPad form factors. **When not to use:** N/A — always required. **Key
rules:**

- `safeAreaInsets` accounts for notch, Dynamic Island, home indicator, status
  bar
- Pin interactive controls to `safeAreaLayoutGuide`, not view edges
- Layout margins: use `viewController.view.readableContentGuide` for content
  width — on large iPads this adds significant horizontal inset (~100pt+) to
  keep text readable; for standard padding use `directionalLayoutMargins`
  (system default 8pt, but overridden to 16–20pt by `UIViewController`)
- Full-bleed backgrounds can extend behind safe areas; interactive controls must
  not **Common mistakes:** Fixed edge insets that don't account for safe areas;
  interactive content under the home indicator.

### Keyboard Avoidance

**When to use:** Any screen with text input that can be obscured by the software
keyboard. **When not to use:** N/A — always handle keyboard on screens with text
fields. **Key rules:**

- SwiftUI: add `.ignoresSafeArea(.keyboard)` to a `ScrollView` — the view
  automatically insets for the keyboard
- UIKit: observe `UIResponder.keyboardWillShowNotification` and adjust
  `UIScrollView.contentInset`, or use
  `UIScrollView.contentInsetAdjustmentBehavior`; never manually calculate
  keyboard height
- Active text field scrolls to stay visible
- "Done" or "Return" on keyboard dismisses it when appropriate
- Provide a visible dismiss path — don't rely on keyboard dismiss gesture alone
  **Common mistakes:** Text fields hidden behind keyboard; manual keyboard
  height calculations that break on different devices.

### Widget

**When to use:** Glanceable information the user wants to see without opening
the app (weather, next event, progress). **When not to use:** Interactive tasks
requiring app navigation; complex data entry. **Key rules:**

- Widgets are read-only — no text input, no scrolling within the widget
- Sizes: small (~155×155pt), medium (~329×155pt), large (~329×345pt) — support
  at least small and medium
- iPadOS also supports extra-large (~715×332pt); iOS 16+ adds Lock Screen widget
  families (circular, rectangular, inline)
- Update via WidgetKit timeline; no live network calls at render time
- Tapping a widget deep-links into the relevant app screen
- Padding: 16pt on all sides (small), 20pt (medium/large) **Common mistakes:**
  Widgets that try to be mini-apps; no deep link on tap; over-crammed content.

### iPadOS: Sidebar

**When to use:** Top-level navigation on iPad (equivalent of iPhone's tab bar).
**When not to use:** iPhone (use tab bar); within a detail view. **Key rules:**

- Collapsible via toolbar button; collapses to a slide-over or hides fully
- Source list style: same as macOS sidebar (disclosure triangles, sections)
- On iPad with Stage Manager: sidebar persists across window resize
- iOS 18+: `UITabBarController` automatically presents as sidebar on iPad
  (regular width) and tab bar on iPhone (compact) — no manual
  `UISplitViewController` required for new projects targeting iOS 18+
- iOS <18: pair with `UISplitViewController`; sidebar drives content in the
  detail column **Common mistakes:** Non-collapsible sidebar; sidebar that
  doesn't adapt to compact size class (should become tab bar on iPhone).

### iPadOS: Pointer Support

**When to use:** iPadOS apps should support the system pointer when a Magic
Keyboard or mouse is connected. **When not to use:** N/A — pointer support is
additive; touch must always work too. **Key rules:**

- Interactive elements automatically highlight on pointer hover (system
  behavior)
- Use `UIPointerInteraction` for custom hover effects on buttons and controls
- Pointer changes to IBeam over text, grab cursor over draggable elements
- Don't require the pointer for any action — all interactions must remain
  touch-accessible **Common mistakes:** No hover states; pointer-only actions.

### iPadOS: Stage Manager & Multitasking

**When to use:** All iPadOS apps should adapt to multiple window sizes and Stage
Manager. **When not to use:** N/A — adaptation is required, not optional. **Key
rules:**

- Use Auto Layout and size classes — never hardcode widths for iPad
- Compact width (≤ 414pt): show iPhone-like layout; Regular width: show iPad
  layout
- Support multiple windows (`UISceneDelegate` / SwiftUI `WindowGroup`) if the
  app concept supports it
- Don't disable multitasking unless your app is inherently single-window
  (camera, AR) **Common mistakes:** Fixed-width layouts that break in Stage
  Manager; no compact-width adaptation.
