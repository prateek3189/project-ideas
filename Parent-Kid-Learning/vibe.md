# Parent-Kid Learning App — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an app where parents and toddlers (like **Karnika**) enjoy **interactive stories**, **rhymes**, and **pronunciation practice** together. V1 is **JavaScript-free**—all audio/mic/AI bits are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Make screen time **co-learning time**: read stories, sing rhymes, practice words.
- Encourage **speech and listening** with friendly **pronunciation cues** (visual in V1).
- Keep the UI **big-tap, low-friction, bilingual-friendly**, and **printable**.
- Prepare a structure you can later enhance with audio recording, TTS, and progress tracking.

---

## 2) Constraints (V1)

- **No JavaScript**; use only semantic HTML and CSS.
- Microphone, TTS, auto-highlighting, and scoring are **placeholders** (icons/copy only).
- Optional static `<audio controls>` may appear with placeholder files (no custom JS).
- Bilingual copy examples may show **English ↔ Hindi/Marathi** pairs (static).

---

## 3) Personas & Core User Stories

- **Toddler (2–5 yrs):** Big pictures, short lines, simple words, tap-along rhymes.
- **Parent/Caregiver:** Needs safe controls, **Parent Mode**, time limits, printables.
- **Educator/Grandparent:** Wants easy story playlists and pronunciation prompts.

**Stories (visual-only in V1):**

1. Pick a **Story** and flip through large **picture pages** with one-line text.
2. Open **Rhymes** and see **karaoke-style** lyric lines (static highlight look).
3. Try **Pronunciation Practice**: word cards show **mouth-shape tips** and **syllable dots**.
4. View **Progress** tiles: “Stories read”, “Rhymes tried”, “Words practiced” (static).
5. Use **Parent Mode** to set session time and choose language packs (visual only).
6. **Print** coloring sheets, flashcards, and a mini reader.

---

## 4) Information Architecture

- **Home** — quick tiles: Continue Story • Rhymes • Pronounce • Printables
- **Stories** — library grid, age tags, languages
- **Story Reader** — full-bleed art, short line text, next/prev pager
- **Rhymes** — rhyme cards with beat bars (static), actions: Play / Lyrics / Motions
- **Pronunciation Lab (Kids)** — word sets, syllable bubbles, IPA hint (tiny), mouth tips
- **Progress** — “This week” tiles, sticker badges (visual), streak dots
- **Parent Mode** — session timer, content selection, languages, safety gates
- **Settings** — theme, text size, high-contrast, language, audio prefs (visual)
- **About** — pedagogy, privacy & safety

**Global Shell**

- Header: app name, language chip, profile avatar (family)
- Sidebar (optional on desktop): sections + theme toggle (visual)
- Main: page content
- Footer: “For families • v0.1 • Print”

---

## 5) Screen Blueprints

### 5.1 Home

- **Hero Tiles** (large):

  - Continue Story → “Juju the Bunny (Page 4/8)”
  - Rhymes → “Clap & Tap”
  - Pronounce → “Animals A-B-C”
  - Printables → “Coloring • Flashcards”

- **Parental Tip**: “Best used together—read first, then repeat.”

### 5.2 Stories (Library)

- Filters: Age (2+, 3+, 4+), Length (Short/Medium), Language (EN/HI/MR)
- Story Cards:

  - Cover art, title, 1-line synopsis, chips: **Bilingual**, **Phonics**, **Numbers**
  - CTA: **Read** / **Preview**

- Empty state copy for filters.

### 5.3 Story Reader (Core)

- **Page Layout**:

  - Large illustration
  - **One-line text** below with **keyword bold**
  - **Parent whisper tip** (tiny): “Ask: Where’s the **red ball**?”

- **Paging**: Prev / Next buttons (big tap targets)
- **Read-Along Row**:

  - “Play” icon (visual), “Slow” icon (visual)
  - **Word chips** for key vocabulary (EN ↔ HI/MR)

- **End Page**:

  - “We learned: Colors • Animals”
  - “Say it with me:” word list
  - “Print this story” link

### 5.4 Rhymes

- **Rhyme Card**:

  - Title, beat bars (static CSS animation), actions: **Play**, **Lyrics**, **Motions**
  - **Lyric panel**: big lines, child-friendly font; **current line** styled (static)

