# Smart Coding Agent — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** of a developer assistant (like “Junie”) that helps **debug, write, and optimize code live**. V1 is **JavaScript-free**—no real execution, LSP, terminals, or repo access. All “AI” bits are **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Provide a **single workspace** that blends **code view**, **chat**, **actions (fix/optimize/test)**, and **diff review**.
- Make suggestions **traceable**: “why”, “risk”, “time to apply”, and **file changes**.
- Keep UI **fast, accessible, and print-friendly**, with clean theming (light/dark/high-contrast).

---

## 2) Constraints (V1)

- **No JS**: no real runs, builds, terminals, git, or language servers.
- Use semantic HTML (`<details>`, `<form>`, tables, lists) and **pure CSS** (badges, loaders, diff colors, tabs).
- All “Run”, “Fix”, “Explain”, “Profile” buttons are **visual**.

---

## 3) Personas & Core User Stories

- **Solo Dev**: “Explain this stack trace and propose a safe patch.”
- **Team Lead**: “Summarize this PR and surface risks.”
- **Perf Hunter**: “Find hotspots and suggest micro-optimizations.”
- **New Contributor**: “Generate tests and guard-rails before refactor.”

**Stories (visual-only)**

1. Paste error log → **Root-cause analysis** + **Fix Patch** (diff).
2. Ask for **function implementation** → insert-ready snippet + usage examples.
3. **Optimize** a file → complexity note + micro-opts diff.
4. **Generate tests** → table of cases + skeletons.
5. **Explain code** → inline comments + diagram placeholder.

---

## 4) Information Architecture

- **Workspace** — code view, chat, actions, context panel
- **Diff Review** — unified/split diffs, file tree, risk notes
- **Tests** — suggested cases, coverage meter (CSS), flaky notes
- **Perf** — hotspots list, complexity bars, budget chips
- **Playbooks** — recipes (debug/optimize/test/ship)
- **Settings** — models (visual), repo scope, privacy, themes
- **About** — capabilities, limitations, disclaimers

**Global Shell**
Header: app name, repo selector (visual), branch chip, print
Sidebar: nav, project tree (static), theme toggle (visual)
Main: page content • Footer: tips/version

---

## 5) Screen Blueprints

### 5.1 Workspace (Core)

- **Top Bar**: Path breadcrumbs, file status chips (M/A/R), search input (visual).
- **3-Pane Layout** (responsive):

  - **Code Pane**: syntax-colored **static** blocks; line numbers; inline **annotation markers** (🔎, ⚠️).
  - **Chat Pane**: user/agent bubbles; “why this” `<details>`; **Action buttons**: **Fix**, **Explain**, **Test**, **Optimize**, **Doc**.
  - **Context Pane**: stack trace, env vars, deps, test summary cards.

- **Command Palette** (visual): “Ctrl/Cmd+K” opens a sheet with actions list.
- **Status Bar**: model chip (visual), tokens est., latency (—), git pseudo state.

### 5.2 Diff Review

- **Tabs**: Unified • Split
- **File Tree**: changed files, insert/delete counts chips.
- **Diff Blocks**: `+`/`−` lines with CSS line gutters; **Risk callouts**: API change, behavior change, perf cost.
- **Footers**: “Apply”, “Stage subset” (visual), **Print Patch**.

### 5.3 Tests

- **Coverage Tile** (ring, CSS conic) + target badge.
- **Test Table**: case name, inputs, expected, priority, status (planned/wip).
- **Scaffold Blocks**: language-specific skeletons (static).
- **Flaky Detector** (copy): heuristics explanation.

### 5.4 Perf

- **Hotspots List**: file/function, est. time % / allocations (copy), **Complexity bars**.
- **Suggestions**: memoize • streaming • batch I/O • algorithmic switch.
- **Budget Chips**: target p95, memory cap, bundle size.
- **Before/After** callout (copy-only).

### 5.5 Playbooks

- Debug: “Reproduce → Min case → Hypothesis → Patch → Verify”.
- Optimize: “Measure → Focus → Replace → Guard with tests”.
- Testing: “Arrange/Act/Assert templates”, “Golden files”, “Property tests”.
- Shipping: “Changelog, Backward compat, Feature flag, Rollout plan”.

### 5.6 Settings

- Model (visual), context window, privacy (local-only concept), telemetry toggle.
- Project scope (folders), unsafe file types warning.
- Theme (light/dark/high-contrast), fonts (monospace), reduced motion.

---

## 6) Component Inventory (CSS-only)

- **Code Block** (mono, line nums, highlight ranges)
- **Annotation Marker** & **Inline Note**
- **Chat Bubble** (user/agent variants)
- **Action Bar** buttons (Fix/Explain/Test/Optimize)
- **Diff Block** unified/split + **Risk Badge**
- **Coverage Ring**, **Bar Meters**, **Budget Chips**
- **Stack Trace Panel**, **Env Vars Table**
- **Playbook Card**, **Command Palette Sheet**
- **Alert/Nudge** (e.g., “Run tests before applying patch”)
- **Print Header/Footer** (diff & report)

---

## 7) Data Model (future-ready; no code)

**Project**

- `id`, `name`, `lang[]`, `paths[]`, `branch`, `env{}`

**Context**

- `files[]` (`{path, content, hash}`), `stackTrace[]`, `deps[]`, `tests[]`, `metrics{}`

**Turn**

- `role` (user|agent), `message`, `attachments[]` (files/snippets), `time`

**Action**

- `type` (fix|explain|test|optimize|doc), `inputs`, `outputs` (diff|tests|notes), `confidence`

**Diff**

