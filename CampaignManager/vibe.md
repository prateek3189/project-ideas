# Campaign Manager — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** to **create, schedule, and track** SMS / email marketing campaigns. V1 is **JavaScript-free**—no real sending, lists, analytics, or integrations. All dynamic behavior is **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Ship an **end-to-end flow**: **Brief → Audience → Content → Schedule → Review → Track**.
- Support **Email & SMS** with **templates**, **A/B testing**, **UTM builder**, and **drip/journey** (visual).
- Provide **clear compliance cues** (opt-in, unsubscribe, sender ID) and **deliverability hints** (copy only).
- Keep UI **accessible, responsive, and printable** for briefs & reports.

---

## 2) Constraints (V1)

- **No JavaScript**: no SMTP/SMS gateway, no contact upload, no analytics ingestion.
- Use semantic HTML (`<form>`, `<details>`, tables) and **pure CSS** (progress bars, badges, KPIs).
- Placeholders for: integrations (SMTP/APIs), domain auth (SPF/DKIM), link tracking, DLT/10DLC notes.

---

## 3) Personas & Core User Stories

- **Marketer:** “Launch a product update email + SMS reminder tomorrow.”
- **Growth PM:** “Run A/B subject test; pick winner by open rate in 4h.”
- **Lifecycle Lead:** “Create a 5-step onboarding drip with delays and exit rules.”
- **Compliance Owner:** “Ensure consent & easy opt-out; review content.”

**Stories (visual-only)**

1. Create **Campaign Brief** → choose **Email/SMS** → add **Audience Segment** → compose content.
2. Configure **Schedule** (time zone, throttling) → **Review** checklist → **Start** (visual).
3. Track **Sends/Opens/Clicks/Replies/Bounces** (mock) with **UTM** summary.
4. Create **A/B test** (subject/CTA) with **auto-winner** rule (visual).
5. Build **Drip/Journey** (visual canvas): triggers, delays, branches.

---

## 4) Information Architecture

- **Dashboard** — KPIs, recent campaigns, alerts
- **Campaigns** — list (status), create/edit wizard
- **Templates** — email blocks, SMS snippets
- **Audiences** — segments, imports (visual), suppression lists
- **A/B Tests** — config & results
- **Journeys** — drip builder (visual nodes)
- **Reports** — performance, link map, deliverability (copy)
- **Assets** — images, brand colors, logos (placeholders)
- **Settings** — channels, providers, tracking, compliance
- **About** — methodology, legal disclaimers

**Global Shell**
Header: app name, workspace switch, create button, print link
Sidebar: nav + theme toggle (visual)
Main: page content • Footer: help/version

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **KPI Tiles**: Sends, Deliverability %, Open %, Click %, Unsubscribe %, SMS Reply %.
- **Recent Campaigns** table: name • channel • status (Scheduled/Sending/Completed/Draft) • sent • open • click.
- **Alerts**: Domain not authenticated, High bounce rate, Missing unsubscribe (visual).

### 5.2 Campaign Wizard (Core)

**Steps tabs**: 1) Brief 2) Audience 3) Content 4) Schedule 5) Review

1. **Brief**

   - Fields: name, objective, channel (Email/SMS/Both), tags, owner, budget note (copy).
   - `<details>`: success metric definition (open/click/reply/conversion placeholder).

2. **Audience**

   - Segment selector (chips): All subscribers • New signups < 30d • Lapsed 90d • High value.
   - Filters (visual): country, device, last seen, purchase count.
   - **Suppression lists** chip: unsubscribed, bounced, do-not-contact.
   - Size estimate bar (mock).

3. **Content**

   - **Email**: subject, preheader, from name/email, **builder** (sections: hero, text, button, product grid), footer with address/unsubscribe note.
   - **SMS**: sender ID (visual), message text, personalization tokens (e.g., `{{first_name}}`), length counter (copy), link shortening toggle (visual).
   - **UTM Builder**: source/medium/campaign/content (preview URL).
   - **Spam/Policy checks** (copy): image-to-text balance, forbidden words list (visual).

4. **A/B (optional)**

   - Variant controls: **Email** (Subject A/B, Content A/B) • **SMS** (Message A/B).
   - Split slider (e.g., 10% A, 10% B, 80% after winner).
   - **Winner rule** (visual): highest open/click/reply after **X hours**.

5. **Schedule**

   - Send now / Schedule later (date/time/timezone).
   - **Smart send** (visual): local morning windows, throttle per minute.
   - **Compliance gates** (copy): quiet hours, consent check, mandatory footer.

