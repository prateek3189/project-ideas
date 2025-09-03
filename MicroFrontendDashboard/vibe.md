# Micro-Frontend Dashboard Builder — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** of a _drag-and-drop_ platform where enterprise teams compose a dashboard from **micro-frontends (MFEs)**. V1 is **JavaScript-free**—no real drag, live data, auth/SSO, deployments, or Module Federation runtime. All interactive behavior is **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- **Unify** many apps into **one dashboard**: tiles/widgets sourced from different teams.
- Enable **no-code page assembly** (drag grid, resize, config panels) with **role-based controls**.
- Provide **environment awareness** (Dev/Staging/Prod), **versioning**, and **publishing** flows (visual).
- Keep the shell **accessible, responsive, themeable, and printable**.

---

## 2) Constraints (V1)

- **No JS**: grid “drag/resize” is **visual only** (handles, ghosts, guides). No live federation, no iframes.
- **Placeholders** for: SSO, RBAC, audit log, health checks, CI/CD deploys, web components registry.
- Use semantic HTML, `<details>` for config drawers, **pure CSS** for grids, badges, meters, and status.

---

## 3) Personas & Core User Stories

- **Platform Admin:** “Curate widget catalog, manage tenants, enforce policies.”
- **Space Owner (Ops/PM):** “Assemble pages from approved widgets; publish to a team.”
- **Widget Dev:** “Register new widget versions, attach documentation and changelog.”
- **Viewer (Exec/Agent):** “Consume dashboards with env/status context.”

**Stories (visual-only)**

1. **Create a Space** → add **Pages** → place **Widgets** from Catalog → **Configure** → **Publish**.
2. **Version** a widget; **pin** a version or **auto-upgrade** (visual toggle).
3. **Permissions**: grant page access by role/team (chips).
4. **Observability**: see widget **health** status and **latency** bars (mock).
5. **Theming**: apply brand colors, light/dark, density (visual).

---

## 4) Information Architecture

- **Home / Overview** — spaces, recent activity, platform health
- **Spaces** — list of spaces; inside: pages, members, themes
- **Page Builder** — canvas (grid), catalog drawer, properties panel, preview/publish
- **Catalog** — widget registry, versions, compatibility, owners
- **Releases** — publish history, rollbacks (visual), change notes
- **Permissions** — roles, policies (visual), audits
- **Settings** — tenants, environments, themes, SSO (placeholder)
- **Docs** — embedding guide, contracts, governance
- **About** — scope, disclaimers

**Global Shell**
Header: product name, tenant & env chips, search (decorative), print link
Sidebar: nav + theme toggle (visual)
Main: page content • Footer: build/version/help

---

## 5) Screen Blueprints

### 5.1 Home / Overview

- **KPI Tiles**: Spaces, Pages, Widgets, Healthy %, Incidents (mock).
- **Recent Activity**: “Published Space ‘Ops NOC’”, “Widget `alerts-table` v3.2 approved”.
- **Environment Bar**: Dev | Staging | Prod (chips) with health meters (CSS).

### 5.2 Spaces (List & Detail)

- **Space Cards**: name, owners, pages count, last publish, status (Draft/Live).
- **Space Detail Tabs**: **Pages** • **Members** • **Theme** • **Releases**

  - **Pages**: table of pages with **Edit**, **Preview**, **Publish** (visual).
  - **Members**: role chips (Owner/Editor/Viewer).
  - **Theme**: brand colors, logo, density (compact/cozy).
  - **Releases**: list with version notes and **Rollback** (visual).

### 5.3 Page Builder (Core)

- **Top Bar**: page path, breakpoint selector (Desktop/Tablet/Mobile), “Preview”, “Publish”.
- **Canvas Grid**: CSS grid with **ghost tiles**, **resize handles** (visual), **snap guides** (dotted lines).
- **Catalog Drawer** (left): searchable list of **Widgets** with tags, owners, version badges.
- **Properties Panel** (right):

  - **Widget Config**: title, data source (visual), refresh cadence (copy), inputs/props table, feature flags (visual).
  - **Bindings** (visual): connect widget inputs to outputs of other widgets (line list).
  - **Visibility Rules**: role/device/time filters (chips).

- **Grid Ops**: Add row/column (buttons, visual only), “Auto-layout” badge (copy).
- **Empty State**: “Drag widgets from the Catalog” (visual hint).

### 5.4 Catalog (Registry)

