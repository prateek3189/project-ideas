# Event Buddy — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for discovering, joining, and organizing **local events** with **ticketing** and **RSVP** features. V1 is **JavaScript-free**—all payments, QR scanning, maps, emails, and analytics are **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Make it easy to **find events**, **RSVP/buy tickets**, and **host events**.
- Provide clear **ticket tiers**, **capacity/waitlist** visuals, and **mobile-first** flows.
- Keep the UI **accessible, responsive, printable**, and organizer-friendly.

---

## 2) Constraints (V1)

- **No JavaScript.** No real payments, auth, seat selection logic, or QR scanning.
- Use semantic HTML (`<form>`, `<details>`, tables, lists) and **pure CSS** only.
- All dynamic states (sold out, countdown, fees) are **copy/UI placeholders**.

---

## 3) Personas & Core User Stories

- **Seeker:** “Browse nearby events and RSVP quickly.”
- **Friend Group:** “Grab a few tickets and share the plan.”
- **Organizer:** “Publish an event, track RSVPs/sales, check in guests at the door.”
- **Venue Owner:** “List recurring nights and cap capacity.”

**Stories (visual-only in V1)**

1. Discover events with filters (date, price, category, location).
2. Open **Event Detail** → choose **RSVP** or **Ticket Tier(s)** → mock checkout.
3. Save to calendar / share (links visual only).
4. Organizer creates/edits an event with **capacity & tier** setup.
5. Organizer sees **Dashboard**: RSVPs, sales (mock), and a **Check-in** page with QR placeholders.
6. Print **Tickets** and an **Event Poster**.

---

## 4) Information Architecture

- **Home / Discover** — feed + filters
- **Event Detail** — about, venue box, tiers, host info
- **RSVP / Checkout** — forms, cart summary (visual), order confirmation
- **Organizer Console** — dashboard, events list, create/edit
- **Orders & Check-in** — attendee list, QR placeholders, manual check-in (visual)
- **Calendar** — month/week (static grid)
- **Profile** — your RSVPs/tickets, saved events, organizer profile
- **Messages** — attendee/organizer thread (non-functional)
- **Settings** — notifications, theme, privacy (visual)
- **About** — policies, safety, refunds (copy)

**Global Shell**
Header: logo/name, search (decorative), city selector (visual), profile
Sidebar (desktop): nav + theme toggle (visual)
Main: page content • Footer: help/version/legal

---

## 5) Screen Blueprints

### 5.1 Home / Discover

- **Filter Bar**: Date (Today/Weekend/Custom), Category (Music, Tech, Sports, Family, Arts, Food), Price (Free/₹/₹₹), Distance chips, Venue type.
- **Event Cards**: cover image placeholder, title, **date pill**, time, venue, distance, **price chip**, tags (Family-friendly, Outdoor, Virtual).
- **Featured Carousel** (static stack) and **Nearby Map** box (placeholder grid with pin icon).

### 5.2 Event Detail (Core)

- Hero: cover placeholder + **Date & Time**, **Venue box** (address + mini map placeholder).
- **About** (markdown-like copy), **Schedule**, **Line-up/Speakers**.
- **Ticketing/RSVP Panel**:

  - **Ticket Tiers Table**: name, price, fee note, availability bar (In stock / Low / Sold out), quantity selector (visual).
  - **RSVP (Free)**: Going / Interested chips, capacity meter.
  - **Cart Summary** (side card): subtotal, fees, total (copy-only), “Continue”.

- **Host**: organizer card with rating badges (visual).
- **Policies**: refund, entry, age; `<details>` for more.
- **Share** buttons (visual), **Add to Calendar** (ics icon placeholder).

### 5.3 RSVP / Checkout

- **Buyer Form**: name, email, phone (labels + required markers).
- **Attendee Details** per ticket (name/email) — table style.
- **Payment Options** (visual): UPI • Cards • PayPal; fees note.
- **Order Review**: items, quantities, fee line (copy), total.
- **Confirm** → **Order Confirmation** page with **Ticket List** + QR placeholders + “Download/Print”.

### 5.4 Organizer Console

