# Smart Investment Tracker — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an investment dashboard that shows a user’s **portfolio**, **market trend snapshots**, and **AI-style rebalancing suggestions** (all **visual placeholders**). V1 is **JavaScript-free**—no live prices, trades, or advice. Pure UI scaffolding you can paste into **Cursor** and wire up later.

---

## 1) Vision & Goals

- Provide a **clear portfolio view** and **risk-aware suggestions** (rebalance, diversify, trim, add).
- Present **market/sector trends** as contextual hints (copy + bars, no live data).
- Encourage **long-term discipline** with goals, drift indicators, and allocation targets.
- Keep markup **semantic, accessible, responsive, printable**.

---

## 2) Constraints (V1)

- **No JavaScript**: no brokerage connections, quotes, charting libs, tax calcs, or orders.
- “AI Suggestions,” “signals,” and “risk scores” are **static placeholders**.
- Use native HTML patterns (`<details>`, tables, forms) and **pure CSS** for charts/badges.
- **Educational UI only**; add clear **disclaimers**.

---

## 3) Personas & Core User Stories

- **Hands-off Investor:** “Show me where I’m off-target; make it simple to rebalance.”
- **DIY Optimizer:** “Surface sectors/factors over- or under-weight vs my plan.”
- **New Investor:** “Explain suggestions in plain language with risks.”

**Stories (visual-only in V1)**

1. View **Portfolio** with asset mix (Equity/Bonds/Cash/Alt), sector split, top holdings.
2. See **AI Suggestions** (e.g., “Reduce single-stock concentration; add short-term bonds”).
3. Track **drift** vs **Target Allocation** and review a **Rebalance Plan** (mock steps).
4. Browse **Markets & Trends** tiles (macro copy, sector heat blocks).
5. Set **Goals & Risk** (time horizon, risk band) and see compatibility notes.
6. Print a **Portfolio Review** report.

---

## 4) Information Architecture

- **Dashboard** — total value (placeholder), returns bands, drift, quick suggestions
- **Portfolio** — holdings table, allocation donuts (CSS), sector/country bars
- **Suggestions** — AI-style rebalancing list with rationale & risks
- **Markets & Trends** — macro snapshot, sectors, factors, yields (visual)
- **Transactions** — static ledger (buys/sells/dividends) for context
- **Goals & Risk** — target allocation, horizon, risk score, IPS notes (visual)
- **Insights** — contributions vs performance, fees, diversification score (visual)
- **Settings** — currency, theme, privacy, data import placeholders
- **About** — methodology and **not-investment-advice** disclaimer

**Global Shell**

- Header: app name, date range selector (visual), print link
- Sidebar: nav + theme toggle (visual)
- Main: page content
- Footer: version/help

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **Tiles**: Portfolio Value (—), 1Y Range (bar), Drift from Target (%), Diversification Score.
- **Quick Suggestions** (3 cards):

  - “Trim: Overweight Tech +6% vs target”
  - “Add: Short-Term Bonds to reduce duration risk”
  - “Rebalance: Move 3% from Single Stock → Total Market ETF”

- **Allocation Strip**: Equity • Bonds • Cash • Alt (conic-gradient donut; CSS)
- **Nudge**: “Recheck risk after major life events.”
  `<details>` → “Why this matters”

### 5.2 Portfolio

- **Holdings Table** (static): Ticker • Name • Class • Weight % • Cost • Est. Gain/Loss • Fee (ER) • Notes
- **Target vs Actual**:

  - **Bars** per class (Equity/Bond/Cash/Alt) with **Delta chip** (+/−)

- **Sector & Region**:

  - CSS bars grid (IT/HC/Cons/Ind/Fin/Energy/Real Estate)
  - Region chips (US • Europe • India • APAC ex-JP • EM)

- **Concentration Warning**: callout if any holding >10%

### 5.3 Suggestions (Core)

- **Suggestion Card**:

  - Title: “Reduce Concentration in ABC (12% → 7%)”
  - **Rationale**: “Single-name risk; sector overweight vs plan.”
  - **Action Plan** (visual steps):

    1. Trim ABC −5%
    2. Add Bond ETF +3%
    3. Add Intl Total Market +2%

  - **Impact Row**: Risk ↓ • Fees — • Yield ↑ (icons + small text)
  - **Risks/Tradeoffs** `<details>`: “Tracking error vs benchmark may rise.”
  - **Tax Note** (copy): “Consider tax implications; tax-lot harvesting later.”

