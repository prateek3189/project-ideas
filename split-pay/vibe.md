# Split & Pay — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a **group expense tracker** where friends, roommates, or teams can log expenses, see **who owes whom**, and create **payment links** (all **visual placeholders**). V1 is **JavaScript-free**—no real payments, logins, OCR, or currency rates. Paste into **Cursor** and wire up logic later.

---

## 1) Vision & Goals

- Make splitting bills **simple and fair** for trips, households, and teams.
- Support multiple split types: **equal, shares, percentages, itemized, weights**.
- Provide a clear **Settle Up** plan and **payment link** placeholders (UPI/PayTM/PhonePe/PayPal).
- Keep UI **accessible, responsive, printable**, and privacy-conscious.

---

## 2) Constraints (V1)

- **No JavaScript**: all calculations, payments, imports, and exchange rates are **non-functional**.
- Use native HTML (`<details>`, forms, tables) and pure CSS only.
- Photos/receipts and scanning are **placeholders**.

---

## 3) Personas & Core User Stories

- **Trip Crew:** “We added lots of mixed-currency expenses—who owes what?”
- **Roommates:** “Split rent and utilities monthly with different shares.”
- **Team Leads:** “Track project expenses and settle with fewer transfers.”

**Stories (visual-only in V1)**

1. Create a **Group** and add **Members** (names, handles).
2. Add an **Expense** with split type (equal/shares/%/itemized/weights).
3. View **Balances** per member and **minimized transfers** (mock).
4. Generate **Settle Up** with **payment buttons** (UPI/PayPal placeholders).
5. Attach **receipt** (thumbnail placeholder); add **notes** and **tags**.
6. Print a **Trip Summary** with settlement instructions.

---

## 4) Information Architecture

- **Dashboard** — your groups, totals, unsettled balances
- **Group** — expenses list, balances, settle up
- **Add Expense** — payer, amount, currency, split type, participants
- **Settle Up** — minimized transfer plan + payment link placeholders
- **Members** — member handles, default shares, reminders (visual)
- **Insights** — by category, by member, timeline (CSS bars)
- **Receipts** — upload placeholders, link to expense
- **Settings** — currency, theme, rounding, privacy (visual)
- **About** — method, disclaimers

**Global Shell**

- Header: app name, group switcher, print link
- Sidebar: nav + theme toggle (visual only)
- Main: page content
- Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **Tiles**: Groups • Unsettled Amount • This Month Added • You Owe / Owed To You
- **Group Cards**: title, members count, unsettled total, last activity; CTA **Open**
- **Quick Actions**: New Group • Add Expense

### 5.2 Group (Core)

- **Header Row**: Group name, currency (visual), trip dates, invite link (placeholder)
- **Tabs**: Expenses • Balances • Settle Up • Insights
- **Balances Strip**: per-member chips (You owe / You’re owed)
- **Expenses List** (reverse chrono):

  - Merchant/Note • Paid by **X** • Split among **N**
  - Amount & currency, tags, receipt thumb
  - `<details>` shows split breakdown table per member

### 5.3 Add Expense

- **Form**

  - Payer (select member), Amount, Currency (visual), Date
  - Category (Food, Travel, Stay, Utilities, Office…)
  - Description / Merchant, Notes, Receipt (placeholder)
  - **Split Type** (radio):

    - Equal • Shares • Percentage • Itemized • Weights

- **Split Panel** (varies by type)

  - **Equal:** checkbox list of participants
  - **Shares:** per-person integer shares (e.g., 1-2-1)
  - **Percentage:** inputs sum to 100%
  - **Itemized:** mini table (item, qty, price, who)
  - **Weights:** decimals (e.g., 0.7, 0.3)

- **Save Expense** (visual) → anchors back to Group

### 5.4 Settle Up

- **Summary**: Total owed, transfers count (mock minimal-cash-flow)
- **Transfer Plan** (cards):

  - “**A pays B ₹1,250**” • “**C pays A ₹600**” …
  - Payment buttons (visual): **UPI**, **Paytm**, **PhonePe**, **PayPal**
  - Copy payment note (group + expense ref)

- **Alternative Plans** `<details>`: “Fewer transfers vs Balanced payers”
- **Fairness & Rounding** note: 2 decimals, last payer adjusts (copy-only)
- **Mark as Settled** (visual toggle) → moves to history

### 5.5 Members

- Member list with avatar initials, handle (UPI/PayPal id visual), default share %, reminders (visual), remove member (guard text only)

### 5.6 Insights

- **Tiles**: Top Spender, Most Owed, Biggest Category, Avg per Day
- **Charts** (CSS blocks): By Category bars, By Member bars, Daily adds (7-day)
- **Tags** list: Food, Fuel, Tickets, Stay…

### 5.7 Receipts

- Grid of thumbnails (placeholders) with amount, date, link to expense

### 5.8 Settings

- **Default Currency** (₹, \$, €), **Multi-currency** note (copy-only FX)
- **Rounding** (nearest 0.50/1.00 visual), **Theme** (light/dark/high-contrast)
- **Privacy**: local-only concept, export placeholders (CSV/JSON)
- **Payment Providers**: show toggles (visual) for UPI/PayPal/Bank transfer

### 5.9 About

- How splits work (concept), limitations, not a payments provider

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Group Card**, **Expense Row**, **Split Table**
- **Member Chip** (owe/owed variants), **Balance Badge**
- **Settle Card** with payment buttons (visual)
- **Receipt Thumb**, **Tag Chip**, **Category Pill**
- **Stat Tile**, **Bar Chart**, **Heat/Block Chart**
- **Alert/Nudge Banner** (e.g., “Unsettled > 30 days”)
- **Print Header/Footer** for summaries

