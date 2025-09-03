# Booking & Subscription Management — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for salons, gyms, studios, and co-working spaces to **take bookings, sell plans/passes, and manage recurring payments**. V1 has **no JavaScript**—no real calendars, payments, notifications, or sync. All dynamic behavior is **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- **One system** to schedule services/resources, manage **memberships & packs**, and (visually) handle **billing**.
- Provide clear **availability**, **role-based views** (Owner/Staff/Member), and **policy cues** (cancellations, no-shows).
- Keep it **accessible, responsive, brandable, printable**, and **multi-location** ready.

---

## 2) Constraints (V1)

- **No JS / backend**: booking, billing, and reminders are **static UI**.
- Use semantic HTML (`<form>`, `<details>`, tables) + **pure CSS** for calendars, meters, badges, and timelines.
- “Conflict checks”, “payment status”, “auto-billing”, and “reminders” are **copy-only**.

---

## 3) Personas & Core User Stories

- **Owner/Manager:** “See occupancy & revenue; create plans; set policies.”
- **Front Desk/Staff:** “Book/edit/cancel slots; check in members; take payments (visual).”
- **Member/Customer:** “Find a time, book or join waitlist, manage my plan, download invoices.”
- **Coach/Stylist:** “View my roster; block time; track sessions used.”

**Stories (visual-only)**

1. **Member** books a service/slot → sees **confirmation** & **policy**.
2. **Recurring booking** (e.g., every Tue 6pm, 8 weeks) → added to calendar (static).
3. **Buy plan** (membership) or **class pack** → **auto-renew** toggle (visual).
4. **Front desk** checks in a member and **redeems** a credit/pass.
5. **Owner** views **analytics** (utilization/MRR/churn) and export/print reports.

---

## 4) Information Architecture

- **Dashboard** — KPIs (Occupancy, MRR, Bookings today), alerts
- **Calendar** — Month/Week/Day, Resource/Staff views
- **Bookings** — list/search, create/edit, waitlist
- **Members** — profiles, plans, passes, invoices
- **Plans & Products** — memberships, packs, add-ons, coupons
- **Resources** — rooms/chairs/equipment; capacity and buffers
- **Staff** — schedules, services offered, permissions
- **Billing** — invoices (mock), payouts (copy), taxes/fees notes
- **Analytics** — occupancy, revenue mix, churn, cohort (CSS charts)
- **Settings** — locations, hours, policies, notifications (copy), branding
- **About/Legal** — disclaimers (PCI, privacy), terms

**Global Shell**
Header: brand, location switch, date picker, print link
Sidebar: nav + theme toggle
Main: page content • Footer: help/version/legal

---

## 5) Screen Blueprints

### 5.1 Dashboard

- **KPI Tiles**: Bookings today, Occupancy %, MRR, New members, Failed renewals (mock), No-show rate.
- **Utilization bar** by resource/room.
- **Upcoming** list: next 10 bookings with status (Confirmed/Waitlist/Cancelled).
- **Alerts**: “3 renewals failed”, “Policy missing for Service X”, “Low pack balance warnings” (visual).

### 5.2 Calendar (Core)

- Tabs: **Day / Week / Month** + **Staff** and **Resource** lanes.
- **Slots**: service title, member name, status pill, payment badge (Paid/Due).
- **Drag/resize** handles (visual), **buffer** shading, **conflict** banner (copy).
- **Filters**: service type, staff, room, plan-required.
- **Quick add** button → opens “New Booking” form (same as Bookings).

### 5.3 Bookings

- **List** with filters: date range, status, service, staff, member.
- **New Booking** form:

  - Member (search/select or “Guest”), Service, Staff, Location, Duration, **Recurrence** (visual RRULE summary), **Add-ons**, Notes.
  - **Policy recap** (cancellation window, deposit).
  - **Payment** card (visual): method (card/UPI/cash), amount, tax, discount/coupon.
  - **Confirmation** page with QR/check-in code (placeholder) + calendar links (copy).

- **Actions**: reschedule, cancel (policy note), convert to membership, mark no-show.

### 5.4 Members

- **Profile**: contact chips, consent flags, preferences, photo (placeholder).
- **Plans**: current membership (tier, price, renewal date, **pause/cancel** visual), usage meter (CSS ring).
- **Passes**: e.g., “10-Class Pack—7 remaining” with expiry bar.
- **Invoices**: table with status badges (Paid/Failed/Refunded), print links.
- **Activity**: bookings, check-ins, notes.

### 5.5 Plans & Products

- **Memberships**: tiers (Basic/Plus/Pro), price, billing cycle, included services, booking limits, guest passes.
- **Packs**: 5/10/20 sessions, expiry (e.g., 90 days), transfer rules.
- **Add-ons**: towel service, locker, equipment rental.
- **Coupons**: code, %/₹ off, start/end, usage cap.
- **Taxes/Fees**: GST/VAT toggle (copy), service charges (visual).

