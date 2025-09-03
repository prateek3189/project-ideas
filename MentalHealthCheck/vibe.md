# Anonymous Mental Health Chat — Project Document (Plain HTML & CSS)

> **Goal:** Build a **static HTML + CSS v1 prototype** for an **anonymous, text-based mental health chat** that connects **help-seekers** with **trained listeners**. V1 is **JavaScript-free**—all matching, chat, moderation, and safety escalations are **visual placeholders** you can wire up later.

---

## 1) Vision & Goals

- Provide a **kind, stigma-free** place for people to talk with **trained (non-clinical) listeners**.
- Keep users **anonymous by default** (pseudonyms, no emails/phone required in V1).
- Make **safety and consent** explicit: clear scope, crisis routes, and respectful boundaries.
- Ship an **accessible, responsive, print-friendly** UI scaffold that’s easy to enhance.

---

## 2) Constraints (V1)

- **No JavaScript**: no real-time messaging, auth, or moderation backends.
- **Placeholders** for: queue/matching, chat bubbles, typing indicators, reporting, and escalation flows.
- **No medical advice**: copy must reflect **peer support**, not therapy. Add strong disclaimers.

---

## 3) Personas & Core Stories

- **Seeker**: “I’m overwhelmed and need someone to listen right now—privately.”
- **Listener**: “I’m trained in active listening; I want clear boundaries and safety tools.”
- **Moderator**: “I need to triage sessions, handle reports, and enforce rules.”

**User Stories (visual-only)**

1. Anonymous onboarding → consent → **mood check-in** → **matching** → chat room.
2. Listener toggles **available** → receives a request → opens **session** with safety toolkit.
3. **Report/Flag** message, view **resources**, end session with **feedback** from both sides.
4. **Crisis pathway**: display immediate help modal and resource links.

---

## 4) Information Architecture

- **Home / Start** — what this is (and isn’t), start support, become a listener
- **Get Support** — consent → mood check-in → queue → session room
- **Session Room** — chat view, tools, resources, end/feedback
- **Listeners** — onboarding, code of conduct, availability card, sample dialogues
- **Moderation** — report queue (visual), safety policies, escalation guides
- **Resources** — crisis lines, self-help articles (placeholders), grounding exercises
- **Settings** — theme, text size, language (visual), anonymity controls
- **About** — peer-support scope, privacy, disclaimers

**Global Shell**

- Header: app name, quick **Get Help** button
- Sidebar: nav + theme toggle (visual)
- Footer: disclaimers, last updated

---

## 5) Screen Blueprints

### 5.1 Home / Start

- **Hero**: “Talk to a trained listener, anonymously.”
- **Two CTAs**: “Get Support” / “Become a Listener”
- **Scope Notice** (prominent): “Not therapy or crisis service.”
  `<details>`: when to use / not use.
- **Crisis Banner** (always visible): “If you’re in immediate danger, contact emergency services in your region.” (links to **Resources**)

### 5.2 Get Support Flow

1. **Consent & House Rules** (checklist + agree button)

   - No medical advice, be respectful, privacy basics.

2. **Mood Check-in** (chips + optional text): anxious • sad • angry • numb • other

   - Optional tags: relationship • work • health • grief

3. **Queue** (visual): “Finding a listener… \~2 min” + **grounding card** (breathing exercise)
4. **Session Room** (Core)

   - **Pseudonyms** (e.g., “Seeker-Sky”, “Listener-Willow”)
   - **Chat**: bubbles, timestamp, “Listener is typing…” (visual)
   - **Safety Toolbar**:

     - **Resources** (opens side panel)
     - **Flag/Report** (opens modal)
     - **Crisis** (bright button → crisis modal)
     - **End Session**

   - **Guidance Strip** (non-intrusive): “Listeners don’t diagnose or prescribe.”

5. **End & Feedback**

   - 1–5 helpfulness, “What helped?”, “What could be better?”
   - Offer **resource pack** + “Save/Print” (print stylesheet)

### 5.3 Listener Console

