# Client Feedback Hub — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a centralized platform to **collect, triage, and analyze user feedback** across channels. V1 is **JavaScript-free**—no real integrations, NLP, deduping, identity resolution, or dashboards. All dynamic bits are **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Bring **all feedback into one place** with consistent **triage → tag → prioritize → act** flows.
- Turn raw comments into **themes, insights, and roadmap links** (visual only).
- Provide **executive-friendly views** (KPIs, trends) and **team workflows** (ownership, SLAs).
- Keep the shell **accessible, responsive, printable**, and brandable.

---

## 2) Constraints (V1)

- **No JavaScript**: no OAuth, webhooks, ingestion, or search backend.
- Use semantic HTML (`<form>`, `<details>`, tables) and **pure CSS** (chips, meters, charts, kanban, heatmaps).
- “Sentiment”, “Similarity”, “Priority score”, and “Auto-tags” are **copy/UI only**.

---

## 3) Personas & Core User Stories

- **PM / Designer**: “Find top pain themes this quarter and link them to roadmap items.”
- **Support Lead**: “Triage high-urgency bugs and route to the right team.”
- **UX Researcher**: “Cluster verbatims into themes and produce an insight report.”
- **Exec**: “See NPS/CSAT trends and biggest drivers at a glance.”

**Stories (visual-only)**

1. **Inbox**: review new feedback, add tags, set sentiment/priority, assign owner.
2. **Explorer**: filter by product area, tag, sentiment, plan, or segment; save a view.
3. **Themes**: merge/rename tags, group into themes; kanban from “Hypothesis → Validated”.
4. **Insights**: dashboards (CSS charts) with volume, NPS/CSAT, top themes, and drivers (copy).
5. **Roadmap link**: attach feedback sets to epics and show impact score (copy).
6. **Report**: print-friendly summary with highlights and next actions.

---

## 4) Information Architecture

- **Dashboard** — KPIs, trends, highlights
- **Inbox** — new feedback triage
- **Explorer** — filters, saved views, bulk actions
- **Themes & Tags** — taxonomy, merge, governance
- **Insights** — charts, drivers (copy), impact-effort matrix
- **Surveys** — NPS/CSAT/PMF templates (static)
- **Roadmap** — epics list, linked feedback, impact notes
- **Reports** — quarterly/launch summaries (printable)
- **Settings** — channels, privacy, roles, branding, scales
- **About** — methodology & disclaimers

**Global Shell**
Header: product name, environment chip, search (decorative), print link
Sidebar: nav + theme toggle (visual)
Main: page content • Footer: help/version/legal

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **KPI Tiles**: New this week, Tagged %, Median priority, NPS, CSAT, Top theme.
- **Trend Bars** (CSS): weekly feedback volume; NPS/CSAT line (visual).
- **Top Drivers** list (copy): “Checkout friction”, “Slow startup”, “Missing SSO”.
- **Recent Highlights**: 3 verbatims with tags and sentiment badges.
- **Nudge banner**: “Tag coverage < 80% this week.”

### 5.2 Inbox (Triage)

- **Table/List** of feedback cards:

  - Source (in-app, email, app store, ticket), product area, verbatim excerpt, **sentiment** chip (Pos/Neu/Neg), **priority** chip (P0–P3).
  - Actions: Tag, Assign, Link to Epic, Mark as Duplicate (visual).

- **Right Drawer** (on select): full verbatim, customer attributes (plan, region), history, similar items (copy).

### 5.3 Explorer

- **Filter bar**: Product area, Tag(s), Sentiment, Priority, Segment, Date range.
- **Result grid/table** with **bulk actions**: add/remove tag, change owner, link to epic.
- **Saved Views** chips (e.g., “Q3 Bugs”, “Enterprise UX”).
- **Side stats**: count by tag/theme as small bars.

### 5.4 Themes & Tags

- **Tag List**: usage count, last 30d trend spark (CSS).
- **Theme Board** (kanban): Backlog → Investigate → Validated → Shipped.
- **Merge/Rename** (visual): select two tags → “Merge into”.
- **Governance** note (copy): definitions, examples, do/don’t.

### 5.5 Insights

- **Tiles**: Volume Δ%, NPS, CSAT, Neg\:Pos ratio, Coverage %, Duplicates merged.
- **Charts** (CSS only):

  - Volume by product area (stacked bars)
  - Sentiment over time (bands)
  - Impact vs Effort matrix (grid with dots, labels)

