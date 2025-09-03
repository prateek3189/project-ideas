# Sleep Coach — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a sleep coach that **analyzes patterns** (visual only), suggests **bedtime routines**, and offers **calming music/white noise**. V1 is **JavaScript-free**—all analytics, timers, sensors, and audio logic are **placeholders** you can wire up later.

---

## 1) Vision & Goals

- Reduce bedtime friction with a **simple wind-down plan** and **soothing soundscapes**.
- Show **patterns** (sleep/wake time, duration, quality cues) in a friendly, non-judgmental way.
- Keep UI **accessible, responsive, printable**, and easy to enhance later with JS/AI.

---

## 2) Constraints (V1)

- **No JavaScript**: no real tracking, timers, audio mixing, or integrations.
- Use native HTML (`<details>`, forms, tables, `<audio>` optional with placeholder files) and pure CSS.
- No external UI frameworks; system font or a single webfont.

---

## 3) Personas & Core User Stories

- **Busy Professional:** “Give me a quick routine and a consistent lights-out.”
- **Student:** “Block late-night doomscrolling; fall asleep faster.”
- **New Parent:** “Short, flexible wind-down; gentle white noise.”

**Stories (visual-only in V1)**

1. View **Tonight**: suggested **bedtime**, **wind-down steps**, and a **soundscape**.
2. Open **Sounds**: pick **calming music** or **white noise**; set **duration** (visual).
3. Log sleep (static): bedtime, wake time, disturbances, caffeine.
4. See **Insights**: weekly patterns, **sleep debt** and **chronotype guess** (copy-only).
5. Print a **weekly sleep report** for a doctor/coach.

---

## 4) Information Architecture

- **Home / Tonight** — suggested bedtime, wind-down plan, quick sounds
- **Wind-down Planner** — build/edit routine (steps + timing)
- **Sounds & Noise** — calming music, white noise, nature loops (placeholders)
- **Sleep Log** — manual entries; tags (caffeine, late screen, workout)
- **Insights** — weekly/monthly trends, bedtime consistency, sleep debt (visual)
- **Settings** — reminders, themes, accessibility, privacy (visual)
- **About** — method, disclaimers, good-sleep hygiene tips

**Global Shell**

- Header: app name, date picker, print link
- Sidebar: navigation + theme toggle (visual)
- Main: page content
- Footer: help/version

---

## 5) Screen Blueprints

### 5.1 Home / Tonight

- **Suggested Bedtime** pill (e.g., “10:45 PM”) with “why” `<details>` (chronotype/consistency copy).
- **Wind-down Plan (45 min)**:

  1. Lights dim & devices off (15m)
  2. Warm shower & light stretch (10m)
  3. Breathing 4-7-8 (5m)
  4. Read (paper) (10–15m)

- **Quick Sounds** row: “Rain”, “Brown Noise”, “Piano Calm” (play icons visual only).
- **Nudge** banner: “Caffeine after 4 PM can delay sleep.”

### 5.2 Wind-down Planner

- Routine builder cards:

  - **Step**: title, duration chip, small description.
  - Reorder handles (visual), enable/disable toggle (visual).

- Presets: **Classic Calm**, **Phone-Free**, **Traveler**, **New Parent (Short)**.
- Bedtime target selector (pill buttons): 10:00 • 10:30 • 11:00.

### 5.3 Sounds & Noise

- **Tabs**: Calming Music • White/Brown/Pink Noise • Nature (Rain/Ocean/Forest/Fan)
- **Sound Card**: title, loop badge, duration chips (30/60/120m), volume slider look, **mix with** (visual chips, e.g., Rain+Piano).
- Optional `<audio controls>` with placeholder file (no custom JS).

### 5.4 Sleep Log