- **Dashboard Tiles**: Upcoming Events • RSVPs Today • Tickets Sold (mock) • Revenue (—).
- **Events Table**: title, date, status (Draft/Published/Sold Out), RSVPs, Tickets.
- **Create/Edit Event** (multi-section form):

  - Basics: title, category, description, cover upload (placeholder)
  - Date & Time: start/end, timezone
  - Venue: name, address, embed map placeholder
  - Capacity: overall cap, per-tier caps, waitlist toggle (visual)
  - Tickets: add rows (name, qty, price, sales window), promo code section (visual)
  - Settings: visibility (Public/Unlisted), age limit, refund policy
  - Publish bar (visual): Save Draft • Preview • Publish

- **Promote**: share links, poster generator (print style), promo codes list (visual).

### 5.5 Orders & Check-in

- **Orders Table**: order #, buyer, tickets, status (Paid/RSVP/Cancelled), timestamp.
- **Attendee List**: ticket #, name, tier, **Check-in toggle** (visual), note.
- **QR Check-in**: big QR placeholder, “Scan to view ticket” (copy); **Manual code input** field (visual).
- **Export** (CSV placeholder) and **Badge Printer** (print style).

### 5.6 Calendar

- Month grid with event dots; list for selected day beneath.

### 5.7 Profile

- **Tabs**: Tickets & RSVPs • Saved • Organizer
- Ticket cards with **QR placeholder**, event title, date, venue, “Add to Wallet” (visual).

### 5.8 Settings / About

- Notifications (email/push placeholders), Theme (light/dark/high-contrast), Privacy (public name vs initials).
- About: community guidelines, anti-scalping note, refund timelines (copy).

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Event Card**, **Date Pill**, **Price Chip**, **Tag Chip**
- **Tier Row** (name, qty selector visual, price, availability bar)
- **Cart Summary** / **Order Review** / **Confirmation Ticket**
- **Capacity Meter** / **Waitlist Badge**
- **Organizer Card** / **Venue Box** / **Map Box** (static)
- **QR Placeholder** (square with finder corners)
- **Countdown** (visual bar), **Calendar Grid**
- **Stat Tile**, **Alert/Nudge Banner** (e.g., “Limited seats left”)
- **Print Header/Footer** for tickets & posters

---

## 7) Data Model (future-ready; no code)

**Event**

- `id`, `title`, `category`, `about`, `coverUrl`, `startAt`, `endAt`, `timezone`, `venueId`, `organizerId`, `visibility` (public|unlisted), `policies`

**Venue**

- `id`, `name`, `address`, `city`, `geo`, `capacity`, `notes`

**TicketTier**

- `id`, `eventId`, `name`, `price`, `fee`, `currency`, `quantity`, `salesStart`, `salesEnd`, `status` (onSale|soldOut|hidden)

**RSVP**

- `id`, `eventId`, `userId`, `status` (going|interested|waitlist), `createdAt`

**Order**

- `id`, `eventId`, `buyer`, `items[]` (`{tierId, qty}`), `amount`, `currency`, `status` (paid|cancelled|pending), `createdAt`

**Ticket**

- `id`, `orderId`, `tierId`, `attendee`, `qrCode` (text), `checkIn` (bool, time)

**PromoCode**

- `id`, `eventId`, `code`, `discountType`, `value`, `limit`, `used`

**Organizer**

- `id`, `name`, `bio`, `links[]`, `badges[]`

**User**

