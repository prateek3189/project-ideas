# AI Homework Assistant — Project Document (Plain HTML & CSS)

> **Goal:** Create a **static HTML + CSS v1 prototype** of an **AI-guided homework helper** that teaches by walking students through **step-by-step solutions**, **hints**, and **checks for understanding**—not just final answers. No JavaScript in V1; all “AI” parts are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Replace “give me the answer” with **guided learning**.
- Offer **Socratic prompts**, **hint ladders**, and **error-spotting** steps.
- Keep UI **accessible, semantic, responsive, and printable**.
- Make it easy to plug in real logic later (LLM, rules, grading).

---

## 2) Constraints (V1)

- **No JavaScript**. All interactions are visual or use native HTML (`details/summary`, radios, checkboxes).
- **No external UI frameworks**; system fonts or one webfont max.
- All AI feedback is **copy-only placeholders**.

---

## 3) Personas & Core User Stories

**Personas**

- **Middle/High-School Student**: “Guide me through algebra/physics/lit analysis step by step.”
- **College Freshman**: “I need hints before the final formula or proof.”
- **Teacher/Parent** (view only in V1): “I want printable worksheets and visible thinking.”

**Stories (visual-only in V1)**

1. Pick a **subject** and **topic** (e.g., Algebra → Linear Equations).
2. Paste/type a **problem** and get a **guided plan** (sub-steps with hints).
3. Reveal **hint 1 → hint 2 → final hint** before showing the solution.
4. Complete **Checks for Understanding** (quick T/F, multiple choice, short fill-in—nonfunctional).
5. View a **worked solution** and a **rubric** that explains scoring.
6. See **progress** by topic and weak areas (static tiles/bars).
7. **Print** a worksheet (problem + steps + space to write).

---

## 4) Information Architecture

- **Dashboard** — continue where you left off, active subjects, weak areas (visual).
- **Subjects** — Math, Science, Literature, History, CS (cards with topics).
- **Problem Workspace** — problem input, plan outline, steps, hints, checks, solution, rubric.
- **Worksheets** — printable sets of problems by topic (static).
- **Progress** — topic coverage, practice minutes, mastery heatmap (visual).
- **Settings** — difficulty, hint depth, theme, accessibility (visual toggles).
- **About** — learning-first philosophy & academic integrity.

**Global Shell**

- Header: app name, search (decorative), profile chip, print link.
- Sidebar: nav + subject list + theme toggle (visual).
- Main: page content area.
- Footer: help/version.

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **Continue Learning** card: subject/topic, last problem, “resume” link.
- **Quick Start**: “Pick a subject” grid (5–8 cards).
- **Weak Areas** (visual tiles): “Linear Equations”, “Kinematics”, “Thesis Statements”.
- **Study Streak** (thin bar + day dots).

### 5.2 Subjects

- Filter chips: Grade (6–8, 9–10, 11–12, College), Topic tags (Algebra, Geometry, etc.).
- Subject cards: title, syllabus bullets, est. time, “Start Practice” CTA.

### 5.3 Problem Workspace (core)

- **Problem Input Panel**:

  - Textarea for problem statement (static)
  - Context note (“Show your given/unknowns/goal”)

- **Guided Plan** (outline):

  - Step 1, Step 2, Step 3 (brief summary lines)

- **Step Blocks** (repeat per step):

  - Step title + small description
  - **Hint Ladder**: Hint 1, Hint 2, Final Hint (use `<details>` collapsible)
  - **Student Action Placeholder**: answer field look + “Check” button (visual only)
  - **Socratic Prompt**: short guiding question text
  - **Common Mistake**: a bordered warning copy

- **Checks for Understanding**:

  - 2–3 small questions (radio/checkbox/T-F), with “Explanation” boxes (static)

- **Worked Solution**:

  - Structured solution with math/code formatting placeholders
  - “Where did we use each step?” callouts (labels only)

