# Home Workout Buddy — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an **AR-assisted home workout coach** that uses the **phone camera** to guide form and count reps. V1 is **JavaScript-free**—all camera/AR/computer-vision features are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Deliver **safe, guided** home workouts with **visual form cues** over a live camera view.
- Keep sessions **simple**: warm-up → main sets → cool-down, with clear rest timers and rep targets.
- Encourage consistency with **streaks, badges, and progress**.
- Ship an **accessible, responsive, print-friendly** UI scaffold ready for later JS/CV integration.

---

## 2) Constraints (V1)

- **No JavaScript**; all camera, pose tracking, and timing are **non-functional placeholders**.
- Use native HTML (anchors, forms, `<details>`) and **pure CSS** for layout/visual states.
- No external UI frameworks; system font or a single webfont.

---

## 3) Personas & Core User Stories

**Personas**

- **Beginner at Home:** needs simple guidance and confidence (“am I doing it right?”).
- **Busy Professional:** wants quick 15-20 min routines with minimal setup.
- **Form-Focused Lifter:** wants angle cues and depth markers.

**Stories (visual-only in V1)**

1. **Setup & Calibrate**: phone on a stand → distance checklist → camera frame overlay (ghost silhouette).
2. **Start a Workout**: pick a routine (Full Body / Core / Mobility) and follow steps.
3. **Live Coach View**: see **camera preview placeholder** with **pose skeleton**, **joint angle badges**, and **form messages** (“Back straight”, “Knees track toes”).
4. **Rep/Set Tracking**: big counters, rest bar, next exercise preview.
5. **Progress**: weekly minutes, sessions, PR tiles, streak, badges.
6. **Library**: exercise technique cards with do/don’t visuals.

---

## 4) Information Architecture

- **Home / Today** — quick start, last workout, streak/nudge
- **Workouts** — presets (15m, 20m, 30m), focus (strength/core/mobility/HIIT)
- **Coach** — session player with **AR overlay** (camera placeholder)
- **Library** — exercises with technique cues & common faults
- **Plans** — multi-week programs (visual checklist)
- **Progress** — stats, charts (CSS blocks), badges
- **Prep** — camera setup, space & safety checklist
- **Settings** — units, difficulty, a11y, privacy (visual)
- **About** — method, safety disclaimer

**Global Shell**

- Header: app name, today’s date, print link
- Sidebar: nav + theme toggle (visual only)
- Main: page content
- Footer: help/version

---

## 5) Screen Blueprints

### 5.1 Home / Today

- **Quick Tiles**: “Start 15-min Full Body”, “Start Core 10-min”, “Prep Camera”
- **Streak & Minutes** strip (visual bar + day dots)
- **Nudge** (copy): “Tight hips? Add 3×30s hip flexor stretch.”

### 5.2 Workouts

- Filter chips: **Duration** (10/15/20/30), **Focus** (Strength/Core/Mobility/HIIT), **Equipment** (Bodyweight/DB/Band)
- **Routine Cards**:

  - Title, length, level (Beginner/Intermediate), equipment icons
  - Exercise list (e.g., “Squat • Push-up • Glute Bridge • Plank”)
  - CTA **Start** → anchors to Coach

### 5.3 Coach (Core)

- **Camera Stage (placeholder)**:

  - 16:9 viewport with **ghost silhouette** (target posture) and **pose skeleton lines** (CSS art)
  - **Angle badges** near joints (e.g., “Knee 90°”)
  - **Form Toast** (green = good / amber = adjust / red = stop) — text + icon, **not color-only**

- **Session HUD**:

  - **Exercise name** + set/rep target (“Squat • Set 1/3 • 12 reps”)
  - **Rep Counter** (big), **Set Progress Bar**, **Rest Timer** (visual ring)
  - **Next Up** with thumbnail and cues

- **Technique Panel** (collapsible):

  - “Cues: Chest up, sit back”
  - “Common faults: Heels lifting, knees cave”
  - **Safety** chip: “Pain? Stop.”

- **Controls** (visual only): Start • Pause • Skip • End

### 5.4 Library (Techniques)

- Exercise cards:

  - **Hero still** (photo placeholder) + **Do / Don’t** mini frames
  - Cues, faults, **Angle targets** (e.g., squat depth \~ parallel)
  - Equipment variations (Bodyweight / Dumbbell / Band)
  - `<details>` for progression/regression options

### 5.5 Plans

- 4-week tracks (visual checklist): **Beginner Bodyweight**, **Core & Mobility**, **DB Strength**
- Week → Day → Session list; each session links to a packed routine.

### 5.6 Progress

- **Tiles**: Total minutes, Sessions this week, Longest streak
- **Trends**:

  - Weekly minutes bars (CSS)
  - Exercise PRs table (best plank time, most reps, longest hold)

- **Badges**: “Week 1 Complete”, “Form Focused”, “Consistency 7d”

### 5.7 Prep (Setup & Safety)

- **Space Checklist**: clear 2×2m, good lighting, stable phone stand
- **Camera Angles**: front • 45° • side (icons)
- **Calibration** (visual only): “Stand in frame outline” → “Green frame fits”
- **Warm-up** suggestions (3-5 min)

### 5.8 Settings

- Units: kg/lb • cm/in
- Difficulty: Easy / Standard / Challenging (affects targets—copy only)
- A11y: Larger text, **reduced motion**, high contrast
- Privacy: Local-only video note (concept), export placeholders

### 5.9 About

