# Visual Search App — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for a visual search app where users **upload/take a photo** to find **similar items** for **shopping** or **information**. V1 is **JavaScript-free**—no real camera access, model inference, or retailer links. All “AI” bits are **visual placeholders** you can wire up later in Cursor.

---

## 1) Vision & Goals

- Make it effortless to go from **photo → matches** with clear, high-quality results.
- Support two modes: **Shop** (products, prices) and **Learn** (identify plants, landmarks, art, objects).
- Provide **filters** (color, style, price, brand) and **result explanations** (“why this match” copy).
- Keep UI **accessible, responsive, privacy-first, print-friendly**.

---

## 2) Constraints (V1)

- **No JavaScript**: no camera APIs, no uploads, no inference, no outbound links.
- Use semantic HTML and **pure CSS** for states (skeletons, chips, meters, bounding boxes).
- “Confidence scores”, “object detection boxes”, and “visual similarity” are **static**.

---

## 3) Personas & Core User Stories

- **Window Shopper:** “I saw these sneakers—find lookalikes under ₹4k.”
- **Home Decor Fan:** “Match this chair style and color.”
- **Curious Learner:** “What plant is this? Care tips?”
- **Traveler:** “Identify this monument and show a 1-minute summary.”

**Stories (visual-only)**

1. **Upload/Capture** an image → choose **Shop** or **Learn** → see **results grid**.
2. Use **crop** (static overlay) to focus on an object; toggle **detect boxes** (visual).
3. Apply **filters** (price, color, style) or **similarity slider** (CSS range).
4. Open **Result Detail**: product/info card with “why this match” copy.
5. Save to **Collections** and **print/share** a result sheet (print stylesheet).

---

## 4) Information Architecture

- **Home / Search** — upload box, recent searches, mode switch (Shop/Learn)
- **Results** — grid, filters, similarity slider, “why this” notes
- **Detail** — product or info entity page with attributes & related
- **Collections** — saved items/notes screenshots (placeholders)
- **Compare** — side-by-side up to 3 results (visual only)
- **Settings** — region, currency, units, safe-search, theme (visual)
- **About & Privacy** — how it works (concept), data policy, disclaimers

**Global Shell**
Header: app name, mode switch, search/upload button, print link
Sidebar: filters (on desktop), theme toggle (visual)
Main: page content • Footer: help/version/legal

---

## 5) Screen Blueprints

### 5.1 Home / Search

- **Upload Card**: drag & drop zone + “Choose Photo” button (non-functional).
- **Camera Tile** (visual): “Take a photo” icon; shows permission copy only.
- **Mode Switch**: **Shop** | **Learn** (chips).
- **Examples Strip**: small thumbnails (fashion, furniture, plant, landmark).
- **Recent Searches** (visual): last 6 with tiny preview & mode tag.

### 5.2 Results (Core)

- **Header Bar**: image thumbnail, “Edit crop” (CSS overlay), **Visual Similarity** slider (0–100), detected object tags (chips).
- **Filters Panel** (differs by mode):

  - **Shop**: Category, Price range, Color, Brand, Style, Seller (visual), Condition (new/used).
  - **Learn**: Category (plant/landmark/art/object), Confidence (H/M/L), Region, Era/Family.

- **Results Grid**: 2–4 columns, each card contains:

  - **Thumbnail** with **overlaid box** (static) and **confidence** chip.
  - Title, short attributes (color/material/family/era), badge (Official/Community).
  - For Shop: price chip, store chip (placeholder), “Availability: In stock” (copy).
  - For Learn: summary line + “Read more” (goes to Detail).

- **Nudges**: “Crop tighter around the object” | “Try a different angle”.

### 5.3 Detail

- **Hero**: large image with optional **bounding boxes carousel** (static).
- **Right Rail**:

  - **Shop**: price, mock CTA (**Add to Cart / Go to Store**), badges (Free returns, Bestseller).
  - **Learn**: scientific/common name, short description, **“Care/History/Usage”** tabs (copy).

- **Why this match** `<details>`: color/shape/texture cues (copy).
- **Attributes Table**:

  - **Shop**: brand, model, material, color, size options, ratings (stars visual).
  - **Learn**: taxonomy/era/location/artist/medium.

