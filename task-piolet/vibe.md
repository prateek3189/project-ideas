# Smart Task Manager — Project Document (Plain HTML & CSS)

> Purpose: a static, **JavaScript-free** v1 UI you can paste into Cursor to scaffold the app. It defines structure, screens, components, content models, and styling guidelines so you can build clean HTML and CSS that’s ready for later AI/JS wiring.

---

## 1) Vision & Goals

- Help users capture tasks and see a “**Smart Priority**” order based on deadline urgency, task effort, and their current **mood/energy**.
- Version 1 is **pure HTML + CSS**: all “AI” is represented as UI placeholders, badges, and explanatory copy.
- The markup must be **semantic, accessible, responsive, printable**, and easy to enhance later with JS/AI.

---

## 2) Constraints (V1)

- No JavaScript; interactive UX uses native HTML controls (e.g., `details/summary`, anchors) and CSS-only techniques.
- No external UI frameworks. Use system fonts or a single webfont if needed.
- Keep the CSS modular and scalable (naming guide in §8).

---

## 3) Primary Personas & Top User Stories

- **Busy Professional**: “I want my most urgent, low-energy tasks at the top.”
- **Student/Creator**: “Show me tasks that fit my current mood or available energy.”
- **Manager**: “I need quick status, filters, and printable summaries.”

User stories:

1. Capture a new task with title, deadline, effort, energy required, tags, and notes.
2. View a prioritized list with clear visual indicators (deadline proximity, energy match).
3. Adjust “today’s mood” and “current energy” (as static sliders in V1) to see what the AI would consider.
4. Filter by status/tag and print a day plan.
5. Review simple analytics (counts by status, upcoming deadlines) presented as static cards.

---

## 4) Information Architecture & Navigation

- **Top-level pages/sections**

  - Dashboard (default) — prioritized list + quick stats
  - All Tasks — full table/list view with filters
  - Add/Edit Task — form UI (static)
  - Analytics — static summary tiles, legend
  - Settings — appearance, density, theme, default energy bands (copy only)
  - About — brief description of Smart Priority UX and future AI plan

- **Global shell**

  - Header: app name, Search (decorative), Today’s date, Print icon (links to print)
  - Sidebar: nav links, user profile placeholder, theme toggle (visual only)
  - Content area: page header, controls, content
  - Footer: short help text and version

---

## 5) Screen Blueprints (HTML structure guidance)

### 5.1 Dashboard

- Page header: “Today” + date
- “Your State” panel: **Mood** and **Energy** sliders (read-only look), plus badges (e.g., Calm/Focused, Low/Medium/High Energy)
- “Smart Priority” list:

  - Task card with: title, due date badge, effort chip (S/M/L), energy-fit indicator (Good/OK/Poor), tag list, status pill
  - A **priority index** visual (e.g., 0–100 bar) with a tooltip note: “AI score placeholder”

- Empty state (if no tasks): illustration placeholder + CTA copy “Add your first task”

### 5.2 All Tasks

- Filter bar: Status (Open, In Progress, Done), Tags (multi-select look), Deadline quick filters (Today, This Week, Overdue)
- Sort controls (visual only): Smart Priority, Deadline, Effort
- Dense list of task rows; include a compact variant toggle in Settings

### 5.3 Add/Edit Task (Form)

- Fields: Title, Description, Deadline (date), Effort (S/M/L), Energy Required (Low/Med/High), Mood Match (Calm/Creative/Focused etc.), Status, Tags (comma-style), Notes
- Form actions: Save (visual), Cancel (link back)
- Validation hints (static notes under each field)

### 5.4 Analytics

- Tiles:

  - Tasks due Today / This Week
  - Status breakdown
  - Overdue count
  - Energy distribution (text bars, no charts in V1)

- Legend explaining the visual scale used for “Smart Priority”

### 5.5 Settings

- Appearance: Light/Dark theme (visual toggle)
- Density: Comfortable / Compact
- Default energy bands (descriptive copy)
- Accessibility preferences (high contrast mode)

### 5.6 About

- What Smart Priority means
- Future AI integration note (explained in plain language)

---

## 6) Component Inventory (CSS-only behavior)

