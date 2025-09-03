# Skill-Exchange Platform — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** where people **trade skills** (e.g., guitar lessons ↔ coding help) **without money**. V1 is **JavaScript-free**—all matching, scheduling, messaging, verification, and credits are **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Enable **fair, cashless exchanges** of time and skills.
- Make it easy to **offer** and **request** skills, then craft a **trade proposal** with clear terms.
- Encourage **trust & safety** with transparent profiles, references, and community rules.
- Stay **accessible, responsive, and printable**; ready to add logic later.

---

## 2) Constraints (V1)

- **No JavaScript**. No real messaging, scheduling, calendars, or credit accounting.
- Use semantic HTML (`<form>`, `<details>`, tables) and **pure CSS** for badges, meters, and states.
- “Smart match,” “conflict resolution,” and “credit balance” are **UI placeholders** only.

---

## 3) Personas & Core User Stories

- **Learner:** “I want guitar basics in exchange for English practice.”
- **Mentor/Pro:** “I’ll review portfolios in return for yoga sessions.”
- **Parent/Student:** “Homework help for baking lessons.”
- **Community Organizer:** “Form circles/classes that rotate skills monthly.”

**Stories (visual-only in V1)**

1. Create a **Profile** with offered skills, needs, availability, and location radius.
2. Post an **Offer** (what you can teach/do) and a **Request** (what you want).
3. Browse **Matches** and send a **Trade Proposal** with time, place, and exchange ratio.
4. Use **Deal Canvas** to agree on terms (hours, cancellation, materials).
5. Track **Sessions** and leave **Feedback** (kudos + reference).
6. Earn/Spend **Time Credits** (optional timebank concept, visual only).
7. Print a **Trade Agreement** for in-person sessions.

---

## 4) Information Architecture

- **Home / Explore** — search & filter skills; featured exchanges
- **Offers** — list what people can give
- **Requests** — list what people want
- **Matches** — suggested pairings (visual scoring)
- **Proposals** — craft & review trade terms
- **Sessions** — upcoming/past (placeholders)
- **Messages** — mock threads (visual)
- **Profile & Trust** — skills, availability, references, badges
- **Circles** — groups/classes and rotating skill swaps
- **Settings** — notifications, visibility, radius, themes, safety (visual)
- **About** — principles, safety guidelines, dispute policy (copy)

**Global Shell**
Header: logo/name, search (decorative), location radius chip, profile
Sidebar: nav + theme toggle (visual)
Main: page content • Footer: help/version/ethos

---

## 5) Screen Blueprints

### 5.1 Home / Explore

- **Search Bar** (visual) with placeholder suggestions (“guitar”, “frontend”, “yoga”).
- **Filter Chips**: Category (Music, Tech, Wellness, Languages, Crafts) • Mode (In-person/Online) • Time (Weekdays/Weekends/Evenings) • Radius.
- **Cards** (mixed offers/requests) show: title, skill level, location radius, **“Wants ↔ Gives”** line, badges (Verified, Reliable).

### 5.2 Offers

- Grid/list of **Offer Cards**:

  - Title (e.g., “Beginner Guitar 1:1”), Level (Beginner/Intermediate), Mode, Time slots, **Exchange Rate** chip (e.g., “1 hr ↔ 1 hr”).
  - `<details>`: curriculum bullets, needed materials.
  - “Propose Trade” button (visual).

- Filters: Category, Mode, Level, Distance, Availability.

### 5.3 Requests

- Similar layout to Offers; “I need…” phrasing with preferred schedule.
- “Open to Learn With” (solo/pair/small group) badge.

### 5.4 Matches (Suggested)

- **Match Rows** with a **compatibility meter** (CSS bar): skill overlap, schedule fit, location fit (labels only).
- Actions: **View Offer/Request**, **Draft Proposal** (visual).

### 5.5 Proposal (Deal Canvas) — Core

- **Participants**: you + partner chips with trust badges.
- **Trade Terms** (side-by-side table):

  - **You provide** / **They provide**
  - Duration per session, number of sessions, location (online/venue), materials.
  - **Exchange Ratio**: hours↔hours (or 1 hr ↔ 2 code reviews).

- **Schedule**: select time windows (visual chips), timezone note.
- **Expectations** `<details>`: goals, prep work, boundaries.
- **Cancellation** `<details>`: notice period, reschedule allowance.
- **Agreement Banner**: “No money. Community guidelines apply.”
- **Propose / Accept / Revise** buttons (visual).
- **Print Trade Agreement** link.