- **Related** carousel (static row).

### 5.4 Collections

- **Saved Items** grid: snapshot + note + tag chips (Shop/Learn).
- **Folders** (visual): “Shoes”, “Living Room”, “Plants”, “Trip to Rome”.
- **Print Sheet**: selected items with thumbnails, notes, and QR placeholders.

### 5.5 Compare

- Up to **3 columns**: image, key attributes, pros/cons list (copy), visual similarity meter bars.

### 5.6 Settings

- Region & Currency (₹ default), Units (cm/in), Safe-search toggle (visual).
- Theme: Light/Dark/High-contrast; Reduced Motion.
- Privacy: “Don’t retain images” statement (copy-only), face blurring note (future).

---

## 6) Component Inventory (CSS-only)

- **Upload Card**, **Camera Tile**, **Mode Switch Chips**
- **Crop Overlay** (static handles), **Detection Box** (border boxes)
- **Similarity Slider** (CSS range), **Filter Chips**, **Price Range**
- **Result Card** (Shop/Learn variants), **Confidence/Price badges**
- **Why-this** `<details>` block, **Attributes Table**
- **Compare Columns**, **Related Row**
- **Collection Card**, **Folder Tile**, **Print Header/Footer**
- **Alert/Nudge Banner** (privacy or safe-search)

---

## 7) Data Model (future-ready; no code)

**VisualQuery**

- `id`, `mode` (shop|learn), `imageId`, `crop` (`{x,y,w,h}`), `tags[]`, `similarity` (0–1), `filters`

**ImageArtifact**

- `id`, `url`, `thumbUrl`, `boxes[]` (`{label, x,y,w,h, confidence}`), `capturedAt`, `source` (upload|camera|example)

**Result**

- `id`, `type` (product|entity), `title`, `subtitle`, `thumbUrl`, `imageUrl`, `similarityScore` (0–1), `attributes{}`, `badges[]`

**Product** _(extends Result)_

- `price`, `currency`, `brand`, `category`, `color`, `material`, `store`, `rating`, `availability`

**Entity** _(extends Result)_

- `category` (plant|landmark|art|object), `summary`, `meta{taxonomy|era|artist|location}`, `sources[]` (citations later)

**Collection**

- `id`, `name`, `items[]` (`{resultId, note}`), `createdAt`

**Settings**

- `region`, `currency`, `units`, `theme`, `safeSearch` (bool), `privacyPrefs`

---

## 8) CSS Architecture & Naming

- **BEM examples:**
  `.upload-card`, `.mode-chip--active`, `.result-card--shop`, `.result-card--learn`,
  `.box--detected`, `.badge--confidence`, `.filter__group`, `.meter--similarity`,
  `.attrs__row`, `.compare__col`, `.collection__tile`, `.nudge--privacy`
- Layers:

  1. `tokens.css` — colors/spacing/type
  2. `base.css` — reset & typography
  3. `utilities.css` — grid/flex/gap/visually-hidden
  4. `components.css` — cards, chips, boxes, sliders, tables, banners
  5. `layouts.css` — shell, filters+grid, detail two-column
  6. `themes.css` — light/dark/high-contrast/reduced-motion
  7. `print.css` — result sheets & collection pages

---

## 9) Design System

**Colors (Light)**

- Background: #F8FAFC • Surface: #FFFFFF • Text: #0F172A
- Accent: #2563EB • Shop accent: #10B981 • Learn accent: #8B5CF6
- Warning: #F59E0B • Danger: #DC2626 • Info: #3B82F6

**Dark**

- Background: #0B1220 • Surface: #111827 • Text: #E5E7EB

**Typography**

- Display 28 • H1 24 • H2 20 • Body 16 • Caption 12–13
- **Tabular numerals** for prices/scores.

**Imagery/Icons**

- Camera, crop, box, tag, slider, cart, leaf, landmark, palette.

**Spacing & Radius**

- Scale: 4/8/12/16/24/32; Radius: 12 (cards), 6 (chips), 999 (pills).
- Focus: 3px high-contrast outlines; reduced-motion variant.

---

## 10) Accessibility, Privacy & Safety

