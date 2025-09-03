# Hyperlocal Community App — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a neighborhood app that connects nearby people for **events**, **item exchanges** (give/borrow/sell), and **carpooling**. V1 is **JavaScript-free**—all maps, chat, payments, and verification are **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Help neighbors **meet, share, and ride together** safely and easily.
- Keep interactions **hyperlocal** (within a few km) and **family-friendly**.
- Provide clear **trust signals** (badges, references) and **safety tips** (copy-only).
- Ship an **accessible, responsive, print-friendly** scaffold ready for real data.

---

## 2) Constraints (V1)

- **No JavaScript**: maps, live chat, realtime location, payments, OTP, and notifications are **non-functional**.
- Use semantic HTML and CSS only (`<details>`, forms, tables, cards).
- Photos/IDs/ratings and moderation are **placeholders**.

---

## 3) Personas & Core User Stories

- **Organizer:** “Host weekend events (meetups, cleanups, markets).”
- **Sharer:** “Lend/borrow small items; giveaway unused stuff.”
- **Commuter/Parent:** “Find/offer carpool seats for school/office.”
- **New Resident:** “Discover local groups and trusted neighbors.”

**Stories (visual-only)**

1. Join a **Neighborhood** and view **Events**, **Items**, and **Rides** feeds.
2. Create an **Event** with time/place and RSVP placeholders.
3. Post an **Item** to give/borrow/sell with condition and pickup notes.
4. Offer/Request a **Ride** with time, route, seats (safety badges visual).
5. Use **Direct Message** (non-functional) to coordinate.
6. See **Trust & Safety** badges and **Moderation** indicators (visual).
7. Print a **Bulletin** of upcoming events and featured posts.

---

## 4) Information Architecture

- **Home / Feed** — mixed stream (events/items/rides) with filters
- **Events** — list + event detail (RSVP placeholders)
- **Items** — exchange marketplace (give/borrow/sell)
- **Carpool** — offer/request rides
- **Groups** — interest groups (parents, runners, pets, society blocks)
- **Messages** — mock conversations (visual)
- **Profile & Trust** — badges, references, verification (visual)
- **Moderation** — community rules, report flow (visual)
- **Settings** — neighborhood, radius, notifications, privacy (visual)
- **About** — safety tips, guidelines, disclaimers

**Global Shell**
Header: app name, neighborhood switcher (visual), search, print
Sidebar: navigation + theme toggle (visual)
Main: page content
Footer: help/version

---

## 5) Screen Blueprints

### 5.1 Home / Feed

- **Filter Pills**: All • Events • Items • Rides • Groups
- **Sort**: New • Near • Popular (visual)
- **Cards** (mixed): event/item/ride with distance chip, time, tags, mini trust badge

### 5.2 Events

- **Event Cards**: title, date/time, venue (map pin placeholder), host chip
- Tags: Family • Kids • Fitness • Learning • Social
- **Event Detail**:

  - Hero image placeholder
  - When/Where + simple map box (static)
  - About (markdown-like text)
  - **RSVP** chips: Going/Interested (visual only)
  - Host profile box + community rules link

### 5.3 Items (Give / Borrow / Sell)

- **Filter Bar**: Giveaways • Borrow • For Sale; Category (Tools, Kids, Sports, Electronics, Home)
- **Item Card**: photo placeholder, title, status (Give/Borrow/Sell), condition (New/Good/Used), distance
- **Item Detail**:

  - Gallery placeholder, description, condition, pickup window
  - **Exchange Type**:

    - **Giveaway**: “Free—first come, first serve” (copy)
    - **Borrow**: duration chip + deposit note (visual)
    - **Sell**: price chip (currency visual only); “Payment link” placeholder

  - Poster profile + trust badges
  - **Message** button (non-functional)

### 5.4 Carpool

- Tabs: **Offer Ride** • **Request Ride**
- **Ride Card**: origin → destination, time, seats, cost-share note, rules (mask, no pets…)
- **Ride Detail**:

  - Route box (map placeholder), driver/passenger badges (visual KYC)
  - Pickup point chips, ETA note, safety tips panel
  - **Join / Offer seat** button (visual)

