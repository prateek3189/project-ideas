# AI Travel Agent — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an AI travel planner that **auto-generates itineraries** and (visually) **books flights, stays, and activities** based on **budget** and **preferences**. V1 is **JavaScript-free**—no live prices, availability, payments, logins, or maps. Everything dynamic is a **placeholder** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Create a **one-page plan per trip** with day-by-day activities, transit, and cost estimates.
- Keep users within **budget** with a clear **cost bar** and swap suggestions.
- Offer **quick “Book” flows** (visual only) and **printable** itineraries.
- Ship an **accessible, responsive, multilingual-ready** scaffold.

---

## 2) Constraints (V1)

- **No JavaScript**: no real search, booking, maps, or payments.
- Use semantic HTML (`<details>`, forms, tables) and **pure CSS** for meters/charts.
- “AI” labels are **copy only** (why-this notes, swap logic mock).

---

## 3) Personas & Core User Stories

- **Budget Traveler:** “Show me 4 days in Bangkok under ₹60k with street food & markets.”
- **Family Planner:** “Kid-friendly activities near our hotel; minimal transfers.”
- **Remote Worker:** “Cafés with Wi-Fi, 4-hr focus blocks, evening sights.”
- **Weekend Sprinter:** “48-hour plan, hand luggage, walkable core.”

**Stories (visual-only)**

1. Enter **destination, dates, budget, preferences** → see a **generated itinerary**.
2. Adjust **pace** (relaxed/standard/packed) and **themes** (food, culture, outdoors).
3. Review **cost breakdown** and **swap** an activity or hotel (UI only).
4. “Book” flights/hotels/activities (mock checkout), then **print/share** the trip.

---

## 4) Information Architecture

- **Home / Plan Trip** — trip form and “AI plan” preview
- **Itinerary** — day view, timeline, maps box (placeholder), swaps
- **Bookings** — flights, stays, activities (mock carts & confirmations)
- **Budget** — estimator, categories, tips (CSS bars)
- **Collections** — curated lists (neighborhoods, cafés, must-see)
- **Settings** — currency, language, theme, units (visual)
- **About** — data sources (copy), limitations, disclaimers

**Global Shell**
Header: app name, currency selector (visual), print link
Sidebar: nav + theme toggle (visual)
Main: page content • Footer: help/version/legal

---

## 5) Screen Blueprints

### 5.1 Home / Plan Trip (Generator)

- **Trip Form**: Destination, Dates, Travelers, Budget (total/per person), Pace (Relaxed/Standard/Packed), Themes (Food • Culture • Nature • Nightlife • Family), **Musts/Avoids** textarea.
- **AI Plan Summary** card (after submit – static content):

  - **Cost Meter**: within budget / over budget (CSS progress).
  - **Hotel** suggestion (area + star level).
  - **Flight** time window preference (morning/evening).
  - **3 highlight cards** with “Why this” `<details>`.

### 5.2 Itinerary (Core)

- **Day Tabs**: Day 1 • Day 2 • Day 3… (chips)
- **Timeline Blocks** per day:

  - **Morning / Midday / Evening** sections
  - Each block: title, short copy, **walk/metro/ride** chip, **est. cost/time**, distance (placeholder), **swap** button (visual).

- **Map Box** placeholder with pin list.
- **Food Nearby** strip (chips).
- **Notes**: safety/etiquette/weather tip (copy).
- **Print Itinerary** link (print stylesheet).

### 5.3 Bookings

- **Flights** tab (mock): outbound/return cards with times, baggage note, fare type.
- **Stays** tab: hotel/apartment cards with area, rating (stars visual), amenities chips.
- **Activities** tab: tours/entry/tickets with time slots (visual).
- **Cart Summary** side card: subtotal, fees (copy), total; **Proceed** → **Confirmation** (static ticket PDFs/QR placeholders).

### 5.4 Budget