- **Status Card**: Available / On break (visual toggle)
- **Training/Reminders**: active listening micro-tips, boundaries
- **Incoming Requests** list (mock): reason tags + time waiting
- **Session Tools** (visual icons): empathic prompts, reflective statements generator (copy-only), resource quick-links
- **Post-Session Notes** (private; placeholder)

### 5.4 Moderation (Visual)

- **Reports Queue**: session id, reason chip (harassment, medical advice, crisis, spam)
- **Triage Board**: **Crisis**, **High**, **Normal** columns
- **Actions**: warn, restrict, permanent block (copy), escalate to crisis flow
- **Audit Log**: non-PII session metadata (placeholder)

### 5.5 Resources

- **Immediate Help**: “Call your local emergency number (e.g., 112/911).”
  “Contact your country’s national crisis hotline” (add real links later).
- **Grounding**: 4-7-8 breathing, 5-4-3-2-1 senses, journaling prompts (copy)
- **Directories**: therapists, NGOs, support groups (link placeholders)

### 5.6 Settings

- **Anonymity**: regenerate pseudonym, hide typing (visual)
- **Display**: Large text, high contrast, reduced motion
- **Language**: list (visual)

---

## 6) Component Inventory (CSS-only)

- **Consent Checklist**, **Crisis Banner**
- **Mood Chips**, **Tag Chips**
- **Queue Card** with progress bar
- **Chat Bubbles** (seeker/listener variants), **Typing Dot** (CSS anim)
- **Safety Toolbar**: Resources • Flag • Crisis • End
- **Modal** (Crisis / Report / End)
- **Listener Availability Card**, **Request Row**
- **Report Row**, **Triage Card**
- **Resource Card**, **Exercise Card**
- **Feedback Form**, **Print Header/Footer**

---

## 7) Safety & Policy Model (UI copy; no logic in V1)

- **Scope Gate**: required consent acknowledging **peer support** (not therapy/diagnosis).
- **Crisis Pathway**:

  - Dedicated **Crisis button** always visible.
  - Crisis modal: “If you might harm yourself or someone else, consider contacting emergency services now.”
  - Show **immediate help** resources prominently.

- **Listener Toolkit**: de-escalation script snippets (copy-only), boundaries (“I can listen and support; I can’t provide medical advice.”).
- **Reporting & Moderation**: quick report with categories; visible moderation policy.
- **Privacy**: no personal identifiers requested; discourage sharing PII.

---

## 8) Data Model (future-ready; no code)

**User (Anonymous)**

- `id`, `role` (seeker|listener|moderator), `pseudonym`, `createdAt`, `flags[]`, `locale`

**Session**

- `id`, `seekerId`, `listenerId`, `startedAt`, `endedAt`, `moodTags[]`, `status` (queued|active|ended|escalated)

**Message**

- `id`, `sessionId`, `senderRole`, `text`, `createdAt`, `flags[]` (harassment|crisis|spam), `visibility` (normal|hidden)

**Report**

- `id`, `sessionId`, `messageId?`, `reason`, `notes`, `status` (new|triaged|actioned)

**ResourceLink**

- `id`, `type` (crisis|exercise|directory), `title`, `url`, `locale`

**Feedback**

- `sessionId`, `rating1to5`, `comments`, `followupOptIn` (false by default)

---

## 9) CSS Architecture & Naming

- **BEM** examples:
  `.consent__item`, `.mood-chip--active`, `.queue__bar`, `.chat__bubble--seeker`, `.toolbar__btn--crisis`, `.modal--crisis`, `.report__row--high`, `.triage__col--crisis`, `.resources__card`
- Layers:

  1. `tokens.css`—colors/spacing/type
  2. `base.css`—reset & typography
  3. `utilities.css`—flex/grid/gap/visually-hidden
  4. `components.css`—chips, banners, bubbles, modals, lists, forms
  5. `layouts.css`—shell, two-column session
  6. `themes.css`—light/dark/high-contrast/reduced-motion
  7. `print.css`—resource pack & session summary

---

## 10) Design System (Calm & Trustworthy)

**Colors (Light)**

- Background: #F6F8FB • Surface: #FFFFFF • Text: #0F172A
- Primary: #2563EB • Success: #16A34A • Warning: #F59E0B • Danger (crisis): #DC2626 • Info: #3B82F6