- **Carpool Safety** block: share trip with family (copy), meet in public place, ID check (visual badge)

### 5.5 Groups

- **Group Cards**: name, member count, purpose, meet cadence
- **Group Page**:

  - About + rules
  - Posts list (events/items/rides tagged to group)
  - Join/Leave (visual), Admin chips

### 5.6 Messages (Mock)

- **Thread List**: avatar initials, last line preview, timestamp
- **Thread View**: bubble layout with date separators, attachment pill (visual)
- Composer bar: text box, photo icon, send icon (non-functional)

### 5.7 Profile & Trust

- Profile header: name, unit/block, join date, “verified” badge (visual), references count
- Tabs: **About** • **Listings** • **References** • **Badges**
- Badges (visual): Phone Verified • Residence Verified • Community Helper • Safe Driver
- **References**: short quotes (static text)

### 5.8 Moderation

- **Rules** page with community guidelines
- **Report** form (visual): reason chips, details textarea
- **Status** (visual): received • under review • actioned
- “Three-strike policy” copy

### 5.9 Settings

- Neighborhood selector (visual) • Radius (1–5 km)
- Notifications (email/push placeholders)
- Privacy: show only to neighbors, hide unit number (visual)
- Language/theme/accessibility toggles

### 5.10 About

- Safety guidance, inclusivity pledge, non-commercial policy notes
- Disclaimers: platform is connector, not a party to transactions

---

## 6) Component Inventory (CSS-only)

- **Header / Sidebar / Footer**
- **Feed Card** types: event/item/ride/group
- **Filter & Tag Pills**, **Distance Chip**, **Time Chip**
- **Map Box** placeholder (static grid with pin icon)
- **Profile Chip** with badges
- **RSVP Chips**, **Seat Counter** (visual), **Price/Deposit** chips
- **Message Button**, **Report Button**
- **Badge** (verified/helper/driver), **Reference Quote**
- **Nudge/Alert Banner** (e.g., “Meet in public places”)
- **Print Header/Footer** for bulletin

---

## 7) Data Model (future-ready; no code)

**Neighborhood**

- `id`, `name`, `city`, `radiusKm`, `rulesUrl`

**User**

- `id`, `name`, `unit`, `joinedAt`, `badges[]`, `references[]`, `visibility` (neighbors|groups|private)

**Event**

- `id`, `title`, `datetime`, `venue`, `geo` (lat/lng), `about`, `tags[]`, `hostId`, `rsvpCounts` (going|interested)

**Item**

- `id`, `title`, `type` (give|borrow|sell), `category`, `condition`, `price`, `deposit`, `description`, `pickupWindow`, `images[]`, `posterId`, `status`

**Ride**

- `id`, `kind` (offer|request), `from`, `to`, `via`, `datetime`, `seats`, `costShareNote`, `rules[]`, `driverOrRequesterId`, `safetyBadges[]`

**Group**

- `id`, `name`, `about`, `membersCount`, `tags[]`, `adminIds[]`

**Message (placeholder)**

- `threadId`, `fromId`, `toId`, `text`, `sentAt`

**Report**

- `id`, `targetType` (event|item|ride|user), `targetId`, `reason`, `details`, `status`

**Settings**

- `neighborhoodId`, `radiusKm`, `language`, `theme`, `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.feed-card--event`, `.feed-card__meta`, `.chip--distance`, `.map-box`,
  `.profile-chip__badge--verified`, `.rsvp__chip--going`, `.price-chip`,
  `.ride-card__route`, `.alert--safety`, `.badge--helper`
- Layers:

  1. `tokens.css` — colors, spacing, radii, typography
  2. `base.css` — reset, base elements, headings
  3. `utilities.css` — grid/flex/gaps/visually-hidden
  4. `components.css` — cards, chips, lists, map box, badges, banners
  5. `layouts.css` — shell, feed grids, detail pages
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — bulletin & flyers

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC
- Surface: #FFFFFF
- Text: #0F172A
- Accent: #2563EB (actions)
- Trust: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display: 28 • H1: 24 • H2: 20 • Body: 16 • Caption: 12–13
- Use **tabular numerals** class for times/distances.