- **Other Patterns**: “Shift duration”, “Add value factor”, “Raise cash buffer”, “Consolidate funds”
- **Approve Plan** (visual only) → “Rebalance Summary” page

### 5.4 Markets & Trends

- **Macro Tiles**: “Equities: mixed”, “Yields: elevated”, “Credit spread: stable” _(copy-only)_
- **Sector Heat Blocks** (CSS): 3×4 grid intensity classes (− − • • + +)
- **Yield Curve**: horizontal blocks: 3M • 2Y • 5Y • 10Y • 30Y (heights = CSS only)
- **Factor Snapshot**: Growth • Value • Quality • Small • Momentum (bars)
- **Note**: “Trends are simplified placeholders; verify with data.”

### 5.5 Transactions

- Table: Date • Account • Action (Buy/Sell/Div/Reinv) • Ticker • Qty • Price • Amount • Notes
- Filters (visual): Account • Security Type • Date Range

### 5.6 Goals & Risk

- **Goal Cards**: Retirement • Education • House (target amount + date)
- **Risk Band**: Conservative • Balanced • Growth (radio visuals)
- **Target Allocation Editor**: Equity % • Bond % • Cash % • Alt % (inputs are static)
- **Compatibility Note**: “Current risk is **slightly above** your band due to Tech overweight.”

### 5.7 Insights

- **Tiles**: Contributions (12m), Fees est/yr, Dividend yield est, Turnover (copy)
- **Attribution Blocks**: Contributions vs Market Move (two bars)
- **Diversification Score** (visual meter) & “Top Correlated Holdings” list (copy-only)

### 5.8 Settings

- Currency (₹/\$/€), Region, Theme (Light/Dark/High-contrast)
- Data (visual): CSV import placeholder, “Broker sync (future)”
- Privacy: local-only concept, export placeholders

### 5.9 About

- Methods: allocation, drift calc, suggestion templates
- Disclaimers: **educational UI**, not investment/financial advice

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Stat Tile**, **Delta Chip**, **Nudge Banner**
- **Donut Allocation** (conic gradient), **Bar Charts**, **Heat Blocks**
- **Holdings Table** with sticky head
- **Suggestion Card** (rationale, plan steps, impacts, risks)
- **Risk Band Radios**, **Goal Card**
- **Badge** (e.g., “High Concentration”, “Low Fee”), **Alert** (tax)
- **Print Header/Footer** for reports

---

## 7) Data Model (future-ready; no code)

**Holding**

- `id`, `ticker`, `name`, `class` (equity|bond|cash|alt), `sector`, `region`,
  `weightPct`, `targetPct`, `costBasis`, `estValue`, `estGainLossPct`, `expenseRatio`, `notes`

**Portfolio**

- `holdings[]`, `asOfDate`, `totalValue`, `allocationTarget` ({equity,bond,cash,alt})

**Suggestion**

- `id`, `title`, `rationale`, `actions[]` ({ticker|class, changePct, note}),
  `impacts` ({risk, yield, fee, diversification}), `risks[]`, `taxNotes[]`

**MarketSnapshot**

- `asOfDate`, `sectors[]` ({name, signalLevel}), `factors[]` ({name, strength}), `yields[]` ({tenor, level})

**Goal**

- `id`, `name`, `targetAmount`, `targetDate`, `riskBand`, `targetAllocation`

**Transaction**

- `date`, `account`, `type`, `ticker`, `qty`, `price`, `amount`, `note`

**User**