---

## 7) Data Model (future-ready; no code)

**Group**

- `id`, `name`, `currency`, `multiCurrency` (bool), `createdAt`, `members[]`

**Member**

- `id`, `name`, `handle` (upi/paypal/bank note), `defaultWeight`, `isActive`

**Expense**

- `id`, `groupId`, `payerId`, `amount`, `currency`, `date`, `category`, `description`, `tags[]`, `receiptUrl`, `splitType` (equal|shares|percent|itemized|weights)

**SplitLine**

- `expenseId`, `memberId`, `share` (amount or % or weight), `finalAmount` (computed later)

**Balance**

- `groupId`, `memberId`, `netAmount` (positive = owed to member)

**TransferPlan**

- `groupId`, `planId`, `transfers[]` (`{fromId, toId, amount, currency, paymentHint}`), `note`

**PaymentLink** (placeholder)

- `provider` (upi|paytm|phonepe|paypal), `toHandle`, `amount`, `currency`, `note`

**Settings**

- `defaultCurrency`, `roundingMode`, `theme`, `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.group-card__meta`, `.expense-row__amount--debit`, `.split-table__cell`,
  `.balance-badge--owed`, `.settle-card__button--upi`, `.chart__bar--food`,
  `.member-chip--you`, `.nudge--warning`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — cards, rows, chips, tables, banners, charts
  5. `layouts.css` — header/sidebar/group grids
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — summaries & statements

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent: #2563EB
- Owe: #DC2626 • Owed: #16A34A • Info: #3B82F6 • Warning: #F59E0B

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB (AA)

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- **Tabular numerals** class for money columns.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Focus rings high-contrast; reduced-motion variant.

---

## 10) Accessibility & Fairness

- Landmarks: `<header> <nav> <main> <footer>`; single H1/page.
- Labels on all inputs; keyboard navigable; visible focus rings.
- Not color-only: pair text/icons with owe/owed indicators.
- **Rounding** note and last-payer adjustment explained (copy).
- Privacy copy: local-only concept; show masked handles (e.g., `name@ok****`).

---

## 11) Print Styles

- **Trip Summary**: totals by member, expenses table, settlement plan.
- **Monthly Statement**: per group, categories, owed/owing snapshot.
- Hide nav; black on white; page numbers & footer.

---

## 12) File & Folder Structure

```
root
 ├─ index.html            (Dashboard)
 ├─ group.html            (Expenses/Balances/Settle/Insights)
 ├─ add-expense.html
 ├─ members.html
 ├─ receipts.html
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

- **Nudge (Dashboard):** “You have **₹3,420** unsettled across 2 groups.”
- **Add Expense helper:** “Use **Shares** when some people consumed more (e.g., 1-2-1).”
- **Settle Up note:** “Plan minimizes transfers. Last payer’s amount adjusted for rounding.”
- **Payment hint:** “Use UPI handle (e.g., `alex@okicici`). Add the group name in the note.”
- **Privacy banner:** “In V1, data stays in your browser (concept). Exports are manual.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **4 tiles** and **group cards** with unsettled totals.
- Group page lists **≥12 expenses**, **balances**, and a **Settle Up** plan (visual).
- Add Expense supports **5 split types** with participant controls.
- Members page shows handles and default shares.
- Insights shows **by category/member** bars and **daily adds** blocks.
- Receipts page displays **thumbnails** linked to expenses (placeholders).
- Print stylesheet outputs **Trip Summary** and **Monthly Statement** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real math engine for splits, drift, rounding; **minimal cash flow** optimizer.
- **Multi-currency** with FX rates and per-expense currency.
- **OCR** for receipts; email/SMS parsing; bank/UPI imports where supported.
- **Payment deep links** (UPI intent, PayPal.me) and settlement confirmations.
- Notifications, reminders, and due dates.
- Offline-first PWA; CSV/JSON import/export; audit history.

---

## 16) Sample Static Data (populate UI)

**Group: Goa Trip (₹, 4 members)**

- Members: Aditi (`aditi@okhdfc`), Rahul (`rahul@okicici`), Neha (`neha@ybl`), You (`you@okaxis`)
- Expenses (examples):

  - Taxi Airport → Hotel — **₹1,200** — Paid by Rahul — **Equal (4)**
  - Lunch Day 1 — **₹1,860** — Paid by You — **Shares** (1/2/1/0)
  - Resort Booking — **₹9,800** — Paid by Aditi — **Weights** (0.3/0.3/0.2/0.2)
  - Water Sports — **₹3,600** — Paid by Neha — **Percentage** (25/25/25/25)

- Balances (mock outcome):

  - You **owe ₹1,050** • Rahul **owed ₹620** • Aditi **owed ₹180** • Neha **owe ₹ -** _(sample only)_

- Settle Up (mock):

  - **You → Rahul ₹650** • **You → Aditi ₹400** • **Neha → Rahul ₹ -** (none)

**Roommates: Flat 3B (Monthly)**

- Rent **₹36,000** — Paid by Aditi — **Shares** (1/1/2)
- Internet **₹899** — Paid by You — **Equal (3)**
- Electricity **₹2,340** — Paid by Rahul — **Weights** (0.25/0.25/0.5)

---

If you want, I can also convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) to drop straight into Cursor.