### 5.6 Resources

- **Resource list**: rooms/chairs/beds/desks with capacity and buffers.
- **Availability**: operating hours, blackout dates, maintenance notes.
- **Assignment**: which services require which resources (copy matrix).

### 5.7 Staff

- **Roster**: weekly table per staff member; PTO/blocked time rows.
- **Services Offered**: durations, price overrides, commission (copy-only).
- **Targets**: bookings/week, utilization %, satisfaction (visual).

### 5.8 Billing

- **Invoices** (mock): number, member, items, subtotal, tax, total, status.
- **Payouts** (copy): upcoming payout date and summary.
- **Failed Payments** list (visual): retry policy text, update method reminder.

### 5.9 Analytics

- **Tiles**: MRR, Net adds, Churn %, Avg revenue/member, Occupancy %, No-show %.
- **Charts**: revenue by product (stacked bars), occupancy by hour heatmap, churn cohort (table), plan mix pie.
- **Leaderboards**: top services, most utilized resources, busiest staff.

### 5.10 Settings

- **Locations & Hours**: address, time zone, open/close, holidays.
- **Policies**: cancellation window, deposits, grace periods, no-show fee (copy).
- **Notifications** (visual): booking confirm, reminder, renewal, failed payment.
- **Branding**: logo, colors, invoice footer, SMS/email sender (copy).
- **Privacy & Legal**: consent wording, data retention, terms links.

---

## 6) Component Inventory (CSS-only)

- **Calendar Grid** (day/week/month) with **Lane** (staff/resource) headers
- **Slot Card** (status, payment, member)
- **Recurrence Summary** chip (e.g., “Every Tue × 8”)
- **Plan/Pack Card** with **Usage Ring**
- **Invoice Card** & **Status Badge**
- **Payment Badge** (Paid/Due/Failed/Refunded)
- **Occupancy Bars** & **Heatmap**
- **Waitlist Row** with **Position** pill
- **Check-in Keypad** tile (kiosk visual)
- **Policy Banner** & **Alert Chips**
- **Coupon Chip**, **Tax Row**
- **Print Header/Footer** (invoices, rosters, schedules)

---

## 7) Data Model (future-ready; no code)

**Location**

- `id`, `name`, `timezone`, `address`, `hours{}`, `holidays[]`

**Service**

- `id`, `name`, `durationMin`, `price`, `requiresResourceIds[]`, `category`, `bufferBefore/After`

**Resource**

- `id`, `name`, `capacity`, `locationId`, `status` (active|maintenance)

**Staff**

- `id`, `name`, `services[]`, `locations[]`, `workHours{}`, `pto[]`

**Member**

- `id`, `name`, `contact{}`, `consents{}`, `planIds[]`, `passes[]`, `balance`, `notes`

**Plan (Membership)**

- `id`, `name`, `price`, `interval` (month|quarter|year), `includes{limits}`, `autoRenew`, `status`, `start/renewal/cancelAt`, `pause{from,to}`

**Pass (Pack)**

- `id`, `name`, `credits`, `remaining`, `expiresAt`, `shareable`

**Booking**

- `id`, `memberId?`, `serviceId`, `staffId?`, `resourceId?`, `locationId`, `start`, `end`, `status` (confirmed|waitlist|cancelled|completed|no_show), `recurrence?{rule, count|until}`, `paymentStatus` (paid|due|failed|refunded), `notes`

**Invoice**

- `id`, `memberId`, `items[]`, `subtotal`, `tax`, `total`, `currency`, `status`, `dueAt`, `paidAt?`

**Coupon**

- `id`, `code`, `type` (%|fixed), `value`, `validFrom/To`, `maxRedemptions`, `appliesTo{plans|services}`

**ReportMetric**

