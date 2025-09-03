# Language Learning Buddy — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an **AI-powered conversation partner** that supports **speaking practice** and **pronunciation feedback**. V1 is **JavaScript-free**—all mic/AI features are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Provide a safe, motivating space to **practice real conversations** in a target language.
- Encourage **speaking out loud** with **pronunciation feedback** (visual in V1).
- Structure learning with **topics/roles**, **phrase help**, and **gentle grammar tips**.
- Keep the UI **semantic, accessible, responsive, and printable**.

---

## 2) Constraints (V1)

- **No JavaScript**. Use native HTML (anchors, `<details>/<summary>`, form controls) for a realistic feel.
- **No external UI frameworks**; system fonts or single webfont.
- Mic input, TTS, feedback scores, and SRS are **non-functional placeholders**.

---

## 3) Personas & Core User Stories

- **Beginner (A1–A2):** Wants slow speech, transliteration, key phrases.
- **Intermediate (B1–B2):** Wants roleplay scenarios and targeted pronunciation notes.
- **Advanced (C1–C2):** Wants nuanced feedback, idioms, and formal/informal registers.

**Stories (visual-only in V1):**

1. Start a **chat session** on a topic (e.g., café order, travel check-in, interview).
2. Tap a **mic button** (placeholder) to “speak”, see a **waveform** and “listening” state.
3. Receive **AI reply** bubbles with **pronunciation tips** and **phrase suggestions**.
4. Open **Pronunciation Lab** to see **score bars**, **phoneme highlights (IPA)**, and **slow playback** icons (visual).
5. Track **progress** (streak, minutes, topics covered, CEFR target) and view **review deck** (words/phrases).
6. Print/export a **chat transcript** with notes.

---

## 4) Information Architecture

- **Chat** — primary conversation UI (buddy replies, hints, feedback)
- **Topics** — scenarios & roleplays (Café, Travel, Job, Small Talk, Emergencies)
- **Pronunciation Lab** — per-phrase/pronunciation analysis (visual)
- **Lessons** — short grammar/phrase micro-cards linked to chats
- **Review** — phrasebook + spaced-repetition (visual)
- **Progress** — streaks, time learned, CEFR path, weak phonemes
- **Settings** — language pair, speech speed, accent, theme, accessibility
- **About** — methodology & ethics (learning > answers)

**Global Shell**

- Header: app name, search (decorative), profile chip, print button
- Sidebar: navigation + language switch + theme toggle (visual only)
- Main: page content
- Footer: help/version

---

## 5) Screen Blueprints

### 5.1 Chat (Core)

- **Conversation Area**

  - **User bubble** + avatar (RTL/LTR aware)
  - **Buddy bubble** with: main reply, **slow/normal** speech icons (visual), **vocab chips**, and a **“Tip”** callout (e.g., intonation)

- **Composer Bar**

  - Mic button (visual), “Listening…” indicator, waveform bar (CSS animation)
  - Text input (for typed practice), send icon (visual)

- **Assist Strip**

  - **Phrase help** (native phrase + transliteration + translation)
  - **Grammar hint** (`<details>` reveals explanation & examples)
  - **Cultural note** (short)

- **Feedback Chip (inline)**

  - “Pronunciation: 78/100 (visual) • Try softer ‘r’ / tap ‘t’ ”

- **Transcript Tools**

  - Save/Print transcript (links)

### 5.2 Topics

- Grid/list of **scenario cards** with CEFR badge, estimated time, and tags.
- Card actions: **Start Chat**, **Preview Phrases**, **Role Cards** (You are: customer / clerk).

### 5.3 Pronunciation Lab

- **Selected Phrase** header (native + transliteration + translation)
- **Score Row** (visual bars):

  - Overall • Stress • Intonation • Phoneme accuracy

- **Phoneme Map (IPA)**:

  - Text line with **per-syllable highlights** (e.g., red for low accuracy)
  - Tooltip copy (visual): “/ɹ/ often softened; try retroflex”