- **Tiles**: Total budget, Planned spend, Buffer, Per-day average.
- **Bars** (CSS): **Flights / Stay / Food / Local transit / Attractions / Misc**.
- **Tips** `<details>`: “shift one paid museum → free park”; “metro pass saves ₹… (copy)”.
- **Currency note** (visual) and multi-currency disclaimer.

### 5.5 Collections

- **Neighborhoods** cards: vibe, average price, walkability.
- **Top Cafés / Kid-friendly / Sunset spots** lists (static).
- **Seasonal** banner (visual): “Monsoon: pack light rain jacket.”

### 5.6 Settings

- Currency (₹/\$/€), Language (visual), Units (km/mi), Theme (light/dark/high-contrast), Reduced Motion, Privacy (local-only concept).

---

## 6) Component Inventory (CSS-only)

- **Trip Form** with chips and sliders
- **Cost Meter** progress bar
- **Itinerary Timeline Block** (time, title, chips, “why this”, swap)
- **Map Box** placeholder grid with pins
- **Booking Cards** (flight, stay, activity variants)
- **Cart Summary** and **Confirmation Ticket** (QR placeholder)
- **Budget Bars** & **Category Chips**
- **Collection Card** (neighborhood/POI)
- **Alert/Nudge Banner** (weather/holiday)
- **Print Header/Footer** (itinerary + tickets)

---

## 7) Data Model (future-ready; no code)

**Trip**

- `id`, `destination`, `dates`, `travelers` (adults/kids), `budgetTotal`, `pace`, `themes[]`, `musts`, `avoids`

**Plan**

- `tripId`, `days[]` with `segments[]` ({ timeOfDay, title, type (sight|food|transit|rest), estCost, estTime, transport, notes })

**Option**

- `kind` (flight|stay|activity), `provider`, `title`, `subtitle`, `price`, `currency`, `rating`, `area`, `amenities[]`, `tags[]`

**Cart**

- `items[]` (`{kind, optionId, qty, price}`), `currency`, `subtotal`, `fees`, `total`

**Budget**

- `cap`, `planned`, `byCategory[]` (flights, stay, food, transit, attractions, misc)

**Preference**

- `pace`, `foodPrefs[]`, `accessibility[]`, `avoid[]` (crowds, night travel, etc.)

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.trip-form`, `.chip--theme`, `.meter--budget`, `.day-tabs`, `.timeline__block`, `.timeline__chip--walk`, `.booking-card--flight`, `.cart__total`, `.map-box`, `.bar--flights`, `.nudge--weather`
- Layers:

  1. `tokens.css` — colors, spacing, type
  2. `base.css` — reset & typography
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — cards, chips, bars, timeline, cart, tickets
  5. `layouts.css` — shell, two-column itinerary/bookings
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — itinerary & tickets

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Accent: #2563EB • Success: #16A34A • Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6
- Category hints (optional): Flights #3B82F6 • Stay #8B5CF6 • Food #10B981 • Transit #F59E0B • Sights #06B6D4

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB (AA)

**Typography**

- Display 28 • H1 24 • H2 20 • Body 16 • Caption 12–13
- Use **tabular numerals** for prices & times.

**Spacing & Radius**

- Scale: 4/8/12/16/24/32; Radius: 12 (cards), 999 (chips).
- Focus rings: high-contrast; Reduced-motion theme available.

Icons: plane, bed, fork, train, walk, pin, ticket.

---

## 10) Accessibility & Safety

- Landmarks `<header><nav><main><footer>`; one **H1** per page.
- Labels for all inputs; keyboard navigable; visible focus.
- Don’t rely on color alone—pair chips/labels with icons or text.
- **Safety copy**: travel advisories, local norms, scam alerts (static).
- **Content notes**: accessibility tags (step-free, quiet hours) where relevant.

---

## 11) Print Styles

- **Itinerary**: day-by-day with times, addresses, quick tips; hide nav; black on white.
- **Tickets/Confirmations**: flight, hotel, activity stubs with QR placeholders.
- Footer: “AI Travel Agent — v0.1” + page numbers.

---

## 12) File & Folder Structure

```
root
 ├─ index.html          (Home / Plan Trip)
 ├─ itinerary.html
 ├─ bookings.html       (Flights / Stays / Activities)
 ├─ budget.html
 ├─ collections.html
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