- **Drivers** (copy): “Top 3 tags associated with negative feedback”.
- **Priority Model** (copy): show RICE or custom weights; editable sliders (visual).

### 5.6 Surveys

- **Templates**: NPS, CSAT, PMF, “How disappointed if…?”
- **Question editor** (visual): scale, question text, follow-up free-text, targeting.
- **Mock results**: distribution bars, top comments with tags.

### 5.7 Roadmap

- **Epics list**: status (Planned/In Progress/Done), team, target quarter.
- **Epic Detail**: linked feedback count, representative quotes, **impact score** (copy), dependencies, release notes (placeholder).
- **Traceability**: “This theme → epic(s) → release” breadcrumbs (visual).

### 5.8 Reports

- **Quarterly Review** template: KPIs, top themes, top quotes, actions & owners.
- **Launch Readout**: before/after metrics, issues found, fixes shipped.
- **Export/Print** buttons (visual); print stylesheet outputs clean PDFs.

### 5.9 Settings

- **Channels** (visual toggles): In-app widget, Email alias, Support tickets, App store, Social, Interviews.
- **Privacy**: PII redaction (copy), retention window, access levels.
- **Scales**: sentiment labels, priority scale, SLA targets.
- **Branding**: logo, colors, typography.
- **Roles**: Admin, Analyst, Contributor, Viewer.

---

## 6) Component Inventory (CSS-only)

- **Feedback Card** (source badge, sentiment, priority, tags)
- **Tag Chip**, **Theme Pill**, **Owner Avatar**
- **Priority Meter** (P0–P3), **Sentiment Badge** (pos/neu/neg)
- **Trend Bars**, **Sparkline**, **Donut Tile**
- **Impact–Effort Matrix** (grid), **Drivers List**
- **Kanban Column** for themes, **Merge Dialog** (visual)
- **Filter Chips**, **Saved View Chip**
- **Epic Card** & **Trace Breadcrumbs**
- **Report Section** header, **Quote Block**
- **Alert/Nudge Banner** (“Tag coverage low”, “PII detected”)
- **Print Header/Footer** (reports & readouts)

---

## 7) Data Model (future-ready; no code)

**Feedback**

- `id`, `source` (in_app|email|store|ticket|social|interview), `submittedAt`, `author` (anon|acctId?), `verbatim`, `productArea`, `tags[]`, `themeId?`, `sentiment` (pos|neu|neg), `priority` (0–3), `status` (new|triaged|linked|closed), `ownerId?`, `duplicates[]`

**Tag**

- `id`, `name`, `definition`, `usageCount`, `parentThemeId?`

**Theme**

- `id`, `name`, `status` (backlog|investigate|validated|shipped), `tagIds[]`, `notes`

**Epic / RoadmapItem**

- `id`, `team`, `title`, `status`, `quarter`, `impactScore`, `linkedFeedbackIds[]`

**SurveyResponse**

- `id`, `type` (nps|csat|pmf), `score`, `comment`, `segment`, `submittedAt`, `tags[]`

**Insight**

- `id`, `period`, `highlights[]`, `drivers[]`, `charts{}`

**User**

- `id`, `name`, `role`, `email?`, `avatar?`

**Settings**