- **Rubric & Reflection**:

  - Criteria table (Setup • Method • Accuracy • Explanation)
  - Self-reflection prompts: “What tripped you up?”, “Next time you’ll…”

### 5.4 Worksheets

- Topic selector + list of 5–10 problem cards with level badges (Easy/Medium/Hard).
- Each card: problem stem + “Show Plan” (anchors to workspace template).
- Print note: “Use print to generate a practice set.”

### 5.5 Progress

- Tiles: Minutes Practiced, Problems Attempted, Topics Touched.
- **Mastery Bars** by topic (static %s).
- **Heatmap** (CSS grid): days vs. practice intensity.
- “Recommended Next” list (copy-only).

### 5.6 Settings

- Difficulty: Gentle / Standard / Challenging (visual radios).
- Hint Depth: Shallow / Medium / Deep.
- Show Mistakes First: On/Off.
- Theme: Light/Dark/High Contrast (visual).
- Font size: Normal / Large.

### 5.7 About

- “Learn by doing” manifesto.
- Academic integrity note: “Use hints before solutions.”
- Roadmap: real AI tutor, adaptive plans, teacher dashboard.

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Subject Card / Topic Chip**
- **Problem Card** (worksheet)
- **Plan Outline** (ordered list with active item style)
- **Step Block**: title, description, hint ladder (`<details>`), action area, mistake callout
- **Hint**: levels (1,2,final) with icons and muted tones
- **Socratic Prompt**: italic helper text
- **Check Item**: fieldset/legend + options; explanation box
- **Solution Panel**: formatted block with callouts
- **Rubric Table**: criteria rows, score descriptors (visual)
- **Progress Bars** & **Heatmap** (7×5 grid, intensity classes)
- **Badge**: “Perseverance”, “Concept Mastery” (locked/unlocked visuals)
- **Alert/Toast** (info, caution)
- **Print Header/Footer** for worksheets

---

## 7) Data Model (future-ready; no code)

**Problem**

- `id`, `subject`, `topic`, `gradeBand`
- `prompt` (text), `given`, `unknown`, `goal`
- `plan` (array of `Step` IDs)
- `solution` (rich text/markup)
- `rubricId`

**Step**

- `id`, `title`, `description`
- `hints` (array: {level:1|2|final, text})
- `socratic` (prompt text)
- `commonMistake` (text)
- `expectedWork` (what student should produce)

**Check**

- `id`, `type` (single|multi|tf|short)
- `stem`, `options`, `answerKey`, `explanation`

**Rubric**

- `id`, `criteria` (array: {name, descriptorLevels})

**Progress**

- `topicId`, `problemsAttempted`, `minutes`, `masteryPercent`, `heatmap` (date→intensity)

**User**

- `id`, `name`, `gradeBand`, `preferences` (hintDepth, theme, fontSize)

---

## 8) CSS Architecture & Naming

- **BEM**: `.step__hint--level-2`, `.rubric__cell`, `.heatmap__cell--intensity-3`
- Layers:

  1. `tokens.css` (colors, spacing, radii, type)
  2. `base.css` (reset, base elements, typography)
  3. `utilities.css` (grid/flex/spacing helpers)
  4. `components.css` (cards, steps, hints, rubric, checks, progress bars)
  5. `layouts.css` (header/sidebar/workspace)
  6. `themes.css` (light/dark/high-contrast)
  7. `print.css` (worksheets & solutions)

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Muted: #64748B
- Accent (educational): #2563EB
- Success (understood): #16A34A
- Caution (common mistake): #F59E0B
- Danger (misconception): #DC2626
- Heatmap (0–4): progressively stronger fills

**Dark**

- Background: #0B1220
- Surface: #111827
- Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Typography**

- H1: 24–28, H2: 20, Body: 16, Caption: 12–13
- Monospace style block for math/code placeholders (class only).

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 10 (cards), 6 (hint boxes), 999 (chips)
- Subtle shadows for elevation

---

## 10) Accessibility & Semantics