- `id`, `name`, `email`, `phone`, `savedEventIds[]`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.event-card__meta`, `.price-chip--free`, `.tier-row__qty`, `.availability__bar--low`,
  `.cart__total`, `.qr--placeholder`, `.capacity__meter`, `.organizer-card__badge`,
  `.calendar__day--has-events`, `.alert--limited`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements, forms & tables
  3. `utilities.css` — flex/grid/gap/visually-hidden
  4. `components.css` — cards, chips, tiers, banners, meters, qr
  5. `layouts.css` — shell, grids, two-column detail pages
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — tickets & posters

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Accent: #2563EB • Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Availability: neutral → low → sold classes for bars/badges

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB (AA)

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- **Tabular numerals** for prices and order numbers.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)

**Imagery/Icons**

- Line icons for calendar, pin, ticket, RSVP, QR, wallet.

---

## 10) Accessibility & Safety

- Proper landmarks (`<header> <nav> <main> <footer>`), one **H1** per page.
- Labels tied to inputs; required indicators; clear error helper text (copy).
- High-contrast focus rings; keyboard navigable.
- Do **not** use color alone—pair availability with text (“Sold out”).
- Refund & venue safety guidance surfaces near purchase (copy).

---

## 11) Print Styles

- **Tickets**: event, date/time, venue, **QR placeholder**, tier, seat (if any), order ID.
- **Event Poster/Flyer**: hero, titles, date/time, venue, QR placeholder for link.
- **Attendee List**: table with alphabetized names and check-in column.
- Black on white; hide nav; page numbers; footer “Event Buddy v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html            (Home / Discover)
 ├─ event.html            (Event Detail)
 ├─ rsvp.html             (RSVP / Checkout)
 ├─ confirm.html          (Order Confirmation / Tickets)
 ├─ organizer.html        (Organizer Console)
 ├─ orders.html           (Orders & Check-in)
 ├─ calendar.html
 ├─ profile.html
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
     ├─ illustrations/
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Discover nudge:** “Weekend filling up fast—12 events near you.”
- **Tier note:** “Service fees and taxes shown at checkout (placeholder).”
- **RSVP helper:** “Free entry. Capacity limited—arrive early.”
- **Waitlist banner:** “Main tier sold out. Join the waitlist to be notified.”
- **Refund policy:** “Full refund up to 24h before start (organizer policy).”
- **Check-in tip:** “Have your QR ready. Manual code available if needed.”

---

## 14) Acceptance Criteria (V1)

- Discover lists **≥12 events** with functional filters (visual only).
- Event Detail shows **tiers table**, **capacity meter**, host & venue sections.
- RSVP/Checkout pages collect buyer + attendee info and show a **cart summary**.
- Confirmation page displays **tickets with QR placeholders** and a print link.
- Organizer Console lets you **create/edit** events with **tiers & caps** (visual) and a dashboard of **tiles + tables**.
- Orders & Check-in lists attendees with a **check-in toggle** and **manual code** field (visual).
- Print styles output **tickets**, **poster**, and **attendee list** cleanly.
- Baseline a11y (labels, contrast, focus) passes.

---

## 15) Future Enhancements

- Real auth, payments (UPI/Cards/PayPal), refunds & payouts.
- Seat maps & assigned seating; dynamic inventory & queues.
- ICS generation, Google/Apple Wallet passes; calendar sync.
- QR generation & scanning; anti-fraud checks; offline mode for door staff.
- Organizer analytics (revenue, conversion) and email campaigns.
- Map search with geofencing; real-time capacity updates; push notifications.
- Community moderation, report flow, and verified organizers.

---

## 16) Sample Static Data (populate UI)

**Events (Discover)**

- Indie Night @ Blue Door — Fri 8:00 PM — ₹399 — Music
- Dev Meetup: Web Performance — Sat 10:30 AM — Free — Tech
- Sunrise Yoga in the Park — Sun 6:30 AM — ₹199 — Wellness
- Kids Science Hour — Sat 4:00 PM — Free — Family

**Event Tiers (Detail)**

- Early Bird — ₹299 — Qty 50 — **Low stock**
- General — ₹399 — Qty 120 — **In stock**
- VIP — ₹899 — Qty 20 — **Sold out**

**Organizer Dashboard (tiles)**

- Upcoming Events: **4** • RSVPs Today: **32** • Tickets Sold: **118** • Revenue: **—** (placeholder)

**Attendee List (check-in)**

- TKT-0001 — A. Kumar — General — **Not Checked In**
- TKT-0002 — N. Shah — Early Bird — **Checked In**
- TKT-0003 — P. Rao — VIP — **Not Checked In**

---

If you want, I can turn this into **ready-to-paste page skeletons** (still no JS) or a **README.md** to drop straight into Cursor.