- **Widget Cards**: name/id, description, **Kind** (Web Component/iframe/Module Federation; copy only), maintainer, last updated.
- **Version Drawer**: versions table with **SemVer**, **compat matrix** (Shell vX, CSS tokens vY), **Changelog**.
- **Approval Flow** (visual): Draft → Review → Approved → Deprecated.

### 5.5 Releases

- **Publish Summary**: pages affected, widget diffs (chips: new/updated/removed).
- **Checks** (copy): compatibility, perf budget, security policy.
- **Rollbacks** (visual): choose previous release; reason textarea.

### 5.6 Permissions

- **Role Matrix**: Spaces × Roles with toggles (visual).
- **Policies**: Data egress blocked? PII redaction? (copy-only indicators)
- **Audit Log**: who did what when (static rows).

### 5.7 Settings

- **Tenants & Environments**: Dev/Stage/Prod cards; **Promote** visual button.
- **SSO**: SAML/OIDC placeholders; “Test login” (visual).
- **Tokens**: CSS design tokens (brand palette).
- **Integrations**: Git provider, CI, Observability (placeholders).

### 5.8 Docs

- **Embedding Contracts** (copy): events, props, resize API (future).
- **Style Guide**: tokens, spacing, z-index, focus rings.
- **Governance**: versioning, deprecation, security review checklist.

---

## 6) Component Inventory (CSS-only)

- **Canvas Grid** with **Tile** shell, **Drag Handle** (visual), **Resize Handle** (SE corner)
- **Widget Card** (catalog), **Version Badge**, **Owner Chip**
- **Property Panel** sections: **Props Table**, **Bindings List**, **Rules Chips**
- **Breakpoint Switcher**, **Env Chip**, **Status Badge**
- **Publish Banner**, **Checklist Item**, **Diff Chip** (added/updated/removed)
- **Health Meter** (bar/ring), **Latency Pill**
- **Role Matrix** table, **Policy Tag**, **Audit Row**
- **Theme Preview** (brand colors & type scale)
- **Print Header/Footer** for release notes

---

## 7) Data Model (future-ready; no code)

**Tenant**

- `id`, `name`, `environments[]` (`{name, url, status}`), `theme{ tokens }`

**Space**

- `id`, `tenantId`, `name`, `owners[]`, `pages[]`, `status` (draft|live), `lastReleaseId`

**Page**

- `id`, `spaceId`, `name`, `path`, `layout` (`{rows, cols, tiles[]}`), `visibilityRules[]`

**Tile**

- `id`, `widgetId`, `version`, `gridPos` (`{x,y,w,h}`), `props{}`, `bindings[]`, `flags[]`, `refresh` (ms)

**Widget**

- `id`, `name`, `kind` (wc|iframe|mf), `ownerTeam`, `capabilities[]`, `versions[]`

**WidgetVersion**

- `id`, `widgetId`, `semver`, `compat` (`{shell, tokens}`), `changelog`, `status` (draft|approved|deprecated)

**Release**

- `id`, `spaceId`, `env`, `createdAt`, `by`, `pages[]`, `diff{ added[], updated[], removed[] }`, `notes`

**Permission**

- `id`, `spaceId`, `role` (owner|editor|viewer), `principal` (user|group), `scopes[]`

**HealthMetric**

- `widgetId`, `env`, `status` (up|degraded|down), `latencyMs`, `errorRate`

**AuditEvent**