- **Entry Form**:

  - Bedtime (time), Wake time (time), Awakenings (#), Perceived quality (1–5)
  - Tags (checkbox): caffeine late • heavy dinner • workout • screens in bed
  - Notes (textarea)

- **Diary Table**: date, in-bed duration, estimated sleep duration, quality, tags.
- **Weekly Totals** (visual): average duration, bedtime consistency.

### 5.5 Insights

- **Tiles**: Average duration, Bedtime consistency, Wake consistency, Sleep debt (copy math).
- **Trend Strip**: 7-day bars for duration; small circles for bedtime variance.
- **Chronotype** (copy): “You trend toward **early-intermediate**.”
- **Suggestions** list:

  - “Shift bedtime by 15 min earlier for 3 nights.”
  - “Keep phone outside bedroom.”
  - “Try brown noise instead of white if highs feel harsh.”

### 5.6 Settings

- **Reminders** (visual switches): begin wind-down, lights-out, morning light.
- **Theme**: Light/Dark/High-contrast • **Reduced Motion**.
- **Accessibility**: Larger text, dyslexia-friendly font (visual).
- **Privacy**: local-only note (concept), export placeholders (CSV/JSON).

### 5.7 About

- Sleep hygiene mini-guide, how suggestions are derived (concept), not medical advice.

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Suggested Bedtime** pill, **Nudge** banner
- **Routine Step** card (title, duration chip, toggle)
- **Sound Card** with loop/duration/volume (visual)
- **Tile** (KPIs), **Trend Bars**, **Consistency Dots**
- **Diary Table**, **Tag Chips**
- **Badge** (streak: nights logged), **Chronotype** label
- **Print Header/Footer** for weekly report

---

## 7) Data Model (future-ready; no code)

**SleepSession**

- `id`, `date`, `bedTime`, `wakeTime`, `awakenings`, `quality1to5`, `tags[]`, `notes`

**Routine**

- `id`, `name`, `targetBedTime`, `steps[]` ( `{title, minutes, enabled}` )

**Sound**

- `id`, `category` (music|noise|nature), `title`, `durationPreset[]`, `loop`, `mixWith[]`

**Insights**

- `dateRange`, `avgDurationMin`, `bedtimeStdDevMin`, `wakeStdDevMin`, `sleepDebtMin`, `chronotypeLabel`, `suggestions[]`

**User**

- `id`, `reminders` (winddown/lightsOut/morning), `theme`, `a11yPrefs`, `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.bedtime-pill`, `.routine-step__title`, `.sound-card__controls`, `.trend__bar--day-4`, `.consistency__dot--offtarget`, `.tile--sleep-debt`, `.badge--streak`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — flex/grid/gap/visually-hidden
  4. `components.css` — pills, cards, tiles, charts, tables, chips, banners
  5. `layouts.css` — header/sidebar/content grids
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — weekly report

---

## 9) Design System (Calm & Night-friendly)

**Colors (Light)**

- Background: #F6F8FB
- Surface: #FFFFFF
- Text: #0F172A
- Accent (calm): #5B7BD5
- Secondary: #7AC3B2
- Warning (late caffeine): #F59E0B • Info: #38BDF8

**Dark**

- Background: #0B1020 • Surface: #121826 • Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Generous line-height 1.5–1.7; tabular numerals for times.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 14 (cards), 999 (chips)
- **Reduced Motion** theme variant.

---

## 10) Accessibility & Well-being

- Landmarks: `<header> <nav> <main> <footer>`; one H1 per page.
- High-contrast focus rings; large tap targets; keyboard navigable.
- Do not rely on color alone—pair text/icons with chart states.
- Compassionate copy (no shaming), optional neutral “quality” labels.

---

## 11) Print Styles

- **Weekly Sleep Report**: date range, nightly table (times/duration/notes), averages, consistency dots, suggestions.
- Black on white; hide nav; include page numbers and footer note: “Sleep Coach – v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Tonight)
 ├─ planner.html         (Wind-down Planner)
 ├─ sounds.html          (Calming Music & White Noise)
 ├─ log.html             (Sleep Log)
 ├─ insights.html
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
     ├─ illustrations/
     └─ audio-placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Tonight (why bedtime):** “Target aligns with your recent average wake time and desired 7h 30m.”
- **Wind-down tip:** “Dim lights and put phone away 45 minutes before bed.”
- **Sound hint:** “Brown noise reduces harsh highs; many find it gentler than white noise.”
- **Insight note:** “Consistency beats perfection—±30 minutes counts as ‘on time’.”
- **Nudge:** “Caffeine cutoff: \~6–8 hours before bedtime.”

---

## 14) Acceptance Criteria (V1)

- Home shows **suggested bedtime**, a **4-step wind-down**, and **3+ quick sounds**.
- Planner lets users view **presets** and **step cards** with durations (visual).
- Sounds page lists **≥9 sound cards** across categories with loop/duration chips.
- Log page has a **form** and a **weekly diary table** with totals.
- Insights shows **tiles**, **7-day duration bars**, and **consistency dots** plus suggestions.
- Print stylesheet outputs a **weekly sleep report** cleanly.
- Meets basic a11y checks (headings, labels, focus, contrast).

---

## 15) Future Enhancements

- Real analytics: automatic sleep/wake via wearable or device motion.
- AI suggestions: bedtime shifts, caffeine cutoff, light exposure timing.
- Smart routines: adapt step lengths to adherence and next-day alertness.
- Audio engine: cross-fade loops, multi-mix (rain+brown noise).
- Integrations: Apple Health / Google Fit for sleep data import.
- Morning check-in + daytime light/exercise nudges.

---

## 16) Sample Static Data (populate UI)

**Week (sleep log)**

- Mon 11:15 PM → 6:40 AM (7h 25m) • Quality 4 • Tags: _workout_
- Tue 12:05 AM → 6:45 AM (6h 40m) • Quality 3 • Tags: _screens_
- Wed 10:55 PM → 6:30 AM (7h 35m) • Quality 4 • Tags: _none_
- Thu 11:40 PM → 6:20 AM (6h 40m) • Quality 3 • Tags: _late caffeine_
- Fri 12:20 AM → 7:30 AM (7h 10m) • Quality 4 • Tags: _none_

**Routine (Classic Calm, 45m)**

- Devices off (15m) → Shower/stretch (10m) → 4-7-8 breathing (5m) → Read (15m)

**Sounds**

- **Calming Music**: Piano Calm • Night Strings • Ambient Pad
- **Noise**: White • Brown • Pink
- **Nature**: Rain • Ocean • Forest • Fan

---

If you’d like, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) for Cursor.
