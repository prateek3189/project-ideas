# AI Nutrition Guide — Project Document (Plain HTML & CSS)

> **Goal:** Create a **static HTML + CSS v1 prototype** for an app that logs meals with **photo recognition placeholders**, suggests **healthier alternatives**, and shows **fitness-app sync** (visual only). No JavaScript—just clean, semantic markup and styles you can paste into **Cursor** and wire up later.

---

## 1) Vision & Goals

- Make food logging **fast** (add by photo or quick search).
- Encourage **better choices** with clear, compassionate **swap suggestions**.
- Show **progress**: calories, macros, fiber, hydration, and activity.
- Keep everything **accessible, printable, and privacy-aware**.

---

## 2) Constraints (V1)

- **No JavaScript.** All “AI recognition,” sync, and calculations are **visual placeholders**.
- Use native HTML patterns (`<details>`, forms, tables) and CSS only.
- No external UI frameworks; system fonts or one webfont max.

---

## 3) Personas & Core User Stories

**Personas**

- **Busy Professional**: “Snap and log—don’t make me type.”
- **Health Seeker**: “Show me **simpler swaps** that fit my cuisine.”
- **Athlete in Training**: “Macros + workout sync (read-only in V1).”
- **Parent**: “Family plates; split portions.”

**Stories (visual-only)**

1. **Log a meal** via photo or quick search; review recognized items and portions.
2. See **nutrition breakdown** and **healthy alternatives** (swap chips).
3. Track **hydration** and **mood/satiety** (smiley scale).
4. Browse **daily diary**; print a clean summary.
5. View **weekly insights**: calories trend, macro balance, fiber score, top swaps.
6. See **Fitness sync** badges (Apple Health / Google Fit / Strava placeholders).

---

## 4) Information Architecture

- **Onboarding** — diet preference, allergies, goals, cuisine
- **Dashboard** — today’s calories/macros, water, steps (sync placeholder), quick add
- **Log Meal** — photo upload, recognition review, portions, notes
- **Food Details & Swaps** — nutrient panel + “healthier alternatives”
- **Diary** — day view by meals (Breakfast/Lunch/Dinner/Snacks)
- **Insights** — weekly charts (CSS blocks), badges, streaks
- **Integrations** — fitness app connections (visual toggles)
- **Settings** — units, goals, themes, privacy/export (visual)
- **About** — method & disclaimers

**Global Shell**

- Header: app name, date picker, print link
- Sidebar: nav + theme toggle (visual only)
- Main: page content
- Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Onboarding

- **Dietary Profile** (radios): Balanced • Veg • Vegan • High-Protein • Low-Carb
- **Cuisine Focus** (chips): Indian • Mediterranean • Continental • Asian
- **Allergies/Exclusions** (chips): Nuts • Dairy • Gluten • Eggs • Shellfish
- **Goals**: Maintain • Lose • Gain; activity level (light/moderate/high)
- **Privacy note** (copy): “Photos are processed to identify foods (placeholder).”

### 5.2 Dashboard (Today)

- **Top Row Tiles**: Calories remaining, Macro ring (visual), Hydration, Steps (sync badge)
- **Quick Add**: “+ Photo”, “+ Search”, “+ Water 250ml”
- **Nudge** (copy): “Low on fiber—add a salad or fruit.”
- **Recent Meals**: card list with small thumbnail + kcal

### 5.3 Log Meal (Core)

- **Upload/Camera** area (icon + drag-drop placeholder)
- **Recognition Results** (visual table):

  - Item (e.g., _Poha_), Portion (dropdown look), Kcal, Macros
  - “Replace with healthier swap” chip (opens swaps panel)

- **Portion Helper**: “Palm/Thumb/Cup” visual cues (icons only)
- **Add Notes**: mood/satiety slider (faces), “post-workout” tag
- **Save** (visual button) → anchors back to Diary/Today

### 5.4 Food Details & Swaps

