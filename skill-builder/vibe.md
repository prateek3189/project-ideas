# Skill Builder Micro-Courses — Project Document (Plain HTML & CSS)

> **Goal:** Create a **static HTML + CSS v1 prototype** for **short, interactive micro-lessons** with **quizzes** and **progress tracking** placeholders. No JavaScript in V1—pure UI scaffolding you can paste into **Cursor** and enhance later.

---

## 1) Vision & Goals

- Deliver **bite-sized lessons** (5–10 minutes) that feel approachable and focused.
- Provide **quiz UIs** and **progress visuals** (bars, badges) as placeholders.
- Keep markup **semantic, accessible, responsive, and printable**.
- Make the structure easy to wire up later to real scoring, persistence, and analytics.

---

## 2) Constraints (V1)

- **No JavaScript**. Interactions are visual only. Use native HTML (radio/checkbox, `details/summary`, anchors).
- **No external UI frameworks**. System fonts or one webfont.
- CSS organized for clarity and future enhancement.

---

## 3) Personas & User Stories

- **Busy Professional:** “Give me a quick skill burst I can finish over coffee.”
- **Student:** “I want short drills with instant feedback look/feel.”
- **Career Switcher:** “Track what I’ve finished and what’s next.”

**Core Stories (visual-only in V1):**

1. Browse **micro-courses** with length, level, and tags.
2. Open a **lesson** with sections (concept → example → quick check).
3. Take a **quiz** (single/multiple choice, T/F) with a “Your answer” display (no real scoring).
4. See **progress** (lesson completion bars, course %).
5. View a **profile** with badges and certificate placeholders.

---

## 4) Information Architecture

- **Dashboard** — continue learning, today’s streak, next lesson
- **Catalog** — browse/search courses by category/level
- **Course Overview** — syllabus, estimated time, requirements
- **Lesson Player** — content sections, inline checks, quick quiz
- **Quiz** — dedicated page with question list (static feedback copy)
- **Progress** — course % bars, badges, recent activity
- **Settings** — theme, density, accessibility, notifications (visual)
- **About** — how micro-courses work and roadmap

**Global Shell**

- Header: app name, search, profile chip, print link
- Sidebar: navigation, categories, theme toggle (visual)
- Main: page content
- Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **Continue Learning** card: course title, next lesson, % bar.
- **Daily Streak / XP** (visual strip).
- **Recommendations**: 3–6 micro-courses (cards with tags).

### 5.2 Catalog

- Filter bar: Level (Beginner/Intermediate/Advanced), Duration (≤10 min), Tags.
- Sort (visual): Popular, New, Shortest.
- Grid of course cards: title, subtitle, chip tags, est. time, progress bar (if enrolled).

### 5.3 Course Overview

- Hero: title, level, est. time, prerequisites chips.
- **Syllabus list** (use `<ol>`): lessons with length and a status dot (Locked/Available/Done—visual only).
- **Learning outcomes** bullets.
- CTA buttons: Start / Continue (anchors).

### 5.4 Lesson Player

- **Lesson header**: title, est. 7 min, progress bar (this lesson).
- **Section blocks** (use headings and paragraphs):

  - Concept
  - Example (code/diagram placeholder)
  - Mini-check (1 question radio; show static “Your answer: X” line)

- **Pager**: Previous / Next lesson (anchors).
- **Note panel**: key takeaways.
- **Inline glossary** using `<details>` for terms.

### 5.5 Quiz

- Question list:

  - Single choice (radio)
  - Multiple choice (checkbox)
  - True/False (radio)

- **Answer reveal placeholder**: a bordered box with “Sample explanation / Why this is correct.”
- **Score strip** (visual, not computed): “Your score: — / — (placeholder)”
- Submit/Reset buttons (non-functional).

### 5.6 Progress

- **Course progress bars** with % labels.
- **Badges** grid (Locked/Unlocked visual states).
- **Activity** list: “Completed: Lesson 1,” “Viewed Quiz 1.”
- **Certificate** placeholder card (“Available on completion”).

### 5.7 Settings

- Theme (Light/Dark, High contrast).
- Density (Comfortable/Compact).
- Notifications (lesson reminders) — visual switches.

### 5.8 About

- Micro-course philosophy.
- Accessibility and inclusive design note.
- Future features (AI tutor, adaptive quizzes).

---

## 6) Component Inventory

- **Header / Sidebar / Footer**
- **Course Card**: title, tags, est. time, progress bar
- **Lesson Pager**: prev/next anchors
- **Progress Bar**: thin and chunky variants
- **Badge**: locked/unlocked/earned styles
- **Quiz Block**: question stem, options list, explanation box
- **Filter Pills**: level, duration, tags
- **Stat Tiles**: streak, minutes learned, lessons completed
- **Alert/Toast** (visual only)
- **Table of Contents** (lesson outline with active state)

---

## 7) Data Model (future-ready; no code)