- **Motion Cues**: icon chips (clap, stomp, wave)

> _(Avoid full copyrighted lyrics; use public-domain samples or short placeholder lines in V1.)_

### 5.5 Pronunciation Lab (Kids)

- **Word Set Selector**: Animals • Fruits • Colors • Family
- **Word Card**:

  - Big picture + word: **“Apple / सेब / सफरचंद”**
  - **Syllable dots**: “Ap • ple”
  - **Mouth Tips** (tiny): “open /æ/ like a short ‘a’”
  - **Phoneme hint** (optional): `/æ/ /p/ /l/`
  - **Tap to say** (mic icon placeholder), **Repeat after me** (speaker icon placeholder)

- **Mini Game Row** (visual): “Find the word”, “Match picture”, “Say and Stick a Star”

### 5.6 Progress

- **Tiles**:

  - Stories Read **7** • Rhymes Tried **5** • Words Practiced **18**

- **Sticker Badges** (locked/unlocked visuals):

  - “Color Champ”, “Animal Buddy”, “ABC Explorer”

- **Streak Dots** (7-day)
- Parent note: “Progress is a feel-good placeholder in V1.”

### 5.7 Parent Mode (Gate)

- **Parental Gate** (visual): simple question or hold button for 3 seconds (copy only)
- **Controls**:

  - Session Time: 10/15/20 min (visual radios)
  - Languages: EN, HI, MR (multi-select look)
  - Content: Stories, Rhymes, Pronounce packs
  - Text Size: Normal / Large / Extra
  - High Contrast: On/Off

- **Quiet Mode**: reduce visuals for bedtime reading (visual)
- **Download**: “Printables Pack” (link placeholder)

### 5.8 Settings

- Theme: Light/Dark/High-contrast
- Fonts: Standard / Dyslexia-friendly (visual)
- Audio Prefs: Play once / Loop (visual)
- Data & Privacy note (copy)

### 5.9 About

- Learning approach: **Read → Repeat → Play**
- Screen-time guidance and privacy promise
- Roadmap: recording, TTS, custom playlists

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Hero Tile**, **Story Card**, **Rhyme Card**
- **Big Button** (48–56px min height)
- **Pager** (Prev/Next)
- **Word Chip** (bilingual)
- **Beat Bar** (CSS animation, no JS)
- **Syllable Dots** & **Phoneme Badge**
- **Mouth Tip** callout with tiny icon
- **Sticker Badge** (locked/unlocked)
- **Progress Tile**, **Streak Dot Row**
- **Parent Gate** panel
- **Print Button** (link to print stylesheet)

---

## 7) Data Model (future-ready; no code)

**Story**

- `id`, `title`, `lang` (EN/HI/MR), `ageBand`, `pages` (array of `{imageUrl, lineText, vocab[]}`)
- `tags` (colors, animals, numbers), `length` (short/med)

**Rhyme**

- `id`, `title`, `lang`, `isPublicDomain`, `motions` (array), `lyrics` (lines\[])

**Word**

- `id`, `imageUrl`, `en`, `hi`, `mr`, `syllables` (\["ap","ple"]), `ipa` ("/æpəl/"), `mouthTips`

**Session / Progress**

- `storiesRead`, `rhymesTried`, `wordsPracticed`, `streakDays`, `stickers` (ids)

**Settings**

- `languages` (array), `textSize`, `theme`, `contrast`, `sessionMinutes`

---

## 8) CSS Architecture & Naming

- **BEM**: `.story-card__cover`, `.rhyme-card__beat`, `.word-card__syllable-dot`
- Layers:

  1. `tokens.css` (colors, spacing, radii, typography)
  2. `base.css` (reset, base elements, accessibility)
  3. `utilities.css` (grid/flex/gap/visually-hidden)
  4. `components.css` (cards, chips, dots, badges, beat bars)
  5. `layouts.css` (header/sidebar/reader)
  6. `themes.css` (light/dark/high-contrast)
  7. `print.css` (storybook/flashcards)

---

## 9) Design System (Toddler-friendly)

**Colors (Light)**

