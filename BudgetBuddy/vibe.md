# Budget Buddy — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a personal finance app that **tracks expenses automatically** via **SMS parsing** or **UPI** activity (visual only). V1 is **JavaScript-free**—all parsing, imports, and sync are **placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Make expense tracking **hands-off** with SMS/UPI import (mock in V1).
- Show **clear cashflow**, **budgets**, and **category insights** without shaming.
- Keep UI **accessible, responsive, printable, and privacy-aware**.

---

## 2) Constraints (V1)

- **No JavaScript**: no real SMS reading, UPI sync, OCR, or bank logins.
- Use native HTML patterns (`<details>`, forms, tables) and pure CSS.
- “Auto-categorization”, “duplicate detection”, and “recurring hints” are **visual labels**.

---

## 3) Personas & Core User Stories

- **Busy Professional:** “Auto-log everything and show me what changed this week.”
- **Student / First-job:** “Tiny budgets, alerts before I overspend.”
- **Household Manager:** “Split transactions and track bill cycles.”

**Stories (visual-only in V1)**

1. **Onboard** with currency (₹ default), accounts, categories.
2. **Import** via **SMS** or **UPI** (mock files/text); see parsed transactions.
3. Review **Transactions**: merchant, category, notes; edit visually.
4. Track **Budgets** per category with progress bars.
5. View **Insights**: spend by category/merchant, month trend, recurring bills.
6. **Print** a monthly statement for records.

---

## 4) Information Architecture

- **Dashboard** — balances, this month spend, budgets, alerts
- **Transactions** — table/list view with filters & tags
- **Budgets** — per-category limits & progress
- **Insights** — charts (CSS blocks): categories, merchants, cashflow
- **Import** — SMS/UPI mock import & review
- **Accounts** — cards/UPl handles/cash; status & statements
- **Receipts** — upload placeholders (static)
- **Settings** — currency, categories, rules, privacy (visual)
- **About** — methodology, privacy & disclaimers

**Global Shell**

- Header: app name, month picker, print link
- Sidebar: nav + theme toggle (visual only)
- Main: page content
- Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **Tiles**: This Month Spend • Outstanding Bills • Budget Health • Cashflow (In–Out).
- **Budgets Bar**: top 5 categories with progress (green/amber/red classes).
- **Alerts** (copy): upcoming card bill, nearing budget, unusual spend flag.
- **Recent Imports** strip: “12 SMS parsed • 3 UPI entries • 1 needs review”.

### 5.2 Transactions