### 5.6 Sessions

- **Upcoming** and **Past** tabs (visual).
- Rows: date/time, skill, location (map pin placeholder/online), status (Scheduled/Completed/Cancelled), “Mark Completed” (visual toggle).
- **Attendance Note** (copy): “Honor system in V1.”

### 5.7 Messages (Mock)

- Thread list and bubble view; attachment pill (materials link placeholder).

### 5.8 Profile & Trust

- Header: name, location radius, languages, availability chips.
- Tabs:

  - **Skills Offered** (cards), **Skills Wanted** (cards)
  - **References** (short quotes), **Badges** (Reliable, Verified ID, Community Helper)
  - **Time Credits** (visual balance) & simple ledger (—).

- **Safety & Identity** (visual): phone/email verified placeholders.

### 5.9 Circles (Groups/Classes)

- **Circle Cards**: name, cadence (weekly/monthly), member count, focus (e.g., “Code & Coffee”, “Music Jam”).
- **Circle Page**: about, upcoming sessions (visual list), join/leave (visual), resource links.

### 5.10 Settings

- Location radius, visibility (Public/Neighbors/Private link), notification toggles (visual).
- Themes: Light/Dark/High-contrast; Reduced Motion.
- Safety preferences: prefer public venues, visible references only.

### 5.11 About

- Principles: **fairness, safety, inclusivity, no-money**.
- Dispute guidance (copy-only).
- Content rules (no prohibited services).

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Offer/Request Card** with “Gives ↔ Wants” line
- **Filter Chips**, **Radius Chip**, **Availability Chip**
- **Compatibility Meter** (bars), **Badge** (Verified/Reliable/Helper)
- **Proposal Table** (side-by-side), **Agreement Banner**
- **Schedule Chips**, **Location Box** (map placeholder)
- **Session Row**, **Status Pill**
- **Message Bubble**, **Attachment Pill**
- **Reference Quote**, **Trust Panel**
- **Circle Card**, **Member Chip**
- **Print Header/Footer** for Trade Agreement

---

## 7) Data Model (future-ready; no code)

**User**

- `id`, `name`, `bio`, `city`, `radiusKm`, `langs[]`, `availability[]`, `badges[]`, `verified` (bool), `refs[]`, `visibility`

**Skill**

- `id`, `category`, `title`, `level` (beginner|intermediate|advanced), `mode` (inPerson|online), `materials[]`

**Offer**

- `id`, `userId`, `skillId`, `summary`, `timeWindows[]`, `exchangeRate` (e.g., `{"type":"hours","offer":1,"want":1}`), `notes`

**Request**

- `id`, `userId`, `skillId`, `summary`, `timeWindows[]`, `preferredExchange` (same schema), `notes`

**MatchSuggestion**

- `offerId`, `requestId`, `score` (0–100), `factors` (`{schedule, distance, levelFit}`)

**Proposal**

- `id`, `fromUser`, `toUser`,
  `give` (`{skillId, hoursPerSession, sessions, materials}`),
  `receive` (`{skillId, hoursPerSession, sessions, materials}`),
  `ratio` (`{x:1,y:1}` or custom),
  `location` (`{mode, venueName, address}`),
  `timeWindows[]`, `expectations`, `cancellation`, `status` (draft|sent|accepted|revised|cancelled)

**Session**

- `id`, `proposalId`, `datetime`, `durationHr`, `status` (scheduled|completed|cancelled), `notes`

**Reference**

- `id`, `fromUser`, `toUser`, `text`, `createdAt`, `tags[]` (reliable, punctual, clear)

**TimeCredit (optional)**

- `userId`, `balanceHours`, `ledger[]` (`{change, reason, sessionId}`)

**Circle**

