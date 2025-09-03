# AI Personal Coach — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an AI coach that gives **daily advice** across **Fitness**, **Productivity**, and **Leadership** based on user data (visual only). V1 is **JavaScript-free**—all data syncing (wearables/calendars/mood logs), analytics, notifications, and AI reasoning are **placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Deliver **one focused daily plan** per track (Fitness, Productivity, Leadership) with **micro-actions**.
- Visualize **progress, streaks, and trends** with compassionate framing (no shame).
- Make it **personal** via “why this” notes (copy) tied to mock data.
- Keep UI **accessible, responsive, and printable** with clean theming.

---

## 2) Constraints (V1)

- **No JavaScript**: no real device integrations, schedules, or notifications.
- Use semantic HTML (`<details>`, `<form>`, tables) and **pure CSS** for charts/meters.
- All “AI” content is **static copy**; labels like “generated” are UI only.

---

## 3) Personas & Core User Stories

- **Busy Professional**: “Give me a light plan I can actually finish.”
- **Student/Founder**: “Keep me focused; protect deep work.”
- **Team Lead**: “Help me coach my team; prompt better 1:1s.”

**Stories (visual-only)**

1. See **Today’s Plan** for selected tracks with 3–5 actionable steps.
2. Log a quick **Check-in** (sleep, mood, energy) → **Daily Suggestion** cards update (copy).
3. Review **Insights**: trends, streaks, habit adherence.
4. Browse **Coach Library**: bite-size tactics (e.g., Pomodoro, feedback frameworks).
5. Print a **Weekly Plan** and **Progress Report**.

---

## 4) Information Architecture

- **Home / Today** — daily plan + check-in + nudges
- **Tracks** — Fitness • Productivity • Leadership (switch view)
- **Plans** — weekly planner (mock scheduling)
- **Insights** — adherence, streaks, energy trends (CSS charts)
- **Library** — tactics, frameworks, templates
- **Settings** — tracks on/off, themes, privacy (visual)
- **About** — methodology, disclaimers

**Global Shell**
Header: app name, date switcher, print link
Sidebar: nav + theme toggle (visual)
Main: page content
Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Home / Today (Core)

- **Daily Header**: date pill, “You chose: Fitness + Productivity” chips.
- **Check-in Card**: Sleep (hrs), Mood (chips), Energy (low/med/high), Note (textarea).
- **Coach Feed** (3 columns by track):

  - **Fitness Coach Card**: “30-min zone-2 walk,” “8k steps,” “Protein 25–30g/meal.”
  - **Productivity Coach Card**: “Define top-1 outcome,” “90-min deep work,” “Inbox sweep.”
  - **Leadership Coach Card**: “1:1 agenda: wins → blocks → asks,” “Give 1 specific praise.”
  - Each card shows **Why this** `<details>` (e.g., “low energy → lighter load”).

- **Micro-Habits Row**: toggle-style checkmarks (visual).
- **Nudge Banner**: gentle, time-boxed tip (copy-only).

### 5.2 Tracks

- **Fitness**: goals (steps, cardio, strength), plan blocks (Mon/Wed/Fri), hydration/sleep targets.
- **Productivity**: focus blocks table, priority list, “meeting diet” note.
- **Leadership**: 1:1s, feedback templates (SBI), team pulse (copy), weekly retro prompts.

### 5.3 Plans (Weekly Planner)

- Week grid (Mon–Sun).
- Drag-drop is **visual**: plan cards with time chips and category color bars.
- “Auto-balance” badge (copy) and **Print Weekly Plan** link.

### 5.4 Insights

- **Tiles**: Streak (days), Adherence %, Avg sleep, Focus hours (mock).
- **Charts** (CSS only):

  - **Streak Ring** (conic gradient).
  - **Weekly Bars**: focus hours / workouts completed.
  - **Energy vs Output** strip (dots/lines visually).

- **Highlights** list: “Deep work increased 20% vs last week” (copy inference).

### 5.5 Library

- **Playbooks** (cards with `<details>` expanders):

  - Productivity: **Timeboxing**, **Pomodoro 50/10**, **Kill-Switch for Distractions**.
  - Fitness: **Zone 2 basics**, **Protein target guide**, **Mobility 8**.
  - Leadership: **SBI Feedback**, **Weekly 1:1 template**, **Decision log**.

- **Templates**: daily plan, retro, 1:1 agenda (print-friendly).

### 5.6 Settings

- Tracks on/off, default track order, reminder preferences (visual).
- Theme: Light/Dark/High-contrast; Reduced Motion.
- Privacy note: local-only concept; export placeholders (CSV/JSON).

---

## 6) Component Inventory (CSS-only)

- **Coach Card** (title, steps, “why this” `<details>`)
- **Check-in Chip** (mood/energy), **Stat Tile**, **Streak Ring**
- **Micro-Habit Row** (checkbox look), **Nudge Banner**
- **Plan Card** (time chip, category color), **Weekly Grid**
- **Chart Bars/Dots** (utilities), **Template Card**
- **Print Header/Footer** (weekly plan & report)

---

## 7) Data Model (future-ready; no code)

**User**

- `id`, `tracks[]` (fitness|productivity|leadership), `prefs` (theme, reminders)

**CheckIn**

- `date`, `sleepHrs`, `mood` (enum), `energy` (low|med|high), `note`

**Goal**

- `id`, `track`, `title`, `target`, `unit`, `period` (daily/weekly)