- `files[]` (`{path, hunks[]}`), `risks[]`, `notes[]`

**TestCase**

- `id`, `name`, `inputs`, `expected`, `priority`, `status`

**PerfInsight**

- `location`, `metric`, `estImpact`, `suggestion`

---

## 8) CSS Architecture & Naming

- **BEM examples**
  `.code`, `.code__line--added`, `.code__line--removed`, `.note--risk`,
  `.chat__bubble--agent`, `.actions__btn--fix`, `.diff__hunk`, `.meter--coverage`,
  `.hotspot__row`, `.badge--budget`, `.palette`, `.alert--warning`
- Layers:

  1. `tokens.css` — colors/spacing/type
  2. `base.css` — reset & typography
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — code, chat, diff, meters, badges, cards, sheets
  5. `layouts.css` — shell, 2/3-pane
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — diffs & reports

---

## 9) Design System

**Colors (Light)**

- Bg #0F172A on code? (invert for contrast) → Use **Surface** #FFFFFF, **Text** #0F172A
- Accents: **Primary** #2563EB • Success #16A34A • Warn #F59E0B • Danger #DC2626 • Info #3B82F6
- Diff: Added **#E8F7EE** / Removed **#FDECEC**; gutters muted.

**Dark**

- Bg #0B1220 • Surface #111827 • Text #E5E7EB
- Diff: Added **#12391F** / Removed **#3a1d1d**

**Type**

- Monospace stack: `ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace`
- Sizes: Display 28 • H1 24 • H2 20 • Code 13–14 • Caption 12

**Spacing & Radius**

- Scale: 4/8/12/16/24/32; Radius: 8 (code blocks), 12 (cards), 999 (pills)

**Icons**

- Bug, lightning, beaker, diff, branch, clock, chip.

---

## 10) Accessibility & DevX

- Proper landmarks; one H1/page; **skip-to-content** link.
- Keyboard-visible focus; large hit areas; no color-only signals in diffs (use `+`/`−` markers).
- Code blocks are **selectable**; line numbers non-selectable via CSS.
- Chat bubbles accessible names (“You”, “Agent”).
- Print-friendly diffs & reports.

---

## 11) Print Styles

- **Patch Review**: per-file diffs with risk notes & summary.
- **Session Report**: prompts, agent rationale, actions, resulting diffs/tests.
- Hide nav; black on white; footers with page numbers.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Workspace)
 ├─ diff.html            (Diff Review)
 ├─ tests.html           (Test Plan)
 ├─ perf.html            (Hotspots)
 ├─ playbooks.html
 ├─ settings.html
 ├─ about.html
 ├─ styles/
 │   ├─ tokens.css
 │   ├─ base.css
 │   ├─ utilities.css
 │   ├─ components.css
 │   ├─ layouts.css
 │   ├─ themes.css
 │   ├─ print.css
 └─ assets/
     ├─ icons/
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Workspace nudge:** “Drop a stack trace or paste a file path to get targeted help.”
- **Action helper (Fix):** “Patches are **minimal** and **reversible**. Review diffs before applying.”
- **Action helper (Optimize):** “Prefer algorithmic wins over micro-opts unless measured.”
- **Risk note:** “Public API change detected → bump minor, update docs & tests.”
- **Test tip:** “Start with **happy path** + **1 failure case**; add **property test** if pure.”
- **Perf banner:** “Budget exceeded for p95 latency (target 180ms, est 240ms).”

---

## 14) Acceptance Criteria (V1)

- Workspace shows **3 panes** with code, chat, and context; top bar + status bar.
- Diff page shows **unified & split** views, file tree, and risk badges.
- Tests page lists **≥8** suggested cases, coverage ring, and scaffold blocks.
- Perf page lists **≥6** hotspots with bars and suggestions.
- Playbooks page shows **≥9** recipes across debug/optimize/test/ship.
- Print stylesheet outputs **Patch Review** & **Session Report** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real repo connect (Git), code embeddings & retrieval, multi-file edits.
- Runtime sandboxes (Docker/Firecracker), **on-demand tests**, coverage & trace import.
- LLM + tools: **lint**, **type-check**, **unit run**, **profiler**, **formatter**.
- Safe apply with **feature flags**, migration assistants, codemods.
- Team mode: shared sessions, comments, approvals, audit trail.
- Privacy: on-device diffing, redaction, secrets scanner.

---

## 16) Sample Static Data (populate UI)

**Stack Trace (context panel)**

```
TypeError: cannot read property 'map' of undefined
  at buildRows (src/table.ts:87)
  at render (src/app.tsx:142)
```

**Agent Suggestion (chat)**

- **Root cause:** `rows` is `undefined` when API returns `{ data: null }`.
- **Fix (risk: low):** Default `rows = []` and guard in `buildRows`.
- **Patch size:** 6 lines; files: `src/table.ts`, `src/types.ts`.

**Unified Diff (snippet)**

```diff
- export function buildRows(rows: Row[]) {
+ export function buildRows(rows: Row[] = []) {
   if (!rows.length) return [];
-  return rows.map(r => toView(r));
+  return rows.filter(Boolean).map(r => toView(r));
}
```

**Tests (table rows)**

- `buildRows/empty → []` — **Planned**
- `buildRows/nulls filtered` — **Planned**
- `render handles empty state` — **Planned**

**Perf Hotspots**

- `parseLargeJson` — 38% time — Suggest: stream + chunk parse.
- `getUserProjects` — N+1 queries — Suggest: batch with `IN` clause.

---

If you want, I can also convert this into **ready-to-paste page skeletons** (still no JS) or a **README.md** tailored for Cursor.
