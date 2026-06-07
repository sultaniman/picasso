# Apple HIG — macOS Components

> Reference: Apple Human Interface Guidelines (developer.apple.com/design) +
> 1992 Macintosh HIG Use when working on macOS AppKit or SwiftUI mac idiom.

---

### Document Window

**When to use:** Primary workspace for a document-based app (text editor, image
editor, code editor). **When not to use:** Non-document apps (utilities,
preferences, system tools) — use standard window without document semantics.
**Key rules:**

- Title bar shows document name; set `window.isDocumentEdited = true` (AppKit —
  shows dot in close button) or mark `@Environment(\.undoManager)` dirty
  (SwiftUI) for unsaved changes
- Standard traffic-light controls (close, minimize, zoom) must always be present
  and functional
- Full-screen button appears in title bar; support it unless the app is truly
  incompatible with full-screen
- Minimum window size should allow the app to be usable, not just visible
  **Common mistakes:** Hiding or disabling traffic-light buttons; forgetting to
  handle unsaved-changes state.

### Utility Window / Panel

**When to use:** Floating tools or inspectors that stay visible while the user
works in document windows (tool palettes, find/replace, color picker). **When
not to use:** Primary content; anything requiring modal focus. **Key rules:**

- Utility windows float above document windows but yield to dialogs
- Use `.utilityPanel` window style; smaller title bar
- Close when the app goes to background unless the user has explicitly pinned it
- Don't put primary actions here — only auxiliary tools **Common mistakes:**
  Making panels modal; putting critical workflow steps in a utility window.

### HUD (Heads-Up Display)

**When to use:** Transient overlay of controls during a mode (full-screen video
playback, slideshow controls). **When not to use:** Permanent UI; anything the
user needs to find reliably. **Key rules:**

- Dark translucent background (approved exception to "avoid heavy blur")
- Auto-dismiss on inactivity; re-appear on mouse move
- Minimal controls only — this is a HUD, not a panel **Common mistakes:** Using
  HUD style outside full-screen/immersive contexts.

### Toolbar

**When to use:** Frequent actions in a document or main window; actions the user
performs many times per session. **When not to use:** Infrequent or destructive
actions (put those in menus); navigation between sections (use sidebar). **Key
rules:**

- Users can customize the toolbar (show/hide, rearrange items)
- Provide a default toolbar configuration that covers the 80% use case
- Items have both icon and label; label can be hidden by user preference
- Separators group related items; don't overcrowd
- Overflow menu (>>) appears automatically when window is too narrow **Common
  mistakes:** Non-customizable toolbars; toolbar items with no corresponding
  menu bar item (WYSIWYG violation — every toolbar action must be reachable via
  menu).

### Menu Bar

**When to use:** Every macOS app must have a menu bar. This is non-negotiable.
**When not to use:** N/A — always present. **Key rules:**

- Standard menus in standard order: Apple, App, File, Edit, Format (if
  applicable), View, Window, Help
- Every action available via toolbar or click must also be accessible via menu
- Keyboard equivalents: use system-standard shortcuts (⌘C, ⌘V, ⌘Z, ⌘Q); don't
  reassign them
- Unavailable items are dimmed, not removed (Perceived Stability)
- Destructive items go last in their group; never at the top **Common
  mistakes:** Missing standard menus; keyboard shortcuts conflicting with system
  shortcuts; removing items instead of dimming.

### Contextual Menu

**When to use:** Right-click/Control-click on objects to surface relevant
secondary actions. **When not to use:** Primary access to actions — contextual
menus are a shortcut, not a replacement for menu bar items. **Key rules:**

- Only include actions relevant to the clicked object
- Mirror the main menu; don't offer exclusive actions only reachable via
  right-click (WYSIWYG)
- Separate groups with dividers; keep the menu short (≤ 10 items ideally)
  **Common mistakes:** Contextual menus as the only way to reach an action;
  overly long contextual menus.

### Sidebar (Source List)

**When to use:** Navigation between sections or documents (Finder, Mail, Notes,
Xcode navigator). **When not to use:** Attribute editing — use an Inspector for
that; secondary tools — use a panel. **Key rules:**

- Source list style: single selection highlight with sidebar vibrancy, no
  alternating rows; disclosure triangles for hierarchy