- How form cues work (pose angles concept), limitations, **medical disclaimer**

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Routine Card**, **Exercise Card**
- **Camera Stage**: frame, ghost silhouette, pose skeleton, joint badges
- **Form Toast**: info/safe/adjust/stop variants (icon + text)
- **Rep Counter**, **Set Progress**, **Rest Ring**
- **Technique Panel** with cue list & faults
- **Badge** (locked/unlocked), **Nudge Banner**
- **Trend Bars**, **PR Table**
- **Checklist** (plans), **Calibration Frame**
- **Controls**: start/pause/skip/end buttons

---

## 7) Data Model (future-ready; no code)

**Exercise**

- `id`, `name`, `category` (squat/push/plank/hinge/pull), `equipment` (bw/db/band)
- `cues` (array), `faults` (array), `angleTargets` (e.g., `{knee: 85-100, hip: 80-95}`)
- `progressions` / `regressions` (ids), `media` (image refs)

**Routine**

- `id`, `title`, `level`, `durationMin`, `exercises` (array of `{exerciseId, sets, repsOrTime}`)

**SessionLog**

- `id`, `routineId`, `date`, `setsCompleted`, `reps`, `timeUnderTension`, `notes`

**FormAssessment (concept)**

- `sessionId`, `exerciseId`, `angles` (per rep), `flags` (e.g., kneesValgus, backRounded)

**User**

- `id`, `units`, `difficulty`, `a11yPrefs`, `privacyPrefs`, `streakDays`

**Stats**

- `dateRange`, `minutesPerDay`, `prRecords`, `badges`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.coach-stage`, `.pose__joint-badge`, `.form-toast--adjust`, `.hud__rep-counter`, `.rest-ring__fill`, `.tech-panel__cue`, `.trend__bar--week-2`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — cards, stage, toasts, counters, rings, trends, badges
  5. `layouts.css` — header/sidebar/coach grid
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — plan & progress reports

---

## 9) Design System

**Colors (Light)**

- Background: #F7FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent (action): #2563EB
- Success (good form): #16A34A
- Warning (adjust): #F59E0B
- Danger (stop): #DC2626
- Info (tips): #3B82F6

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Type & Sizing**

- Display: 28
- H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Counters use **tabular numerals** class.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Motion: keep subtle; provide reduced-motion theme.

---

## 10) Accessibility & Safety

- Landmarks: `<header> <nav> <main> <footer>`; single H1 per page.
- Big tap targets; visible focus; keyboard navigable.
- **Not color-only**: pair icons/text with green/amber/red toasts.
- **Reduced-motion** mode to avoid discomfort.
- **Safety copy** throughout: stop on pain, clear space, hydrate.
- Print “Form Cues” for offline reference.

---

## 11) Print Styles

- **Session Plan**: routine, exercises, sets/reps, technique cues, rest.
- **Progress Report**: sessions/week, PRs, notes area.
- Black on white; hide nav; page numbers.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Today)
 ├─ workouts.html        (Routines)
 ├─ coach.html           (Live Coach - AR placeholder)
 ├─ library.html         (Exercise Techniques)
 ├─ plans.html           (Programs)
 ├─ progress.html
 ├─ prep.html            (Setup & Safety)
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
     ├─ frames/          (ghost silhouettes, do/don’t stills)
     ├─ icons/
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Prep tip:** “Place phone at hip height, 2–3 m away, with good side lighting.”
- **Form toast (good):** “Nice depth! Knees tracking toes.”
- **Form toast (adjust):** “Back rounding—brace core, hinge at hips.”
- **Form toast (stop):** “Sharp pain? **Stop** and modify.”
- **Cue (squat):** “Spread floor with feet; keep chest proud.”
- **Nudge:** “Short on time? 8-minute EMOM: Squat • Push-up • Hollow Hold.”

---

## 14) Acceptance Criteria (V1)

- Home shows **3 quick tiles**, streak strip, and a nudge.
- Workouts lists **≥9 routines** with mixed durations/focus; each card shows 4+ moves.
- Coach page renders **camera stage** with ghost silhouette, pose skeleton, **3 toast variants**, big rep counter, rest ring, next-up.
- Library lists **≥12 exercises** each with cues, faults, and do/don’t stills.
- Plans page shows **3 programs** with 4 weeks of checklists (visual).
- Progress shows tiles, weekly minutes bars, and PR table.
- Prep page shows camera/space checklist and calibration frame.
- Print styles output a clean session plan & progress report.

---

## 15) Future Enhancements

- WebRTC camera feed; on-device **pose estimation** (MoveNet/BlazePose).
- Real-time **angle calculations** & **fault classifiers** (knees valgus, lumbar flexion).
- Auto **rep counting** & **tempo** detection; rest timers with haptics.
- Personalized progressions; **AI coach** nudges based on history & fatigue.
- Integrations: Apple Health / Google Fit / Strava (read workouts, write minutes).
- Offline PWA, video form replays, coach comments.

---

## 16) Sample Static Data (populate UI)

**Routines (cards)**

- Full Body 15m (BW) — Squat • Push-up • Glute Bridge • Forearm Plank
- Core 12m — Dead Bug • Side Plank • Hollow Hold • Bird Dog
- Mobility 10m — Hip Flexor • T-Spine Opener • Hamstring Sweep

**Exercises (library)**

- **Squat** — Cues: Chest up, sit back. Faults: Heels lift, knees cave. Angles: Knee \~90–100°.
- **Push-up** — Cues: Straight line, elbows \~45°. Faults: Sagging hips.
- **Lunge** — Cues: Vertical shin, tall torso. Faults: Knee collapse.
- **Hinge (RDL)** — Cues: Hips back, neutral spine. Faults: Back round.
- **Plank** — Cues: Ribs down, glutes on. Faults: Hip pike.

**PRs (example)**

- Longest plank: **1:20** • Max push-ups set: **18** • Most squats 60s: **34**

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) so you can drop it straight into Cursor.