- Landmarks: `<header> <nav> <main> <footer>`; one H1/page.
- All controls labeled; keyboard navigable; large, visible focus rings.
- **No color-only signals**—pair confidence/availability with text/icons.
- **Privacy-first copy**: Avoid personal data, faces, or sensitive documents.
- **Safe-search** (UI only) warns and hides restricted categories in V1.
- Attribution section (copy) to encourage citing sources for Learn results.

---

## 11) Print Styles

- **Result Sheet**: grid with image, title, price/info, notes; QR placeholders.
- **Comparison Sheet**: 2–3 columns with key attributes & pros/cons.
- Black on white; hide nav; page numbers; footer: “Visual Search — v0.1”.

---

## 12) File & Folder Structure

```
root
 ├─ index.html           (Home / Search)
 ├─ results.html         (Grid + filters)
 ├─ detail.html          (Product/Entity)
 ├─ compare.html
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
     ├─ examples/
     └─ placeholders/
```

---

## 13) Page Copy (paste-ready snippets)

- **Home helper:** “Snap or upload a photo. Choose **Shop** for lookalikes or **Learn** for info.”
- **Nudge (results):** “Crop closer to remove background clutter.”
- **Why this match:** “Similar **shape** and **color palette** to your selection.”
- **Shop badge:** “Price & availability are placeholders in this prototype.”
- **Learn disclaimer:** “Names and confidence are illustrative; verify with trusted sources.”
- **Privacy banner:** “Avoid faces and personal documents. Images are not stored in this prototype.”

---

## 14) Acceptance Criteria (V1)

- Home shows **upload/camera** tiles, mode switch, examples, and recent searches (visual).
- Results page displays **filters**, **similarity slider**, **detected object chips**, and a **grid of ≥12 cards** across both modes.
- Each result card shows a **confidence badge**, a **box overlay**, and **why-this** text on hover/click (visual).
- Detail page has **hero image**, **attributes table**, **why-this details**, and **related** row.
- Collections page lists **≥2 folders** and **≥8 saved items** (placeholders) with a print link.
- Compare page supports **up to 3** side-by-side columns with key attributes.
- Print styles output **Result Sheet** and **Comparison** cleanly.
- Baseline a11y (headings, labels, focus, contrast) passes.

---

## 15) Future Enhancements

- Real **camera access**, **image uploads**, and **on-device preprocessing** (resize/normalize).
- **Vision model** (local or API): detection + embedding; **ANN** search index for similarity.
- **Multi-object queries** (choose which object to search) and **text+image** hybrid prompts.
- **Retail integrations** (affiliate/merchant feeds), stock/price freshness, deep links.
- **Knowledge graph** for Learn mode with citations and multilingual summaries.
- **On-device redaction/face blur**, NSFW filtering, copyright detection.
- Personalization: style preferences, brand blocking, saved filters; cross-device sync.
- PWA + offline previews; batch search for wardrobe/home snapshots.

---

## 16) Sample Static Data (populate UI)

**Detected boxes (visual):**

- `{"label":"sneaker","x":12,"y":18,"w":56,"h":28,"confidence":0.92}`
- `{"label":"plant","x":22,"y":10,"w":40,"h":60,"confidence":0.86}`

**Shop results (cards):**

- “Runner Flex 2.0 — Black/White” — **₹3,499** — Store: MockMart — **Confidence: 0.91**
- “Street Sprint Low — Mono” — **₹3,199** — Store: ShoeHub — **0.87**
- “Aero Knit Sneaker — Graphite” — **₹3,899** — Store: SneakPeek — **0.84**

**Learn results (cards):**

- “Ficus elastica (Rubber Plant)” — **Confidence: 0.89** — Care: bright indirect, moderate water
- “India Gate, New Delhi” — **0.94** — Built: 1931; Architect: Lutyens (copy)
- “Impressionist Oil Painting (style)” — **0.73** — Era: late 19th century (copy)

**Why this (examples):**

- “High overlap in **toe shape**, **sole pattern**, and **color tone**.”
- “Leaf **venation** and **gloss** match top-3 candidates.”

---

If you want, I can also turn this into **ready-to-paste page skeletons** (still no JS) or a **README.md** tailored for Cursor.