6. **Review**

   - Checklist with badges: From domain authenticated • Unsubscribe present • Segment size • A/B enabled • Links tagged.
   - **Approval** row (visual): “Marketing”, “Compliance”.
   - **Start Campaign** button (visual).

### 5.3 Reports

- **Overview Tiles**: Delivery %, Open %, Click %, Unsub %, Bounce %, SMS Reply %.
- **Trend chart** (CSS bars) by hour/day.
- **Link map**: list of URLs with click share bars; **top devices/clients** table (copy).
- **Audience breakdown**: segments, geos (chips).
- **A/B Results** table: Variant • sample size • metric • winner badge.
- **Export** (CSV/PNG placeholder) & **Print Report** link.

### 5.4 Journeys (Drip Builder)

- **Canvas** (static): **Trigger** → Delay 1d → Email 1 → If no open 48h → SMS nudge → End.
- Node cards with config `<details>` (subject, message, delay).
- **Entry/Exit rules** (visual): exit if purchase, suppression after unsubscribe.

### 5.5 Audiences

- **Segments** table & “Create Segment” form (visual filters + preview count).
- **Suppression** page: unsubscribed/bounced imports (placeholder).
- **Consent log** note (copy).

### 5.6 Templates & Assets

- Email layout cards; SMS message snippets; brand kit (colors/logos).
- **Content guidelines** banner: accessibility, image alt text, SMS length & unicode.

### 5.7 Settings

- **Channels**: Email (From domain, DKIM/SPF status visual), SMS (sender ID/alpha/long code, region rules note).
- **Providers**: SMTP/API placeholders (e.g., “Connect Provider” buttons).
- **Tracking**: link tracking on/off, custom domain (visual), UTM defaults.
- **Compliance**: default footer, unsubscribe keyword list, quiet hours, DLT/10DLC notes (copy).
- **Team & Roles**: approvers (visual).

---

## 6) Component Inventory (CSS-only)

- **KPI Tile**, **Status Badge**, **Progress Bar**
- **Step Tabs** & **Checklist Item**
- **Segment Chip**, **Filter Row**, **Suppression Chip**
- **Email Builder Block**, **SMS Composer**, **Length Counter (copy)**
- **UTM Preview**, **Link Table**
- **A/B Split Slider (visual)**, **Winner Badge**
- **Schedule Card**, **Timezone Chip**, **Throttle Meter**
- **Report Bars**, **Link Share Bars**, **A/B Results Table**
- **Journey Node Card**, **Connector Line (static)**
- **Alert/Nudge Banner** (e.g., “Add physical mailing address”)
- **Print Header/Footer** (brief & report)

---

## 7) Data Model (future-ready; no code)

**Campaign**

- `id`, `name`, `channel` (email|sms|both), `objective`, `segmentId`, `status` (draft|scheduled|sending|completed|paused), `scheduleAt`, `timezone`, `tags[]`

**MessageVariant**

- `id`, `campaignId`, `type` (email|sms), `variant` (A|B),
  `email` (`{subject, preheader, fromName, fromEmail, html, text}`),
  `sms` (`{senderId, body, shortenLinks:bool}`),
  `utm` (`{source, medium, campaign, content}`), `splitPercent`

**Segment**

- `id`, `name`, `rules[]`, `estimatedSize`, `suppressionIds[]`

**Contact**

- `id`, `consent` (email|sms), `attrs{}`, `status` (active|unsub|bounced)

**Event**

- `id`, `campaignId`, `contactId`, `type` (sent|delivered|open|click|reply|bounce|unsubscribe), `timestamp`, `meta{url, device}`

**Journey**

- `id`, `name`, `nodes[]` (`{type: trigger|email|sms|delay|branch|exit, config{}}`), `status`

**Settings**