**Course**

- `id`, `title`, `subtitle`, `level`, `tags` (array), `estimatedMinutes`
- `syllabus` (array of `Lesson` IDs)
- `prerequisites` (array)

**Lesson**

- `id`, `courseId`, `title`, `sections` (array of content blocks)
- `estimatedMinutes`, `resources` (links), `quizId` (optional)

**Quiz**

- `id`, `lessonId`, `questions` (array of `Question`)

**Question**

- `id`, `type` (single|multi|tf), `stem`, `options` (array), `answerKey`, `explanation`

**Progress**

- `courseId`, `lessonId`, `status` (notStarted|inProgress|done), `percent`
- `lastViewedAt`

**User**

- `id`, `name`, `theme`, `badges` (array), `streakDays`, `minutesLearned`

---

## 8) CSS Architecture & Naming

- **BEM**: `.course-card__title`, `.badge--locked`, `.quiz__option--selected`

- Layers:

  1. `tokens.css` (colors/spacing/radii/typography)
  2. `base.css` (reset, base elements)
  3. `utilities.css` (grid/flex/spacing helpers)
  4. `components.css` (cards, bars, badges, quiz)
  5. `layouts.css` (header, sidebar, catalog grid)
  6. `themes.css` (light/dark/high-contrast)
  7. `print.css`

- **No JS tricks**; for collapsible content use `<details>` and anchor `:target` sections for basic step-through feel.

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Muted: #64748B
- Accent: #2563EB
- Success (completed): #16A34A
- Warning (pending): #F59E0B
- Danger (failed): #DC2626

**Dark**

- Background: #0B1220
- Surface: #111827
- Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Typography**

- H1: 24–28, H2: 20, Body: 16, Caption: 12–13
- Line height: 1.5–1.6, readable measure.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 10 (cards), 999 (pills)
- Shadows: subtle elevations

---

## 10) Accessibility & Semantics

- Landmarks: `<header>`, `<nav>`, `<main>`, `<aside>`, `<footer>`.
- Headings follow hierarchy; one H1 per page.
- Labels + descriptions for form controls.
- Do **not** use color alone for correctness—pair icons/text.
- Focus states high-contrast and always visible.
- Quiz options: use `<fieldset><legend>` with `<label>` per input.

---

## 11) Print Styles

- Hide sidebar/filters/buttons; show lesson content and quiz stems with selected answers.
- Include course title, lesson title, and date.
- Black-on-white, serif body optional.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Dashboard)
 ├─ catalog.html
 ├─ course.html          (Course Overview)
 ├─ lesson.html          (Lesson Player)
 ├─ quiz.html
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

## 13) Page Content Guidance (copy you can paste)

- **Lesson intro**: “You’ll learn X in \~7 minutes: concept → example → quick check.”
- **Quiz feedback placeholder**: “Correct answer: B. Because … (explanation).”
- **Progress copy**: “Complete all lessons to unlock your certificate.”
- **Badges**: “Starter • Streak 3 • Streak 7 • Course Finisher • Topic Explorer”

---

## 14) Acceptance Criteria (V1)

- Catalog lists ≥9 courses with varied tags/levels and static progress bars.
- Course Overview shows syllabus with statuses (Available/Locked/Done visual).
- Lesson Player renders at least 3 sections + mini-check.
- Quiz page includes ≥5 questions across types, with explanation boxes.
- Progress page shows % bars, badges, and activity.
- Print stylesheet produces a clean study handout for a lesson.

---

## 15) Future Enhancements

- JS scoring, persistence, and resume-where-you-left.
- **AI tutor**: hints, adaptive question difficulty, targeted revisions.
- Spaced-repetition scheduler and mastery criteria per skill.
- Certificates generation (PDF), shareable links.
- Offline-first PWA, keyboard-only lesson flow.
- Authoring mode for course creators.

---

## 16) Sample Static Data (to populate UI)

**Courses (cards)**

- “HTML Essentials (10m)” — Tags: Web, Beginner — Progress 20%
- “CSS Layout Quickstart (8m)” — Tags: Web, Beginner — Progress 0%
- “TypeScript Primitives (9m)” — Tags: Web, Intermediate — Progress 60%
- “Git in a Hurry (7m)” — Tags: Tools, Beginner — Progress 0%
- “Design Tokens Basics (6m)” — Tags: UI, Beginner — Progress 100%

**Lesson Sections**

- Concept: “What is a semantic element?”
- Example: “Compare `<div>` vs `<header>` in a simple layout.”
- Quick Check: “Which element defines page navigation?”

**Quiz Sample**

- Q1 (single): Best semantic element for main content? (A) `<main>` (B) `<div>` (C) `<section>`
- Q2 (multi): Which are inline elements? (A) `<span>` (B) `<em>` (C) `<article>`
- Q3 (T/F): `<nav>` is used for site navigation. (T/F)

---