**Dark**

- Background: #0B1020 • Surface: #121826 • Text: #E5E7EB (AA contrast)

**Type**

- Display 28 • H1 24 • H2 20 • Body 16 • Caption 12–13
- Generous line-height (1.5–1.7); avoid dense blocks.

**Motion**

- Subtle only; provide **reduced-motion** theme.

Icons: chat bubble, shield, heart, alert, flag, lifebuoy.

---

## 11) Accessibility & Trauma-Informed UX

- Landmarks (`<header><nav><main><footer>`), one **H1** per page.
- Large, high-contrast focus indicators; keyboard-only flows.
- Avoid flashing/animated content; keep language **non-judgmental**.
- **Content warnings** for sensitive tags; opt-in viewing of reported messages.
- Provide **quick exit** link (visual only) to leave session screen.

---

## 12) Privacy & Data Hygiene (copy; enforce later)

- Anonymous by default; pseudonyms only.
- Do not request PII; actively **discourage sharing PII** in chat.
- Message retention policy (copy): “Your messages are not stored beyond session except for safety reports.”
- Explain moderation visibility and report handling.

---

## 13) Print Styles

- **Resource Pack**: crisis contacts placeholders, grounding exercises, self-care plan.
- **Session Summary (user view)**: tips discussed, resource links; **no transcript**.

---

## 14) File & Folder Structure

```
root
 ├─ index.html           (Home / Start)
 ├─ support.html         (Consent → Mood → Queue)
 ├─ session.html         (Chat Room)
 ├─ listeners.html       (Listener Console)
 ├─ moderation.html      (Reports & Triage)
 ├─ resources.html
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

## 15) Page Copy (paste-ready snippets)

- **Scope Notice:** “We offer **peer support** from trained listeners—not medical care or therapy.”
- **Consent checkbox items:** “Respectful language”, “No hate/harassment”, “No medical/clinical advice”, “No PII sharing”.
- **Crisis modal:** “If you may be at risk of harming yourself or others, consider contacting **your local emergency number (e.g., 112/911)** or your **national crisis hotline**. You are not alone.”
- **Listener boundary:** “I can listen and support. I can’t diagnose, prescribe, or give professional advice.”
- **Grounding card:** “4-7-8 Breathing: inhale 4, hold 7, exhale 8 (×4).”
- **End screen nudge:** “You took a strong step today. Consider a brief walk, water, and sleep hygiene tonight.”

---

## 16) Acceptance Criteria (V1)

- Home shows **scope**, **crisis banner**, and two CTAs.
- Support flow renders **consent**, **mood check-in**, **queue**, and **session room** with safety toolbar.
- Session room includes **chat bubbles**, **typing indicator**, **report**, **resources**, **crisis**, **end** actions (visual).
- Listener console displays **availability** and **incoming requests** (mock).
- Moderation shows **reports queue** with severity chips and triage columns (visual).
- Resources page surfaces **immediate help** first and at least **5** supportive exercises (copy).
- Print stylesheet outputs a clean **Resource Pack**.
- Passes baseline a11y: headings, labels, focus, contrast, reduced motion.

---

## 17) Future Enhancements

- Real-time chat (WebSocket/WebRTC data), queue & matching service with anonymity.
- Crisis keyword detection → **just-in-time prompts** + fast-path resources.
- Listener training modules & certification, scheduling, session re-connects.
- Multilingual content; locale-specific resource directories.
- Privacy tech: **ephemeral storage**, client-side redaction, encrypted transcripts (opt-in).
- Moderation ML assist (spam/harassment), rate limits, abuse prevention.

---

## 18) Sample Static Data (populate UI)

- **Pseudonyms**: Seeker-Sky, Listener-Willow, Mod-Harbor.
- **Mood tags**: anxious, sad, overwhelmed, grieving, “other”.
- **Report reasons**: harassment, medical advice, crisis concern, spam.
- **Resource items**: “Emergency (your country)”, “National hotline (insert)”, “Grounding exercise”, “Sleep tips”, “Finding a therapist (guide)”.

---

If you’d like, I can turn this into a **README.md** or draft **page skeletons** (still no JS) to paste straight into Cursor.