- **Playback Controls** (icons only): Slow, Normal, Shadow (visual)
- **Mouth-shape tips** (static illustrations placeholder)
- **Common Mistakes** callouts per phrase

### 5.4 Lessons (Micro-cards)

- Small cards: **Grammar bite**, **Usage pattern**, **Register** (formal/informal)
- `<details>` to reveal **examples** and **minimal pairs**.

### 5.5 Review (Phrasebook / SRS)

- **Deck tabs**: New • Learning • Due • Mastered (visual counts)
- **Card layout**: front (native phrase) / back (meaning + hint)
- Chips: **Tag**, **CEFR**, **Topic**
- Progress bar for daily review target

### 5.6 Progress

- **Tiles**: Streak days, Minutes spoken (visual), Phrases learned, Topics covered
- **Weak Phonemes** list (e.g., /θ/, /ð/, /ɹ/) with sample words
- **CEFR Path**: A1 → A2 → B1… with current level badge
- **Weekly Heatmap** (CSS grid, intensity classes)

### 5.7 Settings

- **Language Pair**: Native → Target (visual radios)
- **Accent/Voice**: (US/UK/IN etc., visual)
- **Speech Speed**: Slow • Normal • Fast
- **Text Aids**: Transliteration on/off, Subtitles size
- **Accessibility**: High-contrast, Dyslexia-friendly font (visual)
- **Theme**: Light/Dark

### 5.8 About

- Learning philosophy, privacy note (no storing voice by default in V1), and roadmap.

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Chat Bubble** (user/buddy variants), **Typing/Listening** indicators
- **Mic Button** & **Waveform** (CSS animation)
- **Feedback Chip** (score badge + short hint)
- **Phrase Block** (native • transliteration • translation)
- **IPA Line** with **highlight classes** (e.g., `.ipa__seg--low`)
- **Score Bars**, **Heatmap Cells**, **Streak Flame**
- **Lesson Card**, **Grammar Tip**, **Cultural Note**
- **SRS Card** (front/back visual), **Deck Tabs**
- **CEFR Badge**, **Tag Chips**, **Role Card**
- **Alert/Toast** (info/warning for reminders)

---

## 7) Data Model (future-ready; no code)

**User**

- `id`, `nativeLang`, `targetLang`, `accentPref`, `speedPref`, `a11yPrefs`
- `streakDays`, `minutesSpoken`, `currentCEFR`

**Session**

- `id`, `topicId`, `startAt`, `endAt`
- `utterances` (array of `Utterance`)

**Utterance**

- `id`, `role` (user|buddy), `text`, `audioUrl` (future)
- `pronunciationAssessmentId` (optional)

**PronunciationAssessment**

- `id`, `phraseId`, `overallScore`, `stressScore`, `intonationScore`
- `segments` (array: `{ipa, grapheme, score, note}`)

**Phrase**

- `id`, `topicId`, `textNative`, `transliteration`, `translation`, `ipa`, `tags`

**Topic**

- `id`, `title`, `cefr`, `tags`, `roleplayCards` (array)

**SRSItem**

- `phraseId`, `status` (new|learning|due|mastered), `nextReview`

---

## 8) CSS Architecture & Naming

- **BEM**: `.chat-bubble--buddy`, `.ipa__seg--low`, `.score-bar__fill--75`
- Layers:

  1. `tokens.css` (colors, spacing, radius, typography)
  2. `base.css` (reset, typography, elements)
  3. `utilities.css` (flex/grid/visibility/spacing helpers)
  4. `components.css` (bubbles, chips, bars, cards, waveform, badges)
  5. `layouts.css` (header/sidebar/content grids)
  6. `themes.css` (light/dark/high-contrast)
  7. `print.css` (transcripts & lesson sheets)

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Muted: #64748B
- Accent (learning): #2563EB
- Success (good pronunciation): #16A34A
- Warning (needs work): #F59E0B
- Danger (mispronunciation): #DC2626
- Heatmap levels: `--heat-0` … `--heat-4`

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB
- Adjust semantic colors for AA contrast.