- `period`, `mrr`, `bookings`, `occupancy`, `churn`, `noshowRate`, `revenueByProduct{}`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.calendar`, `.calendar__lane--staff`, `.slot--confirmed`, `.slot--waitlist`,
  `.badge--paid`, `.badge--failed`, `.ring--usage`, `.bar--occupancy`,
  `.heatmap__cell`, `.invoice__row`, `.policy--warning`, `.chip--recur`,
  `.waitlist__pos`, `.kpi-tile`, `.kiosk__keypad`
- Layers:

  1. `tokens.css` — colors, spacing, typography
  2. `base.css` — reset & form basics
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — calendars, cards, chips, badges, tables, meters
  5. `layouts.css` — shell, two/three-pane, drawers
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — invoices, rosters, schedules

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Primary: #2563EB • Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Calendar accents: Confirmed #10B981 • Waitlist #8B5CF6 • Cancelled #94A3B8

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display 28 • H1 24 • H2 20 • Body 16 • Mono 13 for IDs • Caption 12–13
- **Tabular numerals** for time & money.

**Spacing & Radius**

- Scale: 4/8/12/16/24/32; Radius: 12 (cards), 6 (chips), 8 (slots)
- Focus rings: 3px high-contrast; reduced-motion variant.

Icons: calendar, clock, user, credit-card, receipt, refresh, shield, repeat.

---

## 10) Accessibility, Policies & Compliance

- Landmarks `<header><nav><main><footer>`; one H1/page; keyboard navigable; visible focus.
- Avoid color-only signals—pair **status text** with color chips.
- **Policy copy**: cancellation windows, grace periods, no-show fees, deposit handling.
- **Privacy/Compliance**: PCI note (payments handled by provider), GST/VAT display (copy), consent for SMS/email reminders, data retention policy.

---

## 11) Print Styles

- **Daily Roster**: per staff/resource with times & members; crisp black-on-white.
- **Member Statement**: invoices & plan summary.
- **Schedule**: week view by room; page numbers + footer “Booking & Subscriptions — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Dashboard)
 ├─ calendar.html        (Day/Week/Month + lanes)
 ├─ bookings.html        (List + New/Edit)
 ├─ members.html
 ├─ plans.html           (Memberships & Packs)
 ├─ resources.html
 ├─ staff.html
 ├─ billing.html         (Invoices)
 ├─ analytics.html
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

- **Booking policy:** “Free cancellation up to **6 hours** before start; after that, one credit is deducted.”
- **Recurrence note:** “Repeats **weekly on Tue** until 12 Dec (8 occurrences).”
- **Waitlist helper:** “You’re **#2**—we’ll auto-confirm if a spot opens.” (copy)
- **Membership blurb:** “**Plus** plan: unlimited gym, 4 classes/week, towel service.”
- **Invoice footer:** “Prices inclusive of taxes where applicable. Payments processed by a secure provider.”
- **Failed renewal banner:** “Update payment method to avoid plan interruption.”

---

## 14) Acceptance Criteria (V1)

- Dashboard shows **≥6 KPI tiles**, utilization bars, and alerts.
- Calendar renders **Day/Week/Month** and **Staff/Resource lanes** with **≥12 slots** and status/payment badges.
- Bookings page includes **New Booking** form with **Recurrence** and **Payment** sections and a **Confirmation** mock.
- Members page shows **Plan**, **Pass**, **Usage ring**, **Invoices**, and **Activity**.
- Plans page lists **≥3 memberships**, **≥3 packs**, **coupons**, and **tax rows**.
- Billing lists **≥10 invoices** with status badges and printable invoice view.
- Analytics shows **4+ tiles**, **2 charts**, **1 heatmap**.
- Print styles output **Roster**, **Schedule**, and **Invoices** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real **payment integration** (Stripe/Razorpay), proration, retries, dunning & smart retries.
- **Policy engine** for deposits, cancellation fees, and grace periods.
- **Reminders** (email/SMS/WhatsApp), ICS calendar invites, timezone handling.
- Capacity mgmt: **overlap checks**, waitlist auto-promote, class caps, **multi-resource** bookings.
- **Self-serve portal** + **kiosk check-in** with QR/NFC; attendance tracking.
- POS integration for add-ons; barcode for retail items.
- **Multi-location** inventory and staff pooling; enterprise roles & audit log.
- **Reports** to CSV/Sheets; webhooks; data warehouse sync.

---

## 16) Sample Static Data (populate UI)

**KPI Tiles (today)**

- Bookings **72** • Occupancy **78%** • MRR **₹4.6L** • New members **12** • Failed renewals **7** • No-show **4%**

**Calendar (Day—Staff lanes)**

- **Arjun** — Haircut (30m) **Paid** — 10:00; Color (60m) **Due** — 11:00
- **Neha** — PT Session (60m) **Paid** — 09:00; 1:1 Coaching **Paid** — 12:30
- **Kabir** — Yoga Class (60m, cap 12/15) — 18:00 (Waitlist 2)

**Plans**

- **Gym Basic** — ₹1,499/mo — Unlimited gym — **Renews 05 Oct**
- **Class Pack 10** — ₹3,999 — **7 remaining** — Expires **12 Dec**

**Invoices**

- INV-2025-0912 — **Paid** — ₹1,499 — 05 Sep
- INV-2025-0887 — **Failed** — ₹3,999 — 01 Sep (retry in 3 days)

**Policies**

- Cancellation: **6h**; No-show: **deduct 1 credit**; Buffers: **10m** before/after color service.

---

If you’d like, I can also turn this into **ready-to-paste page skeletons** (still no JS) or a **README.md** for your Cursor workspace.