- `id`, `actor`, `action`, `target`, `at`, `meta{}`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.canvas`, `.tile`, `.tile__handle--drag`, `.tile__handle--resize`,
  `.catalog__card`, `.badge--version`, `.chip--owner`,
  `.props__table`, `.bindings__row`, `.rules__chip`,
  `.env__chip--prod`, `.status--live`, `.diff--added`,
  `.meter--health`, `.pill--latency-ok`, `.matrix__cell--deny`,
  `.theme__preview`, `.banner--publish`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements, forms
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — tiles, cards, chips, meters, tables, banners
  5. `layouts.css` — shell, builder three-pane, lists
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — release notes & governance checklists

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Primary: #2563EB • Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Accents: Builder grid lines (muted), Tile borders (subtle), Handles (primary)

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display 28 • H1 24 • H2 20 • Mono 13–14 for IDs • Body 16 • Caption 12–13
- **Tabular numerals** for versions and latency.

**Spacing & Radius**

- Scale: 4/8/12/16/24/32; Radius: 12 (cards), 8 (tiles), 999 (chips)
- Focus: 3px high-contrast outlines; reduced-motion variant.

**Iconography**

- Tile, grid, plug, building blocks, rocket (publish), shield (policy), rollback.

---

## 10) Accessibility & Governance

- Landmarks `<header><nav><main><footer>`; single H1/page.
- Labels on all form fields; keyboard focus visible; no color-only signals (use icons/text).
- **Governance copy**: review checklist before publish (security, accessibility, privacy).
- **Deprecation policy** (copy): sunset dates, auto-notify space owners.
- **Content security note**: forbid inline scripts in MFEs; sandbox iframes (future).

---

## 11) Print Styles

- **Release Notes**: space/page diffs, impacted widgets, approvals, rollback plan.
- **Catalog Sheet**: widget list with owners, last updated, status.
- Hide nav; black on white; page numbers; footer “Micro-FE Builder — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Overview)
 ├─ spaces.html          (Spaces list)
 ├─ space-detail.html    (Pages/Members/Theme/Releases)
 ├─ builder.html         (Page Builder)
 ├─ catalog.html         (Widget Registry)
 ├─ releases.html        (Publish history)
 ├─ permissions.html
 ├─ settings.html
 ├─ docs.html
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

- **Builder empty state:** “Drag widgets from the **Catalog** to start. Use handles to **resize** and **snap** to the grid.”
- **Publish checklist items:** “Compatibility check passed • Token usage compliant • Accessibility review done • Owners approved.”
- **Versioning note:** “This page **pins** `alerts-table@3.2`. Toggle **Auto-upgrade** to use latest approved minor.”
- **Health tip:** “High latency in Staging—consider **lazy mount** or **reduce payload** (copy).”
- **Policy banner:** “External network calls must use **approved domains** (visual policy).”
- **Rollback helper:** “Releases keep a **full diff**; you can revert without affecting other spaces.”

---

## 14) Acceptance Criteria (V1)

- Home shows **≥5 KPI tiles**, **recent activity**, and **environment health** bars.
- Spaces page lists **≥6 spaces**; Space Detail contains **Pages/Members/Theme/Releases** tabs.
- Builder presents a **3-pane** layout (Catalog • Canvas • Properties) with at least **8** widget tiles placed across **2 breakpoints** (visual).
- Catalog lists **≥12** widgets with version badges and a **Version Drawer** showing changelog.
- Releases page displays a **publish summary** with **diff chips** and a **Rollback** (visual).
- Permissions page shows a **role matrix** and **audit log** rows.
- Print styles output **Release Notes** and **Catalog Sheet** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- **Runtime**: Module Federation / Web Components with sandboxing; cross-origin isolation rules.
- **True drag/resize** and **collision-free grid** with persistence.
- **Data bindings**: event bus/contract validation, schema registry, type-safe props.
- **Observability**: RUM, error tracking, widget budgets (CPU/mem), SLO alerts.
- **Delivery**: CI gates, signed artifacts, provenance (SLSA), **canary** releases.
- **Security**: CSP, content sandbox, permission requests, secrets vault.
- **Personalization**: per-user layouts, feature flags, experiments.
- **Multitenancy**: org-level theming, quotas, usage analytics.

---

## 16) Sample Static Data (populate UI)

**Widgets (catalog)**

- `alerts-table@3.2` — Owner: **SRE** — Kind: Web Component — Tags: ops, incidents — **Approved**
- `revenue-trend@2.5` — Owner: **Finance** — Kind: MF — Tags: charts — **Approved**
- `deploy-panel@1.8` — Owner: **DevEx** — Kind: iframe — Tags: ci/cd — **Deprecated**
- `tickets-queue@1.4` — Owner: **Support** — Kind: Web Component — **Approved**
- `feature-flags@0.9` — Owner: **Platform** — Kind: MF — **Draft**

**Page (Ops NOC) tiles**

- Grid 12×8; tiles: `alerts-table` (6×3), `incidents-map` (6×3), `latency-spark` (3×2), `uptime-gauge` (3×2), `oncall-rota` (6×2)

**Release summary**

- Added: `latency-spark@1.1` • Updated: `alerts-table 3.1 → 3.2` • Removed: `deploy-panel@1.8`
- Approvals: Platform ✓ • Security ✓ • Accessibility ✓

**Health (Prod)**

- Healthy **94%**, Degraded **5%**, Down **1%** — Median latency **132 ms** (mock)

---

If you want, I can also turn this into **ready-to-paste page skeletons** (still no JS) or a **README.md** tailored for your Cursor workspace.