**Spacing & Radius**

- Scale: 4, 8, 12, 16, 24, 32
- Radius: 12 (cards), 999 (chips)
- Soft shadows; strong focus outlines for a11y.

**Imagery**

- Simple line icons for map pin, car, calendar, box, handshake.

---

## 10) Accessibility & Safety

- Landmarks: `<header> <nav> <main> <footer>`; one H1/page.
- Labels tied to controls; keyboard navigable; visible focus rings.
- Never rely on color alone—pair badges with text/icons.
- **Safety copy** on all transaction pages (meet in public, verify identity, cashless preferred).
- Privacy: hide exact address by default (visual control).

---

## 11) Print Styles

- **Community Bulletin**: upcoming events, featured items, open rides (A4/Letter).
- **Event Flyer**: title, time, venue, QR placeholder.
- Black on white; hide nav; page numbers; footer note: “Hyperlocal Community — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Feed)
 ├─ events.html
 ├─ items.html
 ├─ item-detail.html
 ├─ carpool.html
 ├─ groups.html
 ├─ messages.html
 ├─ profile.html
 ├─ moderation.html
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

- **Safety banner:** “Meet in public places. Share only what you’re comfortable sharing.”
- **Trust tip:** “Complete **Phone** and **Residence** checks to earn a Verified badge (visual).”
- **Event helper:** “Add a clear meetup point and backup contact.”
- **Item helper:** “For Borrow, specify a return date and condition expectations.”
- **Carpool helper:** “Post pickup time window and seat count. Share ride details with family.”
- **Moderation note:** “Be kind. Sales promos and spam are not allowed.”

---

## 14) Acceptance Criteria (V1)

- Home shows **filterable feed** with mixed cards and distance/time chips.
- Events lists **≥9** cards; Event Detail shows RSVP chips and map box placeholder.
- Items lists **≥12** cards across **Give/Borrow/Sell**; Item Detail shows exchange type, price/deposit chips.
- Carpool lists **≥8** rides (offers/requests) with route boxes and safety badges.
- Groups shows **≥6** group cards; group page lists posts.
- Profile shows badges, references, and listings tabs.
- Messages renders thread list and a mock conversation.
- Print stylesheet outputs **Bulletin** and **Flyer** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real **map & geofencing**, address obfuscation, and distance ranking.
- **Chat & notifications**; opt-in phone/email verification (KYC options per region).
- **Payments** for item sales/deposits (UPI/PayTM/Stripe/PayPal)—with dispute policy.
- Event **check-ins/QR**, capacity & waitlist, recurring events.
- Carpool **route match**, live ETA sharing, ratings, SOS flow.
- AI moderation: flag spam/scams; image blurs; auto-tagging.
- Multilingual UI; accessibility audits; PWA/offline mode.

---

## 16) Sample Static Data (populate UI)

**Events**

- Park Clean-up — Sat 7:30 AM — Community Park — Tags: Social • Kids • Service
- Weekend Farmers’ Market — Sun 9:00 AM — Lot B — Tags: Food • Local

**Items**

- **Give**: Children’s storybooks (Good) — Pickup: Gate 2
- **Borrow**: Drill Machine (2 days, refundable deposit ₹500)
- **Sell**: Office Chair (₹1,800) — Condition: Used

**Rides**

- **Offer**: Maple Apts → Tech Park — 8:30 AM — 2 seats — Share fuel
- **Request**: School drop (Sunshine High) — 7:45 AM — 1 seat — Child seat available?

**Groups**

- Runners Club (45) • Parents Circle (120) • Pets & Pawrents (60) • Book Swap (34) • Gardening (27) • Carpool Block C (18)

**Badges (visual)**

- Phone Verified • Residence Verified • Community Helper • Safe Driver

---

If you want, I can also convert this into a **ready-to-paste README.md** or draft **page skeletons** (still no JS) so you can drop it directly into Cursor.