- `id`, `name`, `about`, `cadence`, `memberIds[]`, `posts[]`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.card--offer`, `.card--request`, `.chip--availability`, `.meter--compat`,
  `.proposal__table`, `.agreement--banner`, `.schedule__chip--evening`,
  `.session__status--completed`, `.badge--verified`, `.quote--reference`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements, forms
  3. `utilities.css` — flex/grid/gap/visually-hidden
  4. `components.css` — cards, chips, meters, tables, banners, bubbles
  5. `layouts.css` — shell, lists, two-column detail pages
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — trade agreement & profile one-pager

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent (action): #2563EB
- Trust: #16A34A • Info: #3B82F6 • Warning: #F59E0B • Danger: #DC2626

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Use **tabular numerals** for hours/ratios where shown.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Shadows: soft; focus rings high-contrast.

**Icons**

- Line icons for book, guitar, code, video, map pin, clock, handshake, shield.

---

## 10) Accessibility & Safety

- Landmarks: `<header> <nav> <main> <footer>`; one H1 per page.
- Labels tied to all form controls; keyboard navigable; visible focus.
- Do not rely on color alone—pair meters/badges with text.
- **No money** policy is explicit; list prohibited categories (copy).
- Safety tips: meet in public places, share expectations, respect boundaries.

---

## 11) Print Styles

- **Trade Agreement**: participants, skills exchanged, sessions (# & length), location, expectations, cancellation, signatures line.
- **Profile One-Pager**: skills offered/wanted, availability, references.
- Hide nav; black on white; page numbers; footer “Skill-Exchange v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Explore)
 ├─ offers.html
 ├─ requests.html
 ├─ matches.html
 ├─ proposal.html        (Deal Canvas)
 ├─ sessions.html
 ├─ messages.html
 ├─ profile.html
 ├─ circles.html
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

- **Explore nudge:** “Trade time, not money. Find someone nearby to swap skills.”
- **Offer helper:** “Set clear expectations and bring required materials.”
- **Request helper:** “Share your availability and learning goal (e.g., ‘Play 3 songs in 4 weeks’).”
- **Proposal banner:** “Cashless exchange. Be kind, be clear, be safe.”
- **Cancellation note:** “24-hour notice recommended; reschedule up to 2 times.”
- **Reference prompt:** “Leave a short note after each session—reliability builds trust.”

---

## 14) Acceptance Criteria (V1)

- Home shows **filterable Explore feed** with ≥12 mixed offer/request cards.
- Offers & Requests pages display filters, cards, and `<details>` expansions.
- Matches page shows **compatibility meters** and links to Proposal.
- Proposal page (Deal Canvas) displays **side-by-side terms**, ratio, schedule, location, expectations, and cancellation blocks, plus a **print link**.
- Sessions lists **upcoming/past** with status pills.
- Profile shows skills offered/wanted, availability, references, and badges (visual).
- Messages renders thread list + mock conversation.
- Print stylesheet outputs **Trade Agreement** and **Profile One-Pager** cleanly.
- Baseline a11y (labels, contrast, focus) passes.

---

## 15) Future Enhancements

- Real **matching engine** (schedule/location/level scoring) and “multi-party swaps”.
- Calendar invites; ICS export; timezone handling; reminders.
- In-app **chat** with attachment sharing; content moderation.
- **Timebank** accounting (earn hours from one trade, spend on another).
- Reputation system with categories (punctuality, clarity) and dispute workflows.
- Map search with geofencing; neighborhood verification.
- Community **circles**: rotating workshops; attendance tracking.
- PWA & offline mode; CSV export/import of sessions.

---

## 16) Sample Static Data (populate UI)

**Offers**

- “Beginner Guitar 1:1” — Level: Beginner — Mode: In-person/Online — **1 hr ↔ 1 hr** — Evenings
- “Frontend Code Review” — Level: Intermediate — Online — **1 review ↔ 1 yoga session**
- “Spoken Hindi Practice” — Level: All — Online — **45 min ↔ 45 min**

**Requests**

- “Need Python basics for data” — Weekends — **1 hr ↔ 1 hr**
- “Looking for pottery wheel intro” — Saturdays — **2 hr ↔ 2 hr**
- “Public speaking coaching” — Weeknights — **1 hr ↔ 1 hr**

**Match Suggestions**

- Guitar ↔ English Practice — **Compatibility 82/100** (schedule fit, radius 3 km)
- Code Review ↔ Yoga — **76/100** (time fit, online)

**Proposal Example (Deal Canvas)**

- You give: **Guitar Basics**, 1 hr × 4 sessions, bring own guitar
- You get: **Python 101**, 1 hr × 4 sessions, install Anaconda beforehand
- Ratio: **1:1** • Mode: Online Tue 7–8 PM • Cancellation: 24h notice

**References**

- “On time, patient teacher.” — Arjun
- “Clear examples, friendly & structured.” — Neha

---

If you’d like, I can also turn this into **ready-to-paste page skeletons** (still no JS) or a **README.md** for your Cursor workspace.