- `providers{email,sms}`, `tracking{utmDefaults,domain}`, `compliance{footer, quietHours, regionNotes}`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.kpi-tile`, `.badge--scheduled`, `.wizard__step`, `.checklist__item--ok`,
  `.segment__chip--suppressed`, `.builder__block--hero`, `.sms__counter`,
  `.ab__slider`, `.schedule__card`, `.report__bar--clicks`, `.journey__node--delay`,
  `.alert--compliance`
- Layers:

  1. `tokens.css` — colors, spacing, typography
  2. `base.css` — reset & fundamentals
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — tiles, chips, tables, blocks, meters, badges
  5. `layouts.css` — shell, wizard, reports, canvas
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — brief & performance report

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Primary: #2563EB • Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Channel accents: **Email** #8B5CF6 • **SMS** #10B981

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display 28 • H1 24 • H2 20 • Body 16 • Caption 12–13
- **Tabular numerals** for rates & counts.

**Spacing & Radius**

- 4/8/12/16/24/32; Radius: 12 (cards), 6 (chips), 999 (pills).
- Focus rings: 3px, high-contrast; reduced-motion theme.

Icons: paper plane, inbox, mobile, link, clock, test tube, shield.

---

## 10) Accessibility & Compliance Cues

- Landmarks `<header><nav><main><footer>`; one **H1** per page.
- Labels connected to inputs; keyboard navigable; visible focus.
- **Compliance reminders (copy)**: consent required, physical mailing address in email footer, **unsubscribe** link/keyword, quiet hours for SMS, sender ID/long code rules vary by region.
- **Alt text** fields for images; color contrast AA.

---

## 11) Print Styles

- **Campaign Brief**: objective, audience, content summary, schedule, compliance checklist.
- **Performance Report**: KPIs, trend bars, A/B table, link map, notes.
- Hide nav; black on white; footer: “Campaign Manager — v0.1” + page numbers.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Dashboard)
 ├─ campaigns.html       (List)
 ├─ campaign-new.html    (Wizard)
 ├─ reports.html
 ├─ journeys.html
 ├─ audiences.html
 ├─ templates.html
 ├─ assets.html
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

- **Wizard helper:** “Make sure your email includes a **physical address** and **unsubscribe** link.”
- **Spam tip:** “Keep a healthy text-to-image ratio and avoid all-caps subjects.”
- **SMS helper:** “Shorten links and include an **opt-out keyword** (e.g., ‘Reply STOP’).”
- **A/B tip:** “Test **one variable** at a time; pick winner within **4–24h**.”
- **Deliverability note:** “Authenticate domain (SPF/DKIM/DMARC) to improve inbox placement (visual only).”
- **Report nudge:** “Clicks concentrated on top CTA—consider single-focus layouts.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **6 KPI tiles**, **recent campaigns**, and **alerts**.
- Campaign wizard renders **5 steps** with **A/B** and **Schedule** options and a **Review checklist**.
- Reports page shows **overview tiles**, **trend bars**, **link table**, and **A/B results**.
- Journeys page displays a **static canvas** with at least **5 nodes** and editable `<details>`.
- Audiences page shows **segments**, **filters**, and **suppression** chips.
- Templates page lists **≥6 email blocks** and **≥6 SMS snippets** (placeholders).
- Print styles output **Brief** and **Performance Report** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real **SMTP/SMS** integrations, rate limits, retries, webhook ingestion.
- Domain auth checks (SPF/DKIM/DMARC) & **pre-flight** tests (seed inboxes).
- **Link tracking** & conversion webhooks; post-purchase events.
- **Send-time optimization**, time-zone per contact, quiet hours enforcement.
- **WYSIWYG email builder**, MJML/HTML export, inbox rendering tests.
- **Journey** execution engine with goals, exits, audience joins.
- **Predictive** send & subject scoring; LLM copy assist; image generation (brand safe).
- Multi-workspace roles & approvals; versioning & audit logs; GDPR tooling.

---

## 16) Sample Static Data (populate UI)

**Recent Campaigns (table)**

- “Spring Sale Teaser” — Email — **Completed** — Sent **45,120**, Open **38%**, Click **8.4%**, Unsub **0.21%**
- “Cart Nudge Day-2” — SMS — **Scheduled** — Est **12,340** — Reply **—**
- “Onboarding Step 1” — Email — **Active** — Sent **3,200/day**, Open **42%**, Click **6.7%**

**A/B Results (email)**

- **Subject A** “Don’t miss 20% off” — Open **35.2%** (Winner) — Click **7.9%**
- **Subject B** “A small thank-you: 20% inside” — Open **31.4%** — Click **8.1%**

**Report KPIs (mock)**

- Delivered **97.6%** • Open **36.9%** • Click **7.4%** • Unsub **0.19%** • Bounce **2.1%** • SMS Reply **4.2%**

**Top Links (click share)**

- `/sale` **46%** • `/new` **28%** • `/faq` **12%** • Others **14%**

**Journey (visual)**

- **Trigger**: New signup → **Delay 1d** → **Email: Welcome** → **Delay 2d** → **Email: Value prop** → **Branch** (if no open) → **SMS: Reminder** → **Exit**

---

If you want, I can turn this into **ready-to-paste page skeletons** (still no JS) or a **README.md** tailored for your Cursor workspace.