- Background: #FFFDF7
- Surface: #FFFFFF
- Text: #1F2A44
- Accent: #FF7A59 (warm)
- Secondary: #3BB6F6 (calm)
- Success: #22C55E • Warning: #F59E0B
- High-contrast variants for accessibility

**Typography**

- Titles: 28–32
- Story line: 22–24 (generous line spacing)
- Body UI: 16–18
- Use a legible rounded sans; alternate dyslexia-friendly font (visual only)

**Spacing & Radius**

- Spacing scale: 6, 12, 16, 24, 32
- Radius: 16 (cards), 999 (chips)
- Touch targets: **min 44×44px**

**Imagery**

- Big illustrations, minimal clutter
- Consistent iconography (clap, wave, speak)

---

## 10) Accessibility, Safety & Parenting

- Landmarks: `<header> <nav> <main> <footer>`
- **Readable fonts**, generous line spacing
- **Focus visible**; keyboard navigable
- **Color + icon + text** (never color-only signals)
- **Parental Gate** (copy only) before settings
- **No ads or external links** in kid view (V1 copy)
- Offline-friendly printables; avoid heavy assets

---

## 11) Print Styles (must-have)

- **Storybook Mode**: 2 pages per sheet (image box + one-line text + vocab chips)
- **Flashcards**: 3×3 grid of picture+word (front/back layout)
- **Coloring Sheets**: outline art + word outline
- Remove nav, use dark text on white, large margins for cutting

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home)
 ├─ stories.html         (Stories Library)
 ├─ reader.html          (Story Reader)
 ├─ rhymes.html          (Rhymes)
 ├─ pronounce.html       (Pronunciation Lab - Kids)
 ├─ progress.html
 ├─ parent.html          (Parent Mode)
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
     ├─ illustrations/
     ├─ icons/
     └─ audio-placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Home tip:** “Read together first. Then let your child repeat key words.”
- **Reader whisper (parent):** “Ask: _What color is the ball?_”
- **Pronounce cue:** “Tap the dots: **Ap • ple** — short **/æ/** like in _cat_.”
- **Rhyme note:** “Clap on each bold word. Stomp on the last line!”
- **Parent gate:** “To change settings, hold for 3 seconds.” _(visual only)_
- **Printables:** “Cut along the dotted line for flashcards.”

---

## 14) Acceptance Criteria (V1)

- Home shows 4 hero tiles; all pages navigate via anchors (no JS).
- Stories library lists ≥9 cards with mixed tags and languages.
- Reader renders ≥8 pages with large art and one-line text + word chips.
- Rhymes page shows ≥6 rhyme cards with lyric panels and motion cues.
- Pronunciation page shows ≥12 word cards with syllable dots and mouth tips.
- Progress page shows tiles + sticker badges + streak dots (static).
- Parent Mode exposes session/text/language/contrast controls (visual only).
- Print stylesheet outputs storybook, flashcards, and coloring sheets cleanly.

---

## 15) Future Enhancements

- Web Speech API: record child speech; **phoneme-level** feedback & friendly scores.
- TTS narration with **slow mode** and **word-by-word highlighting**.
- Custom playlists; bedtime “quiet mode” with auto-dim.
- Cloud sync for progress & stickers across devices.
- Local language packs (EN-HI-MR and more) with parent-added words.
- Teacher/therapist profiles for articulation goals.

---

## 16) Sample Static Data (populate UI)

**Stories**

- _The Red Ball_ (EN/HI) — Colors, Objects
- _Mimi’s Garden_ (EN/MR) — Fruits, Counting
- _Animal Parade_ (EN/HI) — Animals, Sounds

**Rhymes (titles only)**

- “Clap Clap Little Hands” (PD-style placeholder)
- “Hop Hop Bunny Hop”
- “Rain Rain Sprinkle Game”

**Pronounce Words**

- **Animals**: cat/बिल्ली/मांजर • dog/कुत्ता/कुत्रा • cow/गाय/गाय
- **Fruits**: apple/सेब/सफरचंद • mango/आम/आंबा • banana/केला/केळी
- **Colors**: red/लाल/लाल • blue/नीला/निळा • green/हरा/हिरवा

**Stickers (visual)**

- “Color Champ” • “Fruit Finder” • “Song Star”

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) for your Cursor workspace.