- `channels{}`, `privacy{retentionDays, piiMasking}`, `scales{priorityLabels, sentimentLabels}`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.feedback-card`, `.feedback-card__meta`, `.badge--source`, `.badge--sentiment-neg`,
  `.chip--tag`, `.pill--theme`, `.meter--priority`, `.trend__bar`, `.sparkline`,
  `.kanban__col`, `.driver__item`, `.matrix__dot`, `.epic__card`, `.alert--privacy`
- Layers:

  1. `tokens.css` — colors, spacing, type
  2. `base.css` — reset & typography
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — cards, chips, badges, meters, charts, kanban
  5. `layouts.css` — shell, two/three-pane, boards
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — reports & readouts

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Primary: #2563EB • Positive: #16A34A • Neutral: #64748B • Negative: #DC2626
- Accent: #8B5CF6 (themes) • Info: #3B82F6 • Warning: #F59E0B

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Type**

- Display 28 • H1 24 • H2 20 • Body 16 • Caption 12–13
- **Monospace** for IDs; **tabular numerals** for scores.

**Spacing & Radius**

- Scale: 4/8/12/16/24/32 • Radius: 12 (cards), 6 (chips), 999 (pills)
- Focus rings: high-contrast; reduced-motion variant.

Icons: inbox, tag, merge, chart, sentiment, roadmap, shield.

---

## 10) Accessibility, Privacy & Compliance

- Landmarks `<header><nav><main><footer>`; single H1/page.
- Labels for all inputs, keyboard navigable, visible focus; no color-only signals.
- **Privacy copy**: PII redaction, consent for public sources, retention windows, role-based access.
- **Ethics note**: avoid quoting sensitive PII in reports; aggregate where possible.

---

## 11) Print Styles

- **Quarterly Insight Report**: KPIs, trends, top themes, representative quotes, actions.
- **Launch/Release Readout**: tagged issues, fixes, before/after metrics.
- Hide nav; black on white; page numbers; footer “Client Feedback Hub — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Dashboard)
 ├─ inbox.html           (Triage)
 ├─ explorer.html
 ├─ themes.html
 ├─ insights.html
 ├─ surveys.html
 ├─ roadmap.html
 ├─ reports.html
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

- **Dashboard nudge:** “Tag coverage below **80%**—prioritize triage to keep insights reliable.”
- **Inbox helper:** “Add at least **one product area** and **one theme** before assigning.”
- **Explorer tip:** “Save filters you reuse—views keep teams aligned.”
- **Theme governance:** “Define tags with examples; merge duplicates; archive stale.”
- **Insight note:** “Priority uses **RICE** (copy): Reach × Impact × Confidence ÷ Effort.”
- **Roadmap banner:** “Link ≥20 pieces of feedback to claim ‘evidence-backed’.”
- **Privacy warning:** “Remove emails/phone numbers from verbatims before sharing.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **≥6 KPI tiles**, volume/NPS trends, top drivers, and highlights.
- Inbox lists **≥12 feedback items** with sentiment/priority badges and an assignment flow (visual).
- Explorer supports filters and **saved view chips**; side stats show tag counts.
- Themes page renders a **kanban** with **≥8 tags** and merge/rename visual.
- Insights page displays **5+ tiles**, **2 charts**, and a **matrix** with labeled dots.
- Surveys page includes **NPS/CSAT/PMF** templates with mock results.
- Roadmap page shows **epics** with linked feedback counts and impact scores (copy).
- Reports print cleanly via **print.css** (Quarterly & Launch templates).
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real ingestion: APIs/webhooks for support tickets, app stores, email, in-app widget.
- **NLP**: language detection, sentiment, topic modeling, dedupe/similarity clustering.
- Identity resolution & segmentation; role-based access and PII masking.
- Weighted prioritization: **custom models** (e.g., revenue impact, churn risk).
- Closed-loop: notify users when issues ship; change logs; satisfaction follow-up.
- BI export, warehouse sync, and metric backfills; anomaly detection.
- Collaboration: comments, @mentions, approvals, and audit trails.
- Multi-product/tenant support; SSO; SCIM.

---

## 16) Sample Static Data (populate UI)

**KPI Tiles**

- New this week **264** • Tagged **78%** • NPS **+41** • CSAT **4.3/5** • Neg\:Pos **0.62** • Top theme **“Checkout UX”**

**Inbox entries**

- Source: **In-app** — _“Apple Pay fails with error on first attempt.”_ — Area: **Checkout** — **Neg** — **P1** — Tags: payments, ios
- Source: **Email** — _“Love the dashboards, but exports time out.”_ — Area: **Analytics** — **Neu** — **P2** — Tags: exports, performance
- Source: **Store** — _“Great app, needs dark mode on Android.”_ — Area: **UI** — **Pos** — **P3** — Tags: dark-mode, android

**Themes (kanban)**

- **Backlog:** multi-currency, onboarding hints
- **Investigate:** dark-mode, exports performance
- **Validated:** checkout error handling, team invites
- **Shipped:** SSO SAML, notification settings

**Insights (matrix dots)**

- High Impact / Low Effort: **Dark mode**
- High Impact / High Effort: **Checkout reliability**
- Low Impact / Low Effort: **Tooltip copy tweaks**

**Roadmap (epics)**

- **Checkout Resilience Q4** — Linked feedback **157** — Impact score **High**
- **Export Pipeline v2** — Linked feedback **68** — Impact score **Med**
- **Mobile Dark Mode** — Linked feedback **44** — Impact score **Med**

---

If you want, I can convert this into **ready-to-paste page skeletons** (still no JS) or a **README.md** tailored for your Cursor workspace.