- **App Header**: logo text, date, print link
- **Sidebar Navigation**: vertical list with active state; include icons as decorative spans
- **Section Header**: title + subtext; optional action area (e.g., “Add Task” link)
- **Filter/Sort Bar**: pill buttons; single-select and pseudo multi-select styles
- **Task Card**:

  - Title (one line truncate), meta row (deadline badge, effort chip, status)
  - Priority index bar (0–100 look)
  - Energy fit badge (Good/OK/Poor)
  - Tags list, notes teaser

- **Badges & Chips**:

  - Deadline urgency: Overdue, Today, Soon, Later
  - Effort: S, M, L
  - Status: Open, In Progress, Blocked, Done

- **Mood/Energy Sliders** (static look):

  - Horizontal track with thumb; label set showing discrete stops

- **Empty State**: icon box + guidance text
- **Toast/Alert** (decorative): success, warning, info
- **Dialog/Sheet** (CSS-only): use a full-screen overlay section linked from “Add Task”; close via “Back” link
- **Skeletons**: shimmering blocks for list items (pure CSS effect)
- **Table/List**: alternate row backgrounds, focus styles

---

## 7) Content Model (for later data/AI wiring; no code)

**Task**

- id, title, description
- deadline (date), createdOn
- effort (S/M/L)
- energyRequired (Low/Med/High)
- moodMatch (Calm/Creative/Focused/Any)
- status (Open/In Progress/Blocked/Done)
- tags (array of short labels)
- notes (long text)
- priorityIndex (0–100, computed later)
- urgencyBand (Overdue/Today/Soon/Later) — derived later

**User State (today)**

- mood (Calm/Creative/Focused/Stressed)
- energy (Low/Med/High)
- availableTime (short/medium/long) — optional
- preferences (e.g., prefers small wins early)

---

## 8) CSS Architecture & Naming

- **Methodology**: BEM-style class names for readability and scalability.
- **Layers**:

  1. Design tokens (colors, spacing scale, radii, elevations, typography sizes)
  2. Base elements (html, body, headings, paragraphs, lists, forms)
  3. Utilities (margin, padding, layout helpers)
  4. Components (header, sidebar, card, chip, badge)
  5. Page layouts (dashboard, tasks, analytics)

- **Themes**: root variables for Light/Dark; toggle by setting a theme class on `<body>`.
- **Accessibility**: clear focus styles; do not remove outlines.

---

## 9) Visual Design System

**Color Tokens (Light Theme)**

- Background: near-white
- Surface: white
- Text primary: near-black
- Text secondary: dark gray
- Accent: blue
- Success: green
- Warning: amber
- Danger: red
- Muted: light gray
- Priority bar gradient: green → amber → red (left to right)

**Dark Theme**

- Background: near-black
- Surface: deep gray
- Text primary: white
- Text secondary: light gray
- Keep semantic colors WCAG AA on dark

**Typography**

- Display: 28–32
- H1: 24
- H2: 20
- Body: 16
- Caption: 13–14
- Line heights: 1.4–1.6

**Spacing & Radius**

- Spacing scale: 4, 8, 12, 16, 24, 32
- Corner radius: 8 (cards), 999 (pills)
- Shadows: subtle layered elevations for surfaces

**Breakpoints**

- Small: ≤ 480
- Medium: 768
- Large: 1024
- XL: 1280+

**States**

- Hover raised shadow for cards
- Focus ring visible and high contrast
- Disabled: lowered contrast + no hover transitions

---

## 10) Accessibility & Semantics

- Use proper landmarks: header, nav, main, section, footer.
- Headings must be hierarchical (H1 per page).
- Labels tied to inputs; required field hints in text.
- Keyboard navigable: logical tab order; visible focus.
- Color contrast: meet WCAG AA; do not use color alone to signal priority—pair with icons or text.
- Provide print styles: remove nav, simplify colors, show full text.

---

## 11) SEO & Metadata (static)

- Page titles per section (“Dashboard — Smart Task Manager”).
- Meta description explaining benefits.
- Favicons and social preview image placeholders.
- No tracking in V1.

---

## 12) Performance & Quality Checklist