- **Food Header**: name, cuisine, common portion sizes
- **Nutrient Panel**: kcal, P/C/F grams, fiber, sugar, sodium (bars)
- **Alternatives** (“Swap Ideas”):

  - _Paneer Butter Masala_ → **Grilled Paneer + Tomato Curry** (−180 kcal, +fiber)
  - _White Rice_ → **Half Brown Rice + Half Salad**
  - _Fried Bhajji_ → **Air-fried Bhajji**

- **Why this swap?** `<details>` with short reasoning (calories, fiber, fat)

### 5.5 Diary

- **Meal Sections**: Breakfast • Lunch • Dinner • Snacks
- Each entry: thumbnail, title, kcal, macro mini-bars, swap chip
- **Daily footer**: totals, macro targets line, fiber score, water count

### 5.6 Insights (Week)

- **Tiles**: Avg calories, Protein/day, Fiber/day, Hydration/day
- **Trends**: 7-day calorie blocks (CSS heatmap cells), macro balance bars
- **Badges**: “Hydration Hero”, “Fiber Friend”, “Balanced Plate” (locked/unlocked)
- **Top Swaps Used** list

### 5.7 Integrations

- **Connect row** (visual toggles only):

  - Apple Health • Google Fit • Strava • MyFitnessPal (read-only placeholder)

- **What syncs** (copy): steps, workouts, weight; **not** medical data in V1

### 5.8 Settings

- Units (g/ml), Calorie target (static field), Macro split (pie sliders visual)
- Dietary prefs & exclusions editor
- Themes: Light/Dark/High-contrast
- **Data & Privacy**: export (CSV/JSON placeholder), clear diary (warning copy)

### 5.9 About

- Educational disclaimer; not a substitute for medical advice
- How recognition works (concept), limitations, and accuracy tips

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Tile** (kcal, macros, water, steps)
- **Macro Ring** (circular progress made with conic-gradients)
- **Heatmap Cell** (intensity classes)
- **Meal Card** with thumbnail and swap chip
- **Food Table** (recognition results)
- **Swap Chip** / **Nudge Banner**
- **Nutrient Bars** (kcal, P/C/F, fiber)
- **Portion Helper** icons (hand/cup/plate outlines)
- **Badge** (locked/unlocked)
- **Toggle** (integration visual), **Radio/Chip** filters
- **Print Header/Footer** for diary

---

## 7) Data Model (future-ready; no code)

**Meal**

- `id`, `datetime`, `type` (breakfast/lunch/dinner/snack)
- `items` (array of `FoodItem`), `notes`, `mood`, `satiety`

**FoodItem**

- `id`, `name`, `cuisine`, `portion` (g/ml/serving), `kcal`, `protein`, `carbs`, `fat`, `fiber`, `sugar`, `sodium`
- `source` (photo|search|barcode), `confidence` (if photo)

**PhotoRecognitionResult**

- `photoId`, `candidates` (array `{name, confidence, defaultPortion}`)

**SwapSuggestion**

- `foodItemId`, `altFoodId`, `benefit` (kcal↓, fiber↑, fat↓), `reason`

**Hydration**

- `date`, `mlTotal`

**Integration**

- `provider` (apple|google|strava|mfp), `status` (connected|notConnected), `lastSyncAt`

**User**

- `id`, `diet`, `allergies`, `goals`, `macroTargets`, `privacyPrefs`

**Insights**