- Landmarks: `<header> <nav> <main> <aside> <footer>`.
- Headings hierarchical; one H1 per page.
- Use `<fieldset><legend>` for checks; `<label>` tied to inputs.
- Hints use `<details><summary>` for keyboard accessibility.
- Do not rely on color alone—pair icons/text for correctness and warnings.
- Ensure print contrast; keep focus outlines visible.

---

## 11) Print Styles (Worksheets & Solutions)

- Hide header/sidebar; show logo, subject, topic, date.
- Render **problem**, **plan outline**, **step prompts**, **ample writing space** (lines).
- Optional second page with **worked solution** and **rubric**.
- Black-on-white, readable serif body optional for print.

---

## 12) File & Folder Structure

```
root
 ├─ index.html            (Dashboard)
 ├─ subjects.html
 ├─ workspace.html        (Problem Workspace)
 ├─ worksheets.html
 ├─ progress.html
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
     └─ illustrations/
```

---

## 13) Page Copy (paste-ready snippets)

- **Workspace Intro**: “We’ll solve this by breaking it into small steps. Try each **hint** in order before revealing the solution.”
- **Socratic Prompts**:

  - “What is the unknown? What is given?”
  - “Which formula or rule applies here? Why?”
  - “Can you check units/signs/reasonableness?”

- **Common Mistake**:

  - “Sign error when isolating variable.”
  - “Forgetting to distribute across parentheses.”

- **Reflection**:

  - “Which step was hardest?”
  - “Write a one-line summary of the method used.”

---

## 14) Subject Templates (sample static content)

**Algebra (Linear Equation)**

- Problem: “Solve for x: 3x + 5 = 20”
- Plan: Isolate variable → Subtract 5 → Divide by 3
- Hints:

  1. “Undo addition first.”
  2. “Subtract 5 from both sides.”
  3. “Now divide both sides by 3.”

- Check (T/F): “x = 5” (T)
- Solution: “3x = 15 → x = 5”
- Rubric: Setup (1) • Method (2) • Accuracy (1) • Explanation (1)

**Physics (Kinematics)**

- Problem: “Distance with v=5 m/s for t=8 s?”
- Plan: Identify knowns → Choose formula → Compute
- Hints: Use $d = v \times t$
- Solution: $d = 5 \times 8 = 40 \, \text{m}$

**Literature (Thesis)**

- Prompt: “State a thesis about theme in ‘The gift of the Magi’.”
- Plan: Identify theme → Claim + because + reasons → Evidence placeholders
- Hint: “Use ‘because’ to force reasoning.”

---

## 15) Acceptance Criteria (V1)

- Dashboard shows recent activity + weak areas (visual).
- Subjects page lists ≥8 topic cards across 3+ subjects.
- Workspace displays **problem → plan → step blocks (with hint ladders) → checks → solution → rubric**.
- Worksheets page lists ≥6 problems with level badges.
- Progress page shows mastery bars and a weekly heatmap.
- Print stylesheet outputs a clean worksheet and solution set.

---

## 16) Future Enhancements

- JS to persist attempts; time on task; step-by-step validation.
- **AI Tutor**: adaptive hinting, misconception detection, Socratic dialogue.
- Auto-generated rubrics and targeted practice sets.
- Teacher dashboard: assign sets, review thinking traces, export grades.
- Handwriting/math input, LaTeX render, code runners (per subject).
- Academic integrity guardrails: solution delays, effort checks.

---

## 17) Sample Static Data (to populate UI)

- Recent: “Algebra • Linear Eq #12 (in progress)”, “Physics • Kinematics #3 (done)”
- Weak Areas: “Factoring Quadratics (35%)”, “Thesis Statements (40%)”
- Heatmap: last 5 weeks with 0–4 intensity classes
- Badges: “Hint Disciplined”, “Step Finisher”, “Consistency 7-Day”

---

Want me to convert this into a **README.md** or draft **page skeletons** (still no JS) so you can paste directly into Cursor?