- Single CSS file minified; avoid @import chains.
- Image assets optimized (SVG where possible).
- Validate HTML; no duplicate IDs.
- Lighthouse check (accessibility, best practices).
- Print stylesheet works cleanly (one page per section if needed).

---

## 13) File & Folder Structure (no code content, just files)

- root

  - index.html (Dashboard)
  - tasks.html (All Tasks)
  - task-form.html (Add/Edit Task)
  - analytics.html
  - settings.html
  - about.html
  - styles/

    - tokens.css
    - base.css
    - utilities.css
    - components.css
    - layouts.css
    - themes.css
    - print.css

  - assets/

    - icons/ (SVG placeholders)
    - illustrations/
    - logo/

_(If you prefer a single CSS file for V1, merge thoughtfully but keep sections.)_

---

## 14) Smart Priority UX (V1 Explanation Only)

- Show a **Priority Index** 0–100 as a horizontal bar on each task card.
- The nearby text explains: “Score is a placeholder; in future, AI ranks your tasks considering deadline urgency, your current mood/energy, and effort.”
- Display **Energy Fit** badge:

  - Good: task’s energyRequired matches current energy
  - OK: one step away
  - Poor: mismatch

- **Urgency Badges**:

  - Overdue: deadline past
  - Today: due today
  - Soon: within 3 days
  - Later: beyond 3 days

- For V1, these are **static labels** you set in HTML to illustrate the concept.

---

## 15) Page-Specific Content Guidance (copy you can paste)

**Dashboard**

- “Your State” section: short helper text under sliders, e.g., “Use your current mood and energy to choose the right work.”
- Priority explainer: “Smart Priority is a preview of how AI will order your tasks.”

**All Tasks**

- Filter hints: “Filters are visual only in this version.”
- Empty state message: “No tasks match your filters.”

**Task Form**

- Helper lines under each field, e.g., “Effort is a rough size: S, M, or L.”

**Analytics**

- Card captions: “Static snapshot for V1; AI insights coming soon.”

**Settings**

- “These settings control appearance of the static UI. Functional changes arrive with JS/AI.”

**About**

- Short mission statement and roadmap note.

---

## 16) Print Styles (must have)

- Hide header/sidebar; show page title and date.
- Expand truncated text; show complete task details.
- Replace dark backgrounds with white and dark text.
- Include a small footer: “Smart Task Manager — printed on {date}”.

---

## 17) Acceptance Criteria (V1)

- Pages render without JS; navigation links function between pages.
- Dashboard shows at least 6 task cards with varied urgency/energy badges.
- All Tasks page shows filter/sort UI visually with at least 10 sample rows.
- Add/Edit Task page shows all fields with labels, helper text, and validation notes (static).
- Analytics shows 3–6 tiles with counts/placeholder bars.
- Settings page allows theme and density **visually**; toggles shown but non-functional.
- Print stylesheet produces a clean, readable day plan.
- Meets basic accessibility checks (headings, labels, focus order, contrast).

---

## 18) Future Enhancements (Post-V1)

- Add JS to persist tasks, compute urgency, and dynamically sort by priority.
- Integrate AI model (local or API) to compute “Smart Priority” with tunable weights.
- Real filters/sorts; search across titles/notes/tags.
- Calendar integration; reminders; timeboxing view.
- Charts (SVG/Canvas) for analytics.

---

## 19) Build Steps in Cursor (no code)

1. Create the file structure listed in §13.
2. Start with index.html using the layout and components described.
3. Compose other pages by reusing the same header/sidebar and section patterns.
4. Style from tokens → base → utilities → components → layouts → themes → print.
5. Manually vary badges/labels on sample tasks to demonstrate the AI concept.
6. Test responsiveness (mobile, tablet, desktop) and print output.

---

## 20) Sample Content Matrix (to populate static UI)

- Create 12–20 tasks mixing:

  - Deadlines: past, today, 2 days, 7 days
  - Effort: S/M/L
  - EnergyRequired: Low/Med/High
  - MoodMatch: Calm/Creative/Focused
  - Status: Open/In Progress/Blocked/Done
  - Tags: work, study, admin, deep-work, quick-win

---

If you want, I can turn this into a ready-to-paste **README.md** or expand any section (e.g., accessibility checklist, color tokens, or page skeletons) — still without code.