- **Filter Bar**: account, date range, category, merchant, amount range.
- **List/Table Rows**:

  - Left: merchant + category pill + note icon
  - Right: amount (− for debit, + for credit), account chip, date
  - Sub-row: tags (UPI/SMS), “Auto-categorized: Food (rule #3)” label (visual)

- Bulk actions (visual): re-categorize, split, mark recurring.

### 5.3 Budgets

- **Category Cards**: limit, spent, remaining; month selector.
- **Drill-down**: list of transactions contributing to the budget.
- **Set Budget** form (visual): monthly/weekly, rollover toggle (visual).

### 5.4 Insights

- **Tiles**: Top category, Top merchant, Avg daily spend, Savings rate (copy only).
- **Charts** (CSS only):

  - Category bars, Merchant bars, Month trend blocks, Income vs Expense bars.

- **Recurring Bills** list (visual detection labels): rent, internet, subscriptions.

### 5.5 Import (Core)

- Tabs: **SMS Parse** • **UPI Import** • **CSV Upload**
- **SMS Parse**:

  - Paste area (static): example SMS lines.
  - **Parse Preview** table (visual): merchant, amount, date, inferred category, confidence chip.
  - Pattern tips via `<details>` (e.g., “spent/debited/txn ref/UPI/POS”).

- **UPI Import**:

  - Enter UPI ID (visual): `name@okbank`
  - Paste mock statement lines OR upload placeholder (no JS).
  - Preview transactions with payer/payee, note, UTR (mock), amount.

- **CSV Upload** (placeholder): show mapped columns (date, amount, description, account).

### 5.6 Accounts

- **Account Cards**: Bank/Card/Wallet/UPI handle; last import, balance (manual field), statement link.
- **Rules** `<details>`: “Map ‘SWIGGY’ → Food; ‘OLA’ → Transport”.
- **Statement** (static table): posted date, description, amount, running balance (copy).

### 5.7 Receipts (Optional)

- **Receipt Card**: thumbnail placeholder, merchant, date, amount, link to transaction (visual).
- Upload button (non-functional) and “Add note” area.

### 5.8 Settings

- Currency: INR (₹), USD, EUR; **Number format** (tabular numerals class).
- Categories manager: add/rename/emoji (visual).
- **Rules**: text contains → category/account/merchant (visual list).
- **Privacy**: local-only concept, masking examples, export (CSV/JSON) placeholders.
- Theme: Light/Dark/High-contrast; Reduced Motion.

### 5.9 About

- How parsing works (concept), **security & privacy**, disclaimers (“approximate; verify statements”).

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Stat Tile**, **Budget Bar**, **Alert Banner**
- **Transaction Row / Table**, **Category Pill**, **Merchant Chip**
- **Filter Pills**, **Date/Amount Range fields (visual)**
- **Import Preview Table** with **Confidence Chip**
- **Account Card**, **Rule Row**
- **Chart Blocks** (bars/heatmap), **Cashflow Badge**
- **Receipt Card**, **Print Header/Footer**

---

## 7) Data Model (future-ready; no code)

**Transaction**

- `id`, `date`, `amount`, `type` (debit|credit), `currency`, `accountId`, `merchantId`, `categoryId`, `notes`, `source` (sms|upi|csv|manual), `raw` (original text), `confidence` (0–1), `isRecurring` (bool), `splitOfId` (optional)

**Account**

- `id`, `type` (bank|card|wallet|upi), `name`, `numberMasked`, `balance`, `lastImportedAt`

**Merchant**

- `id`, `name`, `aliases[]`, `defaultCategoryId`

**Category**

- `id`, `name`, `icon`, `budgetMonthly`, `rollover` (bool)

**Rule**

- `id`, `match` (contains|regex), `pattern`, `actions` ({categoryId, merchantId, accountId})

**SmsMessage / UpiEvent**

- `id`, `text` / `{from, to, note, utr}`, `parsedAt`

**Insight**

- `month`, `totals` (income, expense), `byCategory[]`, `byMerchant[]`, `recurring[]`

**User**

- `currency`, `theme`, `a11yPrefs`, `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.tile--spend`, `.budget__bar`, `.txn-row__amount--debit`, `.pill--category`, `.import__confidence--low`, `.chart__bar--food`, `.rule-row__pattern`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — tiles, rows, pills, bars, tables, banners
  5. `layouts.css` — header/sidebar/content grids
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — statements & budget reports

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent: #2563EB
- Income: #16A34A • Expense: #DC2626 • Warning: #F59E0B • Info: #3B82F6

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB (AA)

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Use **tabular numerals** for amounts & balances.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Focus rings high-contrast; reduced-motion variant.

---

## 10) Accessibility & Privacy

- Landmarks: `<header> <nav> <main> <footer>`; one H1/page.
- Labels for all inputs; visible focus; keyboard navigable.
- Not color-only: pair icons/text with debit/credit indicators.
- **Privacy copy**: local-only concept; show examples of masking (`XXXX1234`, `name@ok****`).
- Disclaimers: parsing is approximate; verify against bank statements.

---

## 11) Print Styles

- **Monthly Statement**: opening/closing balance, totals by category, transactions table.
- **Budget Report**: category limits vs actual, notes.
- Hide nav; black on white; page numbers & footer.

---

## 12) File & Folder Structure

```
root
 ├─ index.html            (Dashboard)
 ├─ transactions.html
 ├─ budgets.html
 ├─ insights.html
 ├─ import.html           (SMS / UPI / CSV)
 ├─ accounts.html
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

- **Dashboard nudge:** “You’re at **72%** of your Food budget. 6 days left in the month.”
- **Import tip (SMS):** “Look for patterns like _‘INR 450.00 spent at’_, _‘debited from a/c’_, _‘UPI txn’_.”
- **Import tip (UPI):** “Match handles like **alice\@okicici**; keep UTR for reference.”
- **Rule helper:** “If description contains **‘SWIGGY’**, set category to **Food**.”
- **Privacy banner:** “Parsing happens on-device in V1 (concept). You control exports.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **4 tiles**, **budget bar**, and **alerts**.
- Transactions page lists **≥20 rows** with filters and category pills.
- Budgets page displays **≥8 categories** with progress bars and one drill-down.
- Insights page shows **category & merchant bars**, **month trend**, and **recurring bills** list.
- Import page demonstrates **SMS parse preview**, **UPI import preview**, and **CSV mapping** (visual).
- Accounts page lists **bank/card/wallet/UPI** with rule examples.
- Print styles output **Monthly Statement** and **Budget Report** cleanly.
- Meets baseline a11y (headings, labels, focus, contrast).

---

## 15) Future Enhancements

- Real SMS permissions (Android) and **on-device regex/NLP** parsers.
- **UPI** integrations (where available) or email receipt parsing.
- Auto-categorization model; merchant normalization; duplicate detection.
- Recurring detection (rent/subscriptions) with reminders.
- OCR for receipts; currency conversion; savings goals; shared budgets.
- Bank email PDF/HTML parsing; webhooks; PWA offline mode.
- Data encryption at rest; granular export; audit log.

---

## 16) Sample Static Data (populate UI)

**Example SMS lines (paste into Import preview)**

- “INR 289.00 spent on your HDFC Credit Card at SWIGGY on 02-Sep 19:24. Avl Cr Lmt INR …”
- “Rs. 199.00 debited from A/c **XXXX1234** via UPI to OLA CABS on 03-Sep 08:05. UTR 2XXXXXXXXX.”
- “INR 1,299.00 spent at AMAZON on 04-Sep 21:10. Txn ID …”

**Parsed Preview (visual table)**

- SWIGGY — **₹289** — Food — 02 Sep — Account: HDFC CC — Source: SMS — Confidence: **High**
- OLA — **₹199** — Transport — 03 Sep — Account: UPI — Source: UPI — Confidence: **Med**
- AMAZON — **₹1,299** — Shopping — 04 Sep — Account: HDFC CC — Source: SMS — Confidence: **High**

**Budgets (₹/month)**

- Food **₹8,000** (Spent **₹5,760**) • Transport **₹3,000** (₹2,220) • Shopping **₹4,000** (₹1,299) • Bills **₹6,500** (₹4,100)

**Top Merchants (month)**

- SWIGGY ₹1,450 • AMAZON ₹3,899 • OLA ₹820 • BIG BAZAAR ₹1,240 _(mock)_

---

If you want, I can convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) to drop straight into Cursor.