- Selection in sidebar drives content in the main area (master-detail pattern)
- Sidebar can be hidden/shown; save user's preference
- Width: user-resizable within a min/max range **Common mistakes:** Putting
  editing controls in a sidebar; non-resizable sidebars.

### Inspector

**When to use:** Displaying and editing attributes of the current selection
(Format Inspector, Attributes Inspector). **When not to use:** Navigation — use
a sidebar; primary editing — use the document canvas. **Key rules:**

- Trailing side of the window (right); user-togglable
- Content updates live to reflect the current selection
- If nothing is selected, show a helpful empty state, not a blank panel
- Group related attributes with section headers **Common mistakes:** Inspector
  that doesn't update on selection change; putting navigation in the inspector.

### Split View

**When to use:** Dividing the window into two resizable panes with related
content (sidebar + content, primary + detail). **When not to use:** When one
pane is always empty or always the same size — use a fixed layout. **Key
rules:**

- User can resize panes by dragging the divider
- Panes have minimum sizes; neither can collapse to zero unless collapse is an
  intentional feature
- Horizontal split (left/right) is standard; vertical split (top/bottom) for
  code editors **Common mistakes:** Non-resizable split views; allowing panes to
  collapse unexpectedly.

### Popover

**When to use:** Transient, focused interaction anchored to a control (color
picker, filter options, date picker from a button). **When not to use:**
Persistent information; anything requiring more than ~5 controls; navigation.
**Key rules:**

- Arrow points to the control that opened it
- Dismiss by clicking outside (non-modal) or via explicit close button if
  complex
- Size to content; don't make it larger than necessary
- Don't open a popover from within a popover **Common mistakes:** Popovers that
  are too large (use a sheet instead); non-dismissible popovers; popovers from
  popovers.

### Sheet

**When to use:** Task requiring user's immediate attention and completion before
returning to the parent window (Save dialog, Print dialog, settings that affect
the current document). **When not to use:** Non-blocking information;
navigation; tasks that can be deferred. **Key rules:**

- Slides down from the title bar of its parent window; attached to the window
- Modal relative to the parent window only; other windows remain accessible
- Includes Cancel and a primary action button (Save, Print, etc.)
- Don't size to fill the entire window; leave the parent context visible
  **Common mistakes:** Using an alert when a sheet is appropriate; making sheets
  full-screen; sheets without a Cancel button.

### Alert

**When to use:** Situation requiring an immediate decision or notification that
will block workflow (irreversible action, error that prevents progress). **When
not to use:** Informational messages; non-critical notifications; status updates
— use inline feedback, banners, or status bars. **Key rules:**

- Title: brief, descriptive (the situation). Body: explanation + consequence.
- Buttons: rightmost = primary/default, Cancel = always present for reversible
  alerts
- Destructive button: labeled with the action (not "OK"), standard style on
  macOS
- "Frequent alert boxes are a good indication that something is wrong with the
  program design." (1992 HIG Ch. 1) **Common mistakes:** Alerts for
  informational messages; OK/Cancel as button labels instead of action verbs;
  missing Cancel button.

### Push Button

**When to use:** Initiating an action (Save, Cancel, Submit, Open). **When not
to use:** Toggling state (use checkbox or segmented control); navigation (use
sidebar or toolbar). **Key rules:**

- Label: verb or verb phrase describing the action ("Save Document", not "OK")
- Default button (Return key): blue fill; only one per dialog/window
- Destructive actions on macOS use no special color (unlike iOS red);
  distinguish by position (last button) and verb label, not color
- Control sizes: Regular for dialogs, Small for inline use, Mini for dense
  toolbars **Common mistakes:** "OK" as a button label; multiple default
  buttons; non-verb labels.

### Segmented Control

**When to use:** Switching between a small set of mutually exclusive views or
modes (2–5 segments). **When not to use:** More than 5 options (use popup
button); non-exclusive choices (use checkboxes). **Key rules:**

- Each segment has a label, icon, or both
- Selection is immediate — no confirmation needed
- Width: segments should be equal width when possible **Common mistakes:** More
  than 5 segments; using for navigation between major sections (use sidebar).

### Pop-up Button (Dropdown)

**When to use:** Selecting one option from a list of 3+ mutually exclusive
options when space is constrained. **When not to use:** Fewer than 4 options
(use radio buttons); very long lists (use a searchable combo box). **Key
rules:**

