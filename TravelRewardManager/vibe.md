# Travel Reward Manager — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a wallet that tracks **loyalty points** across airlines, hotels, and banks; helps plan **redemptions** for flights/hotels/experiences; and visualizes **transfers, expirations, and value**. V1 is **JavaScript-free**—all award search, transfers, and valuations are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Centralize all loyalty programs in one **Points Wallet**.
- Make it easy to **plan redemptions**: target trip, required points, transfer paths, estimated value.
- Prevent **point loss** with expiry alerts and activity nudges.
- Keep UI **semantic, accessible, responsive, and printable**.

---

## 2) Constraints (V1)

- **No JavaScript**: award availability, live pricing, login, and transfers are **non-functional** mockups.
- Use native HTML patterns (`<details>`, forms, tables) and pure CSS.
- No external UI frameworks; system fonts or a single webfont.

---

## 3) Personas & Core User Stories

- **Points Collector:** “Track balances and avoid expirations.”
- **Optimizer:** “What’s the **best value** way to book my trip?”
- **Planner (Family):** “Pool points and plan a summer trip.”
- **Business Traveler:** “See transfer partners and elite progress at a glance.”

**Stories (visual-only in V1):**

1. Add programs (airline/hotel/bank) and see a **unified balance** with **expiry bars**.
2. Set a **Trip Goal** (e.g., BOM → SIN roundtrip) and view **options** (direct redemption or **transfer**).
3. Browse **Award Finder** results (flights/hotels/experiences) with taxes/fees and **cpp** (cents-per-point) estimate (static).
4. Use **Transfer Hub** to see partner mappings and mock transfer times.
5. View **Insights**: weekly points delta, top earners, redemptions, and **effective value**.
6. Print a **Redemption Plan** for a trip.

---

## 4) Information Architecture

- **Dashboard** — totals, upcoming expirations, quick actions
- **Wallet** — programs & accounts, balances, transactions (static)
- **Trip Goals** — plan redemptions; gap to goal; suggested paths
- **Award Finder** — flights • hotels • experiences (visual search/results)
- **Transfer Hub** — partner maps (Amex/Chase/Citi/CapOne → airlines/hotels)
- **Insights** — value, earn vs burn, cpp, badges
- **Alerts & Deals** — expirations, transfer bonuses, promo fares (copy-only)
- **Settings** — currency, region, theme, privacy (visual)
- **About** — methodology & disclaimers

**Global Shell**

- Header: app name, currency switch, print link
- Sidebar: nav + theme toggle (visual only)
- Main: page content
- Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **Tiles**: Total Points • Est. Value (₹/\$/€) • Points expiring next 90 days • Trips Planned.
- **Upcoming Expirations** (list with program, amount, due date, **“Keep Alive”** ideas via `<details>`).
- **Quick Actions**: Add Program • New Trip Goal • Award Finder.

### 5.2 Wallet (Programs & Accounts)

- **Program Cards** (Airlines/Hotels/Banks tabs):

  - Logo, balance, **expiry bar**, last activity, status level, family pooling (visual).
  - Buttons: **View Transactions** (static table), **Program Rules** (`<details>` with high-level notes).

- **Banks & Currencies**: Amex MR, Chase UR, Citi ThankYou, Capital One; show **transfer partners** chips.
- **Sample programs** (mock): KrisFlyer, Avios, MileagePlus, Flying Blue, Privilege Club, Bonvoy, World of Hyatt, Hilton Honors, IHG One.

### 5.3 Trip Goals (Planner)

- **Goal Card**:

  - Route/dates (e.g., BOM → SIN, 15–19 Nov) or **Hotel** (city/dates).
  - Cabin/room preferences, passengers (adults/children), flexibility (±3 days).

- **Path Suggestions** (stacked cards):

  - **Direct Redeem in Program A** — 38k miles + ₹5,200 fees (cpp: 1.6)
  - **Transfer from Bank → Program B** — 26k points (with **20% bonus** mock), fees ₹4,100 (cpp: 2.1)
  - **Cash + Points** (hotel) — 12k pts + ₹7,000 cash (cpp: 1.3)

- **Gap to Goal** bar + **How to Earn Fast** tips (credit, shopping, dining… copy-only).
- **Print Redemption Plan** link.

### 5.4 Award Finder