- **Generator nudge:** “Building a plan that fits **your budget** and **pace**.”
- **Why this (hotel):** “Walkable to Old Town + easy metro access.”
- **Why this (activity):** “Rain forecast → pick an indoor museum in the afternoon.”
- **Budget tip:** “Swap 1 paid tour for a free walking route to save \~₹2,000.”
- **Booking disclaimer:** “Prices & availability are illustrative in this prototype.”
- **Safety note:** “Watch out for unofficial taxis at arrival; use the airport desk or app cabs.”

---

## 14) Acceptance Criteria (V1)

- Home shows **Trip Form** and renders an **AI Plan Summary** with budget meter and 3 highlight cards.
- Itinerary page displays **≥3 days** with **3 segments/day**, transport chips, “why this” notes, and a map box placeholder.
- Bookings page lists **≥3 flight options**, **≥6 stays**, **≥6 activities**, plus a **Cart** and **Confirmation** view (static).
- Budget page shows **tiles** + **category bars** and at least **3 savings tips**.
- Collections page shows **≥6 cards** (neighborhoods/POIs).
- Print styles output **Itinerary** and **Tickets** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real **search/booking** integrations (GDS/OTAs), payments, holds & cancellations.
- Live **pricing**, fare calendars, and **availability** with caching.
- **Map** routing, time-to-walk/metro, crowd/queue estimates; offline maps.
- Personalization from **past trips**, loyalty programs, visa checks, weather windows.
- Multi-city & open-jaw planning; trains/ferries; carbon footprint & greener swaps.
- Collaboration: shared trips, roles, comments; export to Google/Apple Calendar.
- PWA + offline itinerary & ticket wallet.

---

## 16) Sample Static Data (populate UI)

**Trip Form (example)**

- Destination: **Singapore** • Dates: **15–19 Nov** • Travelers: **2** • Budget: **₹85,000** • Pace: **Standard**
- Themes: **Food**, **Family**, **Outdoors** • Musts: “Gardens by the Bay” • Avoids: “Late-night events”

**AI Plan Summary**

- Cost meter: **Within budget (₹79,800 est.)**
- Stay: **Bugis 3★ boutique** — breakfast near MRT
- Highlights: **Night Safari**, **Hawker food trail**, **Marina Bay night show**

**Itinerary (Day 2 snippet)**

- **Morning**: Chinatown heritage walk — **walk** — Est. **₹0** — _Why:_ “Close to hotel; low heat early.”
- **Midday**: Hawker Centre tasting — **metro** — Est. **₹1,200**
- **Evening**: Marina Bay Spectra — **walk** — Est. **₹0**

**Bookings (samples)**

- Flights: **6E 151** BOM→SIN 09:25–17:40 (1 stop) — **₹24,500 pp**; **SQ 423** nonstop — **₹31,800 pp**
- Stays: **Hotel 81 Bugis 3★** — ₹7,200/nt; **V Hotel Lavender 3★** — ₹8,000/nt; **Capsule Downtown** — ₹2,100/nt
- Activities: **Night Safari** — ₹3,200; **River Cruise** — ₹1,500; **City Bike Tour** — ₹2,000

**Budget bars (₹)**

- Flights **49,000** • Stay **28,800** • Food **6,500** • Transit **1,200** • Attractions **6,000** • Misc **2,000**

---

If you want, I can also convert this into **ready-to-paste page skeletons** (still no JS) or a **README.md** tailored for your Cursor workspace.