- `dateRange`, `calorieAvg`, `macroAvg`, `fiberAvg`, `topSwaps`, `badges`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.tile--kcal`, `.macro-ring__fill`, `.meal-card__swap`, `.heatmap__cell--3`, `.nutrient-bar__value`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — layout helpers (flex/grid/gaps/visually-hidden)
  4. `components.css` — tiles, rings, tables, chips, badges, banners
  5. `layouts.css` — header/sidebar/content grids
  6. `themes.css` — light/dark/high-contrast
  7. `print.css` — diary/summary

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent: #22A06B (health)
- Secondary: #2563EB (actions)
- Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Heatmap: `--heat-0` … `--heat-4` (very light → strong)

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Typography**

- H1: 24–28 • H2: 20 • Body: 16 • Caption: 12–13
- Tabular numbers class for nutrient tables.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Shadows: soft for elevation; strong focus outlines for a11y

---

## 10) Accessibility & Privacy

- Landmarks: `<header> <nav> <main> <footer>`; one H1 per page.
- Labels for all form fields; large tap targets; visible focus rings.
- Do **not** rely on color alone—add icons/text for states (e.g., high sodium).
- **Privacy copy**: photos may contain sensitive data; offer local-only processing note in V1.
- Provide **mask/blur** placeholder option for faces/backgrounds (visual only).
- Alt text for images; respectful language in nudges (“try adding…” rather than “avoid”).

---

## 11) Print Styles

- **Daily Diary**: date header, meals table (kcal/macros), swaps used.
- **Weekly Summary**: totals + average macros + hydration + top 3 swaps.
- Hide navigation; black on white; page numbers in footer.

---

## 12) File & Folder Structure

```
root
 ├─ index.html            (Dashboard)
 ├─ onboarding.html
 ├─ log-meal.html
 ├─ food.html             (Food Details & Swaps)
 ├─ diary.html
 ├─ insights.html
 ├─ integrations.html
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
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Nudge (dashboard):** “Low on fiber today—add dal, sprouts, or a fruit.”
- **Swap explainer:** “Swapping to **grilled paneer** trims calories and adds protein without heavy cream.”
- **Portion helper:** “1 cup ≈ your clenched fist. 1 tbsp ≈ your thumb.”
- **Hydration tip:** “Aim for 6–8 glasses (1500–2000 ml) unless advised otherwise.”
- **Integration note:** “When connected, steps and workouts adjust your daily calorie guidance (placeholder).”
- **Privacy banner:** “Photos stay on your device in V1 (concept).”

---

## 14) Acceptance Criteria (V1)

- Onboarding collects diet prefs, allergies, and goals (visual).
- Dashboard shows tiles (kcal, macros ring, water, steps) and quick actions.
- Log Meal page displays photo area, recognition table, portion helpers, and notes.
- Food page shows nutrients + **3+ swap ideas** with reasons.
- Diary lists **4 meal sections** with totals and water count.
- Insights shows **weekly heatmap**, macro bars, and **2+ badges**.
- Integrations page lists **3+ providers** with visual toggles.
- Print styles output a clean daily and weekly report.

---

## 15) Future Enhancements

- Real photo recognition (on-device first), barcode scanning, and branded items.
- Macro/micro calculation, goal personalization, and adaptive nudges.
- True fitness sync (read workouts/steps; write nutrition where supported).
- Offline-first caching; CSV/JSON export; clinician share link.
- Community recipes; batch logging; family plates with portion split.
- Allergy cross-checks and sodium/sugar alerts.

---

## 16) Sample Static Data (populate UI)

**Recognized Items (example table)**

- Poha — 180g — 320 kcal — P 6g • C 55g • F 7g • Fiber 3g
- Masala Omelette — 120g — 220 kcal — P 16g • C 4g • F 15g

**Swap Ideas**

- Poha → **Veg Poha + Peanuts + Sprouts** (fiber↑, protein↑)
- Masala Omelette → **Omelette + extra whites + sautéed veg** (fat↓, protein↑)
- Soda → **Sparkling water + lemon** (sugar↓)

**Hydration**

- Today: 1750 ml (7 × 250 ml)

**Weekly Heatmap (calories)**

- Mon–Sun intensity cells with legend (very low → high)

**Badges**

- “Hydration Hero (3d)” • “Balanced Plate (5 swaps)” • “Fiber Friend (25g avg)”

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) so you can drop it straight into Cursor.
