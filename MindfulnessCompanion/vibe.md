# Mindfulness Companion — Project Document (Plain HTML & CSS)

> **Goal:** Create a **static HTML + CSS v1 prototype** for a calm, guided experience that offers **meditation sessions**, **breathing exercises**, and **stress-level tracking**. V1 is **JavaScript-free**—all timers, audio, sensors, and analytics are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Help users reduce stress via **short, guided practices** they can do anywhere.
- Provide **gentle structure**: daily plan, quick breathing, and longer meditations.
- Show **stress trends** with compassionate language—not guilt.
- Deliver **accessible, responsive, printable** UI scaffolding that’s easy to enhance later.

---

## 2) Constraints (V1)

- **No JavaScript**. All countdowns, audio, HRV/sensor reads are **non-functional**.
- Use native HTML patterns (`<details>`, forms, tables) and CSS only.
- No external UI frameworks; system fonts or one webfont.

---

## 3) Personas & Core User Stories

- **Busy Professional:** “Give me a 1–3 minute reset between meetings.”
- **Student:** “I need help winding down and tracking my stress before exams.”
- **Wellness Seeker:** “I want a gentle routine and to see progress.”

**Stories (visual-only in V1):**

1. Start a **guided meditation** (5, 10, 15 min) with script preview and audio icon.
2. Do a **breathing exercise**: box/4-7-8/coherence with a visual breath ring.
3. Record **stress & mood** (slider + notes) and view a weekly trend.
4. Follow a **Daily Plan**: quick breathe → short meditation → gratitude note.
5. Print a **weekly reflection** (practices + notes + trend).

---

## 4) Information Architecture

- **Home / Today** — quick start tiles, daily plan, nudge
- **Meditate** — session catalog (themes, durations)
- **Breathe** — breathing patterns library and visual coach
- **Check-in** — stress & mood entry; brief journal
- **Insights** — trends (weekly/monthly), streak, badges (visual)
- **Library** — scripts (body scan, loving-kindness, focus), music/soundscapes (placeholders)
- **Settings** — reminders, themes, accessibility, privacy (visual)
- **About** — method, evidence note, disclaimers

**Global Shell**

- Header: app name, date, print link
- Sidebar: navigation + theme toggle (visual only)
- Main: page content
- Footer: help/version

---

## 5) Screen Blueprints

### 5.1 Home / Today

- **Quick Start Tiles**:

  - “Breathe 1 min” • “Meditate 5 min” • “Check-in now”

- **Daily Plan** (3 steps):

  1. Breathe (1–2 min)
  2. Meditate (5–10 min)
  3. Reflect (2 prompts)

- **Nudge** (copy): “Feeling tense? Try 4 slow breaths.”

### 5.2 Meditate (Catalog)

- Filters: **Theme** (Calm, Focus, Sleep, Gratitude), **Duration** (3–20 min).
- **Session Cards**:

  - Title, duration, brief description, tags (voice/music/silent), CTA **Start**
  - “Script preview” via `<details>` (first paragraph)

- **Session Page (static)**:

  - Header with duration pill and **audio icon** (placeholder)
  - Script sections with gentle headings
  - “Bell at start/end” icons (visual)
  - Pager: Previous/Next session

### 5.3 Breathe (Coach)

- **Pattern Selector** chips:

  - **Box 4-4-4-4** • **4-7-8** • **Coherence 5-5** • **Triangle 4-4-8**

- **Breath Ring** (CSS animation placeholder):

  - “Inhale • Hold • Exhale” labels
  - Count badges (visual only)

- **Guide Options** (visual): voice on/off, bell on/off, pace: slow/medium/fast
- **Tips Panel**: “Breathe through nose, relax shoulders.”

### 5.4 Check-in (Stress & Mood)

- **Stress Slider** (0–10): low → high
- **Mood Chips**: Calm • Neutral • Anxious • Low • Energized
- **Body Map** (optional static image) with checkboxes: head, neck, chest, stomach, shoulders
- **Journal** (textarea placeholder): “What’s on your mind?”
- **Save** button (visual) → anchor back to Today

### 5.5 Insights

- **Tiles**: “Streak days”, “Avg daily minutes”, “Avg stress (week)”
- **Trend Blocks**:

  - 7-day **stress line** (CSS bar/line look)
  - Practice time bars (per day)
  - **Breath vs Stress** correlation note (copy-only)

- **Badges** (visual): “Week of Calm”, “Daily Breather”, “Night Owl”

### 5.6 Library

- **Meditations** list with tags (Body Scan, Loving-Kindness, Focus, Sleep)
- **Soundscapes** (placeholders): Rain, Ocean, Forest, White Noise
- **Favorites** section (star icons visual)

### 5.7 Settings

- **Reminders**: morning/evening (visual switches)
- **Theme**: Light/Dark/High-contrast
- **Accessibility**: Larger text, reduced motion, dyslexia-friendly font (visual)
- **Privacy**: local-only data note (copy), export placeholder

### 5.8 About