- Shows the currently selected item
- Opens a menu anchored to the control
- Include a default selection; don't default to a blank/placeholder **Common
  mistakes:** Pop-up with only 2 items (use radio buttons or segmented control);
  no default selection.

### Checkbox

**When to use:** Binary on/off settings; multi-select from a group of
independent options. **When not to use:** Mutually exclusive options (use radio
buttons); actions (use buttons). **Key rules:**

- Label describes the checked state
- Indeterminate state (dash) only for mixed-state parent in a hierarchy
- Vertical list for multiple checkboxes; avoid horizontal rows **Common
  mistakes:** Using checkboxes for mutually exclusive options; labels that
  describe the unchecked state.

### Radio Buttons

**When to use:** Selecting exactly one option from a small set (2–5) of mutually
exclusive options. **When not to use:** Independent options (use checkboxes);
more than 5 options (use pop-up button). **Key rules:**

- Always show all options simultaneously — no hiding
- One option always selected (no null state unless "None" is an explicit option)
- Label each option clearly; group with a title **Common mistakes:** Radio
  buttons for independent options; hiding some options.

### Text Field

**When to use:** Single-line free-form text input. **When not to use:**
Multi-line input (use NSTextView); constrained input with known options (use
combo box or pop-up). **Key rules:**

- Placeholder text describes expected content (not a label — always show an
  external label too)
- Validation feedback inline, not via alert
- Return key confirms and moves focus; Tab moves to next field **Common
  mistakes:** Placeholder text as the only label (it disappears on focus); alert
  dialogs for validation errors.

### Table View

**When to use:** Displaying a list of items with multiple attributes per item
(file browser, music library, spreadsheet-like data). **When not to use:**
Hierarchical data (use outline view); single-attribute lists (use a simple
list). **Key rules:**

- Column headers are sortable by click; show sort indicator
- Row selection: single or multiple (with ⌘ or Shift)
- Alternating row colors optional; used for wide tables with many columns
- Right-click row for contextual menu with row-relevant actions **Common
  mistakes:** Non-sortable columns; no row selection highlight.

### Outline View

**When to use:** Hierarchical data that users need to expand/collapse (file
system, code structure, mail folders). **When not to use:** Flat lists (use
table view); more than 3–4 levels of nesting. **Key rules:**

- Disclosure triangles on the left; indent child rows
- Expand/collapse state should be saved across sessions
- Same column/selection behavior as table view **Common mistakes:** Deeply
  nested outlines (4+ levels); not persisting expand state.

### NSVisualEffectView (Blur / Vibrancy)

**When to use:** Sidebars, toolbars, popovers — where showing through to the
content behind creates meaningful depth and context. **When not to use:** Main
content areas; backgrounds of dialogs; decoration without purpose. **Key
rules:**

- Use system-provided materials (`sidebar`, `menu`, `popover`, `headerView`,
  `titlebar`) — each has a specific semantic context; don't invent custom ones
- Set `blendingMode` to `.behindWindow` for backgrounds that blur the desktop,
  `.withinWindow` for surfaces blurring app content behind them
- Vibrancy makes labels and icons adapt to the background — use it for text and
  icons in blurred areas
- Reject: blur everywhere for aesthetic reasons — blur is for depth cues, not
  decoration **Common mistakes:** Blur on main content areas; custom blur
  materials that don't use system semantics.

### Pointer / Cursor

**When to use:** Always — the pointer must reflect the available action at the
current location. **Key rules:**

- Arrow: default, over non-interactive areas
- IBeam: over editable text
- Crosshair: over drawing/selection areas in canvas tools
- Resize arrows (N/S/E/W): over resize handles
- Open hand / closed hand: over draggable objects
- Pointing hand: over links and clickable non-button elements **Common
  mistakes:** Arrow cursor over draggable objects; no cursor change over
  resizable edges.

### Drag and Drop

**When to use:** Moving or copying objects between locations when the
relationship between source and destination is clear. **When not to use:**
Primary method for an action — drag and drop is an efficiency shortcut, not the
only path. **Key rules:**

- Show visual feedback during drag: ghost image of dragged item, highlight valid
  drop targets
- Provide an alternative non-drag path for every drag action (menu, button,
  keyboard)
- Spring-loaded folders: hovering over a closed container opens it after a delay
- Use UTTypes for data transfer so apps can negotiate formats **Common
  mistakes:** No alternative to drag; no drop target highlighting; no ghost
  image during drag.