**Typography**

- H1: 24–28 • H2: 20 • Body: 16 • Caption: 12–13
- Support **RTL & CJK**: set font stacks and `dir` handling.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (bubbles/cards), 999 (chips)
- Soft shadows for elevation

---

## 10) Accessibility & Internationalization

- Landmarks: `<header> <nav> <main> <footer>`.
- **Language attributes**: set `lang` on blocks; support `dir="rtl"` for Arabic/Hebrew.
- **Readable transliteration**: use `<ruby>` where appropriate (fallback text included).
- **Form labels** tied to controls; visible focus rings.
- **Do not rely on color alone** for correctness—use text/icons.
- **ARIA live (conceptual)** for chat updates (not functional in V1).

---

## 11) Print Styles (Transcripts & Notes)

- Hide sidebar/buttons; print **topic, date, CEFR, transcript**.
- Show **phrase list** with space for notes and IPA hints.
- Black-on-white; enlarge body text; include footer with page numbers.

---

## 12) File & Folder Structure

```
root
 ├─ index.html            (Chat – default landing)
 ├─ topics.html           (Scenarios & roleplays)
 ├─ pronun-lab.html       (Pronunciation Lab)
 ├─ lessons.html          (Grammar & phrase micro-cards)
 ├─ review.html           (Phrasebook / SRS visual)
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
     ├─ illustrations/
     └─ audio-placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Chat Tip (buddy bubble):**
  “Try: _I’d like a cappuccino, please._ → Mind the **/tʃ/** sound in _cappuccino_.”
- **Pronunciation Feedback (chip):**
  “**Overall 78/100** — Great rhythm! Work on **/r/** in _red_ (retroflex).”
- **Grammar Note:**
  “Politeness: add _please_ and a rising intonation for requests.”
- **Cultural Note:**
  “In many cafés, greeting first (‘Hi there!’) softens the request.”
- **SRS Prompt:**
  “Come back in 10 minutes to review: _Where is the metro station?_”

---

## 14) Acceptance Criteria (V1)

- **Chat page** shows at least 6 alternating bubbles, assist strip, and visible listening state (CSS only).
- **Topics page** lists ≥8 scenario cards with CEFR badges.
- **Pronunciation Lab** displays **phrase**, **IPA line with highlights**, and **score bars**.
- **Lessons** page contains 6–12 micro-cards (grammar/phrase/culture).
- **Review** shows deck tabs and at least 12 phrases with tags.
- **Progress** shows streak, minutes, CEFR path, weak phonemes, and a weekly heatmap.
- **Print** produces a clean transcript/phrase sheet.

---

## 15) Future Enhancements

- Web Speech API (ASR) for mic input; TTS for buddy voice and slow mode.
- Real **pronunciation scoring** (phoneme-level) and **prosody** analysis.
- Adaptive dialog: difficulty & speed adjust to user performance.
- Spaced repetition scheduling; daily goals & reminders (PWA).
- Multi-accent voice models; downloadable offline packs.
- Teacher mode: assign topics, view speaking time & weak sounds.

---

## 16) Sample Static Data (populate UI)

**Topics (cards)**

- Café Order (A1) • Travel Check-in (A2) • Directions (A2) • Small Talk (B1)
- Job Interview (B2) • Presentation Pitch (C1) • Emergency Help (A2) • Restaurant (A1)

**Phrases (with IPA)**

- “Good morning!” — /ɡʊd ˈmɔːnɪŋ/
- “I’d like a cappuccino, please.” — /aɪd laɪk ə ˌkæpʊˈtʃiːnəʊ, pliːz/
- “Could you speak more slowly?” — /kʊd juː spiːk mɔː ˈsləʊli/

**Weak Phonemes Examples**

- **/θ/**: _think, thanks_
- **/ð/**: _this, other_
- **/r/** (retroflex/tapped): _red, para_

**Progress Tiles (example text)**

- Streak **5** days • Minutes spoken **42** • Phrases **38** • Topics **7**

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) so you can drop it straight into Cursor.