- `currency`, `region`, `theme`, `a11yPrefs`, `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM** examples:
  `.tile--value`, `.donut__slice--equity`, `.bar--sector-it`, `.delta-chip--over`,
  `.suggestion__impact--risk-down`, `.risk-band__option--selected`,
  `.heat__cell--pos-2`, `.nudge--info`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements
  3. `utilities.css` — grid/flex/gaps/visually-hidden
  4. `components.css` — tiles, donuts, bars, cards, tables, badges
  5. `layouts.css` — header/sidebar/grids
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — portfolio review

---

## 9) Design System

**Colors (Light)**

- Background: #F7FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent (actions): #2563EB
- Equity: #3B82F6 • Bonds: #10B981 • Cash: #F59E0B • Alt: #8B5CF6
- Positive chip: #16A34A • Negative chip: #DC2626 • Info: #3B82F6

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- **Tabular numerals** class for tables.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Reduced-motion theme available.

---

## 10) Accessibility & Disclaimers

- Landmarks: `<header> <nav> <main> <footer>`; single H1 per page.
- Labels tied to controls; visible focus; keyboard navigable.
- Do **not** use color alone for risk or performance—pair with text/icons.
- Add clear **educational-use** and **not-investment-advice** copy on Suggestions & About.
- Avoid real tickers/prices in V1; use placeholders.

---

## 11) Print Styles

- **Portfolio Review** (A4/Letter): allocation vs target, top holdings, concentration alerts, suggestion summary, risks & notes.
- Black on white; hide nav; page numbers & footer: “Smart Investment Tracker — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Dashboard)
 ├─ portfolio.html
 ├─ suggestions.html
 ├─ markets.html         (Markets & Trends)
 ├─ transactions.html
 ├─ goals.html           (Goals & Risk)
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
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Nudge (Dashboard):** “Your equity is **+8%** over target. Consider a light rebalance.”
- **Suggestion card subtitle:** “Goal: reduce concentration & volatility while keeping expected return similar.”
- **Risk note:** “Changes can increase tracking error vs your benchmark.”
- **Tax banner:** “Rebalancing may trigger capital gains. Consider tax lots/harvesting.”
- **Markets note:** “Signals are simplified placeholders; verify data before acting.”
- **About disclaimer:** “This interface is for **education** only and is **not investment advice**.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **4 tiles**, allocation donut, **3 suggestion cards**, and a nudge.
- Portfolio page lists **≥12 holdings** with target vs actual and sector/region bars.
- Suggestions page includes **≥4** varied actions with rationale/risks/impacts.
- Markets page shows **macro tiles**, **sector heat blocks**, **yield blocks**, **factor bars**.
- Goals & Risk page lets users set target allocation and risk band (visual).
- Insights page shows contributions vs market, fees est, diversification meter.
- Print stylesheet outputs a clean **Portfolio Review**.
- Meets baseline a11y (headings, labels, focus, contrast).

---

## 15) Future Enhancements

- Brokerage connections (read-only) & **real quotes**; intraday delay awareness.
- Real **optimization engine**: minimize drift with tax-aware constraints.
- **What-if** simulator; glide paths by goal horizon.
- Factor/sector attribution; fee & tax drag analytics.
- Rebalance ticket export; IPS export; alerts for drift/over-concentration.
- News & corporate actions feed; ESG screens (optional).
- PWA + offline snapshots; CSV import/export.

---

## 16) Sample Static Data (populate UI)

**Holdings (sample)**

- **VTI** — US Total Market — Equity — **32%** (Target 30%) — ER 0.03%
- **VXUS** — Intl ex-US — Equity — **18%** (Target 20%) — ER 0.07%
- **BND** — US Aggregate Bond — Bond — **22%** (Target 25%) — ER 0.04%
- **ICICI Liquid** — Cash — **8%** (Target 5%)
- **Gold ETF** — Alt — **6%** (Target 5%)
- **ABC** (single stock) — Equity — **14%** (Target 5%) ⚠︎

**Suggestion Examples**

- **Trim ABC −5%** → **Add BND +3%** & **VXUS +2%**. _Rationale:_ single-stock risk + international underweight.
- **Shift 2% Cash → Bonds** to meet fixed-income floor.
- **Add 1% Gold** as diversifier; small inflation hedge.

**Markets Snapshot (placeholders)**

- Sectors: IT **+** • Energy **−** • Health **•** • Financials **+** • Real Estate **−**
- Yields: 3M **high** • 10Y **elevated** • 30Y **stable**
- Factors: Value **•** • Growth **+** • Small **•** • Momentum **+**

---