- **Search Form** (visual):

  - **Flights**: From, To, Dates/Flex, Cabin, Stops, Alliances (Star/oneworld/SkyTeam chips)
  - **Hotels**: City, Dates, Brand, Points Range, Free breakfast/Pool/Wi-Fi
  - **Experiences**: City, Category (Tours, Lounge, Events)

- **Results Cards**:

  - For flights: airline/route, cabin, miles + taxes, **availability** (mock), **cpp est.** tag, transfer paths.
  - For hotels: brand/property, night cost (pts), taxes/resort fee copy, perks (mock).
  - For experiences: title, points, time, vendor chip.

- **Filters**: Lowest points • Highest cpp • Fewer fees • Nonstop.

### 5.5 Transfer Hub

- **Partner Map** grid:

  - Bank program → airline/hotel logos with **ratio chips** (e.g., 1:1, 2:1.5; static).
  - **Transfer Bonus** banners (visual): “Amex → Avios **+30%** until Nov 30”.

- **Transfer Time** notes (visual tags): Instant • Few hours • 1–2 days.
- **Warnings** (copy): transfers are **one-way**; verify availability first.

### 5.6 Insights

- **Tiles**: Earned this month, Redeemed this month, Net change, Avg cpp (mock).
- **Charts** (CSS bars/blocks): Earn vs Burn by program; cpp distribution; points by category (flights/hotels/experiences).
- **Badges** (visual): “Optimizer (cpp>1.8)”, “No-Expiry Quarter”, “Family Trip Planned”.

### 5.7 Alerts & Deals

- **Expiring Soon** list with “Keep Alive” `<details>`: e.g., “Small earn via partner dining.”
- **Transfer Bonuses** mock feed.
- **Promo Awards** mock feed (copy-only).

### 5.8 Settings

- **Default Currency** (INR/USD/EUR), **Region** (Asia/Global), **Units** (km/mi) — visual.
- **Theme**: Light/Dark/High-contrast; **Reduced Motion**.
- **Privacy**: local-only note (concept), export placeholders (CSV/JSON).

### 5.9 About

- High level: valuation methodology (cpp estimate), data limitations, not financial advice.

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Program Card** with balance, expiry bar, status chip
- **Trip Goal Card** with gap bar & suggestion list
- **Award Result Card** (flight/hotel/experience variants)
- **Transfer Partner Tile** with ratio/bonus
- **Valuation Chip** (cpp estimate)
- **Expiry Bar** & **Activity Tag**
- **Alert/Deal Banner**
- **Stat Tile**, **Trend Bars**, **Badge**
- **Print Header/Footer** for redemption plan

---

## 7) Data Model (future-ready; no code)

**Program**

- `id`, `type` (airline|hotel|bank), `name`, `statusLevel`, `rulesSummary`, `familyPooling`

**Account**

- `programId`, `memberId`, `balance`, `lastActivityAt`, `expiryPolicy`, `upcomingExpirations[]`

**Transaction**

- `accountId`, `date`, `type` (earn|redeem|transfer), `amount`, `note`

**TripGoal**

- `id`, `kind` (flight|hotel|experience), `params` (route/dates/cabin|city/dates/brand), `people`, `budgetCash`, `budgetPoints`

**AwardOption**

- `tripGoalId`, `programId`, `points`, `taxes`, `fees`, `cppEstimate`, `transferPath[]`, `notes`

**TransferMapping**

- `fromBank`, `toProgram`, `ratioFrom`, `ratioTo`, `bonusPct`, `typicalTime`

**Insight**

- `dateRange`, `earned`, `redeemed`, `net`, `avgCpp`, `byProgram[]`

**Alert**

- `type` (expiry|bonus|promo), `programId`, `message`, `validUntil`

**User**

- `currency`, `region`, `theme`, `a11yPrefs`, `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.program-card__balance`, `.expiry-bar__fill--soon`, `.award-card--flight`, `.valuation-chip--good`, `.transfer-tile__ratio`, `.goal-card__gap`, `.trend__bar--airlines`
- Layers:

  1. `tokens.css` (colors, spacing, radii, type)
  2. `base.css` (reset, base elements)
  3. `utilities.css` (grid/flex/gap/visually-hidden)
  4. `components.css` (cards, chips, bars, banners, tables)
  5. `layouts.css` (header/sidebar/grids)
  6. `themes.css` (light/dark/high-contrast/reduced-motion)
  7. `print.css` (redemption plan & statement)

---

## 9) Design System

**Colors (Light)**