**Habit**

- `id`, `track`, `name`, `schedule` (days), `streak`, `adherence%`

**PlanItem**

- `id`, `track`, `date`, `timeBlock` (e.g., “08:00–09:30”), `title`, `intensity` (low|med|high)

**Suggestion**

- `id`, `track`, `title`, `steps[]`, `whyThis`, `tags[]`, `priority`

**Metric**

- `date`, `focusMins`, `steps`, `workouts`, `proteinGrams`, `meetingsCount`

**Insight**

- `dateRange`, `highlights[]`, `warnings[]`

**Content**

- `id`, `type` (playbook|template), `title`, `body`, `track`, `tags[]`

---

## 8) CSS Architecture & Naming

- **BEM examples**:
  `.coach-card`, `.coach-card__why`, `.checkin__chip--active`, `.streak-ring`,
  `.plan-card__time`, `.chart__bar--focus`, `.nudge--info`, `.tile--adherence`
- Layers:

  1. `tokens.css` (colors, spacing, radii, type)
  2. `base.css` (reset, base elements)
  3. `utilities.css` (grid/flex/gap/visually-hidden)
  4. `components.css` (cards, tiles, chips, banners, charts)
  5. `layouts.css` (shell, columns, grids)
  6. `themes.css` (light/dark/high-contrast/reduced-motion)
  7. `print.css` (weekly/summary)

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Fitness accent: #10B981 • Productivity: #2563EB • Leadership: #8B5CF6
- Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Type**

- Display 28 • H1 24 • H2 20 • Body 16 • Caption 12–13
- **Tabular numerals** for times/counters.

**Spacing & Radius**

- Scale: 4/8/12/16/24/32; Radius: 12 (cards), 999 (chips).
- Reduced-motion variant; visible focus rings.

---

## 10) Accessibility & Tone

- Landmarks `<header><nav><main><footer>`; single H1/page.
- Labels for all inputs; keyboard navigable; high-contrast focus.
- Do not rely on color alone—pair icons/text on charts.
- **Compassionate copy**: nudge, never shame; allow **skip/replace** actions.

---

## 11) Print Styles

- **Weekly Plan**: day grid with plan items by track + micro-habits checklist.
- **Progress Report**: tiles (streak, adherence), weekly bars, highlights list.
- Hide nav; black on white; page numbers & footer “AI Personal Coach — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html          (Home / Today)
 ├─ tracks.html         (Fitness / Productivity / Leadership)
 ├─ plans.html          (Weekly Planner)
 ├─ insights.html
 ├─ library.html
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

- **Today nudge:** “Aim for **one** meaningful win. Small steps compound.”
- **Why this (Fitness):** “Energy checked **Low** → choose zone-2 walk + mobility.”
- **Why this (Productivity):** “High meeting load today → protect one **90-min** deep-work block.”
- **Why this (Leadership):** “Team retro tomorrow → prepare **SBI** feedback for 1 teammate.”
- **Check-in prompt:** “How did you sleep? How’s your energy?”
- **Library intro:** “Playbooks are proven tactics. Pick **one** and try it for a week.”
- **Compassion note:** “Plans are guides, not rules. Adjust without guilt.”

---

## 14) Acceptance Criteria (V1)

- Home shows **Check-in** and **Coach Feed** with at least **3 cards** (one per track).
- Tracks page renders **Fitness/Productivity/Leadership** detail views with goals and plan blocks.
- Plans page provides a **weekly grid** and at least **6 plan cards** (visual).
- Insights page displays **4 tiles**, **2 charts**, and **Highlights** list.
- Library shows **≥9** playbooks/templates with `<details>` content.
- Print styles output **Weekly Plan** and **Progress Report** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real integrations: **HealthKit/Google Fit**, calendar, task managers; email/slack nudges.
- AI personalization: **context-aware plans**, habit difficulty scaling, recovery days.
- Streak protection & **grace windows**; relapse-proof habit math.
- Meeting load analysis; **focus budget** auto-allocation.
- Leadership: pulse surveys, 1:1 auto-drafts, feedback suggestions (SBI → examples).
- Privacy: on-device scoring, encrypted sync, data retention controls.
- Mobile PWA; offline mode; export to PDF/Notion.

---

## 16) Sample Static Data (populate UI)

**Check-in (today)**

- Sleep: **6.5h** • Mood: **anxious** • Energy: **low** • Note: “late meeting”

**Coach Feed (cards)**

- **Fitness** — _Today’s Focus_: 30-min zone-2 walk; 8,000 steps; Mobility-8.
  _Why this:_ “Low energy + short sleep → gentle cardio + mobility.”
- **Productivity** — _Today’s Top-1_: Finish proposal draft; 90-min block 10:00–11:30; Inbox sweep (15m).
  _Why this:_ “3 meetings afternoon → block deep work in the morning.”
- **Leadership** — _People First_: Send 1 SBI praise; Prep 1:1 agenda; Ask one unblocker Q.
  _Why this:_ “Retro tomorrow → nudge psychological safety.”

**Goals (weekly)**

- Workouts **3/3** • Focus hours **7.5/8** • 1:1s **2/2** • Feedback notes **2/2**

**Insights (mock)**

- Streak: **6 days** • Adherence: **78%** • Avg sleep: **7.1h** • Focus hrs: **8.2**

---

If you want, I can also turn this into a **ready-to-paste README.md** or generate **plain HTML page skeletons** (still no JS) that match this IA.