- How mindfulness helps; be-kind-to-yourself message
- Not medical advice; seek professional help if needed

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Quick Tile** (Today)
- **Session Card** (Meditate/Library)
- **Breath Ring** + **Phase Labels**
- **Count Pill** (inhale/hold/exhale)
- **Stress Slider** + **Mood Chip**
- **Body Map** checklist
- **Trend Bars/Line** (CSS only)
- **Stat Tile** / **Badge** (locked/unlocked)
- **Toast/Nudge** banner
- **Print Header/Footer** for reflection report

---

## 7) Data Model (future-ready; no code)

**Session (Meditation)**

- `id`, `title`, `theme`, `durationMin`, `hasVoice`, `script` (sections)

**BreathingPattern**

- `id`, `name`, `inhaleSec`, `holdSec`, `exhaleSec`, `cycles`

**CheckIn**

- `id`, `datetime`, `stress0to10`, `moodTag`, `bodyAreas` (array), `note`

**PracticeLog**

- `date`, `minutesMeditated`, `minutesBreathing`, `streakDay` (bool)

**User**

- `id`, `reminders` (am/pm), `theme`, `a11yPrefs`, `privacyPrefs`

**Insights**

- `dateRange`, `avgStress`, `minutesPerDay`, `streakDays`, `badges`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.tile--today`, `.session-card__meta`, `.breath-ring__phase--inhale`, `.checkin__slider`, `.trend__bar--day-3`, `.badge--locked`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — flex/grid/gap/visually-hidden
  4. `components.css` — tiles, cards, sliders, ring, charts, badges
  5. `layouts.css` — header/sidebar/content grids
  6. `themes.css` — light/dark/high-contrast
  7. `print.css` — reflection/weekly report

---

## 9) Design System (Calm & Accessible)

**Colors (Light)**

- Background: #F6FAF8
- Surface: #FFFFFF
- Text: #0F172A
- Primary (calm): #4F9A94
- Accent: #6C8EE7
- Success: #22C55E • Warning: #F59E0B • Info: #38BDF8

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Typography**

- Display: 28
- H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Generous line-height (1.5–1.7); ample white space.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 14 (cards), 999 (pills)
- Soft shadows; **reduced motion** variant in themes.

---

## 10) Accessibility & Well-Being

- Landmarks: `<header> <nav> <main> <footer>`; one H1 per page.
- Large tap targets; visible focus rings; keyboard navigable.
- **Reduced Motion** theme: disable animations (important for vestibular comfort).
- Do not rely on color alone for state; add text/icons.
- Compassionate language; no guilt in copy or metrics.

---

## 11) Print Styles

- **Weekly Reflection**: date range, total minutes, average stress, notes (lined area).
- **Practice Log** table: days × minutes and check-ins summary.
- Hide navigation; black on white; page numbers/footer.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Today)
 ├─ meditate.html        (Catalog + Session)
 ├─ breathe.html         (Breathing Coach)
 ├─ checkin.html         (Stress & Mood)
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
     └─ illustrations/
```

---

## 13) Page Copy (paste-ready snippets)

- **Nudge (Today):** “Unclench your jaw. Drop the shoulders. Inhale gently for 4.”
- **Meditation intro:** “Notice the breath at the nose. Thoughts can pass like clouds.”
- **Breathing tip:** “Try 4-7-8: inhale 4, hold 7, exhale 8. Slow and quiet.”
- **Check-in prompt:** “Name it to tame it—what word fits your mood?”
- **Insight note:** “Consistency beats intensity. Two minutes counts.”

---

## 14) Acceptance Criteria (V1)

- Home shows **3 quick tiles** + a **daily plan** and a gentle nudge.
- Meditate lists **≥9 sessions** with mixed themes/durations; session page shows script preview.
- Breathe page shows **≥4 patterns**, a **breath ring**, and **phase labels**.
- Check-in records (visually) **stress slider**, **mood chips**, **journal**.
- Insights shows **trend blocks**, **tiles**, and **2+ badges** (visual).
- Library lists **meditations** and **soundscapes** placeholders.
- Print stylesheet outputs a clean weekly reflection & practice log.

---

## 15) Future Enhancements

- Real timers, audio playback, and gentle start/end bells.
- HR/HRV import (Apple Health/Google Fit) to infer **stress variability**.
- Adaptive plans: suggest pattern/session based on recent check-ins.
- Breath pacing animation tied to actual time; haptics on supported devices.
- On-device first; privacy-respecting sync and export.
- Clinician/coach sharing link and “SOS 60-sec reset” flow.

---

## 16) Sample Static Data (populate UI)

**Meditation Sessions**

- Body Scan (10m) • Loving-Kindness (7m) • Box Breathing Focus (5m)
- Sleep Wind-down (12m) • Gratitude (5m) • Mountain Visualization (8m)
- Micro Pause (2m) • Open Awareness (15m) • Calm Before Meeting (3m)

**Breathing Patterns**

- Box 4-4-4-4 • 4-7-8 • Coherence 5-5 • Triangle 4-4-8

**Check-ins (example week)**

- Mon: Stress 6 • Mood “Anxious”
- Tue: Stress 4 • Mood “Neutral”
- Wed: Stress 3 • Mood “Calm”
- Thu: Stress 7 • Mood “Low”
- Fri: Stress 5 • Mood “Calm”

**Badges (visual)**

- “Daily Breather (3d)” • “Week of Calm (7d)” • “Night Wind-down (3 sessions)”

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) for Cursor.