- Background: #F7FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent: #2563EB
- Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Value scale for cpp: neutral → good (green) classes

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB (AA compliant)

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Use **tabular numerals** class for balances and cpp.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Subtle shadows; strong focus outlines for a11y.

---

## 10) Accessibility & Guidance

- Landmarks: `<header> <nav> <main> <footer>`; one H1/page.
- Labels for forms; keyboard navigable; visible focus.
- Do **not** rely on color alone—pair icons/text with valuation tiers.
- Clear disclaimers: award pricing varies; transfers are one-way; verify before transfer.

---

## 11) Print Styles

- **Redemption Plan**: trip goal, options table (points/taxes/cpp), transfer steps, notes.
- **Monthly Statement**: program balances, transactions, expirations, insights summary.
- Black on white; hide nav; page numbers & footer.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Dashboard)
 ├─ wallet.html          (Programs & Accounts)
 ├─ goals.html           (Trip Goals)
 ├─ awards.html          (Award Finder)
 ├─ transfers.html       (Transfer Hub)
 ├─ insights.html
 ├─ alerts.html          (Alerts & Deals)
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
     ├─ logos/
     ├─ icons/
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Expiry Nudge:** “2,500 Avios expire in 28 days. Any activity resets the clock—try a small partner earn.”
- **Value Tip:** “Compare cash fare to points + taxes to estimate **cpp**. Higher isn’t always better if you need flexibility.”
- **Transfer Warning:** “Transfers are **one-way**; confirm award space first.”
- **Goal Helper:** “Short by 4k points? Consider **20% transfer bonus** (if available) or split Cash+Points.”
- **Hotel Note:** “Watch for resort fees; some awards waive them.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **4 tiles**, an **expirations list**, and **quick actions**.
- Wallet lists **≥10 programs** across airline/hotel/bank with expiry bars and status chips.
- Trip Goals page displays at least **2–3 path suggestions** with cpp and transfer hints.
- Award Finder shows **search UI** and **≥6 results** across flights/hotels/experiences.
- Transfer Hub renders **partner map** with ratios and **bonus banners**.
- Insights has **tiles**, **earn vs burn chart**, and **badges** (visual).
- Alerts page lists expirations + bonus promos (visual).
- Print styles output a **Redemption Plan** and **Monthly Statement** cleanly.
- Meets basic accessibility (headings, labels, contrast, focus).

---

## 15) Future Enhancements

- Real logins & balance sync (email parses/APIs where available).
- Live award search & **calendar view**; mixed-cabin logic; surcharges estimation.
- Automatic **cpp** calculation with cash price pulls; multi-currency support.
- Transfer bonus tracker with notifications; **award hold** hints.
- Family pooling workflows; multi-passenger inventory checks.
- Integrations: Google/Apple Wallet passes; trip exporting; calendar holds.
- Mobile PWA; offline read of wallet & plans.

---

## 16) Sample Static Data (populate UI)

**Balances (mock)**

- **Amex MR**: 62,500 (no expiry)
- **Chase UR**: 48,000
- **KrisFlyer**: 18,500 (2,000 expire in 60d)
- **Avios (BA/Qatar)**: 24,300 (activity in 2025-06)
- **MileagePlus**: 12,000 (no expiry)
- **Marriott Bonvoy**: 36,000 • **Hyatt**: 11,500 • **Hilton**: 28,000

**Trip Goal — BOM → SIN (Nov 15–19, 1 pax, Economy)**

- Option A: **KrisFlyer** 26k + ₹4,100 taxes (cpp 1.9)
- Option B: **Transfer UR → Avios** 20k + ₹5,200 (cpp 2.1, **30% bonus** mock)
- Option C: **Cash + Points (Hotel)** 12k pts + ₹7,000/night (cpp 1.3)

**Award Finder (flights, sample cards)**

- SQ 423 BOM→SIN • 26k miles + ₹4,100 • Nonstop • **cpp 1.9**
- QR DEL→DOH→LHR • 62.5k Avios + ₹18k • Business • **cpp 2.4**
- AI BOM→DEL • 7.5k miles + ₹900 • Economy • **cpp 1.5**

**Transfer Hub (examples)**

- **Amex → Avios** 1:1 (**+30% bonus** mock) • Time: Instant
- **Chase → Hyatt** 1:1 • Time: Instant
- **Citi → KrisFlyer** 1:1 • Time: 12–24h

**Badges (visual)**

- “No Expiry Missed (90d)” • “Optimizer cpp>2.0” • “First Transfer Done”

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) so you can drop it directly into Cursor.
