# Voice-Driven To-Do List — Project Document (Plain HTML & CSS)

> **Goal:** Create a **static HTML + CSS v1 prototype** of a **voice-driven to-do list app** that lets users **add, view, and manage tasks** hands-free. The first version focuses on **UI scaffolding only**, with placeholders for speech recognition, syncing, and notifications.

---

## **1) Vision & Goals**

- Provide a **hands-free task management experience**.
- Allow **task creation via voice** (placeholder in v1).
- Display tasks in a clean, responsive UI for easy viewing and management.
- Prepare structure for **cross-device syncing and reminders** in later versions.
- Ensure **semantic, accessible, and responsive markup**.

---

## **2) Constraints (V1)**

- **No JavaScript**; all interactivity is visual only.
- Speech controls, syncing, and reminders will be **non-functional placeholders**.
- Focus purely on layout, styles, and reusable UI patterns.
- Keep CSS clean and modular for easy enhancement later.

---

## **3) Primary Personas & User Stories**

- **Busy Professional:** “I need to capture tasks quickly while driving or multitasking.”
- **Student:** “I want reminders and a way to organize tasks by subject or priority.”
- **Parent/Guardian:** “I want hands-free task entry while cooking or managing kids.”

### **Core Stories**

1. Add tasks by voice (button + placeholder prompt in v1).
2. See **task list** with priorities, reminders, and tags.
3. Mark tasks as complete (static state toggle in v1).
4. Filter by **date, priority, or tags** (visual filters only).
5. View **reminder schedule** (static list).

---

## **4) Information Architecture**

- **Pages / Sections**

  - Dashboard — task list and quick voice input
  - Add Task — voice entry placeholder + manual form
  - Reminders — overview of upcoming reminders
  - Settings — profile, device sync, and preferences
  - About — description of the app and future AI features

- **Global Shell**

  - **Header**: app name, voice input button (non-functional), profile icon
  - **Sidebar**: navigation links, theme toggle (visual only)
  - **Content Area**: main screen for each page
  - **Footer**: version number and support link

---

## **5) Screen Blueprints**

### **5.1 Dashboard**

- Voice Capture Banner:

  - “Tap to Speak” button (static)
  - Text area showing “Listening…” placeholder

- Task List:

  - Task cards with:

    - Title
    - Due date badge
    - Tags (work, personal, urgent)
    - Status checkbox (static)

- Quick Filters:

  - “All”, “Today”, “This Week”, “Completed”

---

### **5.2 Add Task**

- **Voice Input Placeholder:**

  - Icon + instruction text (“Say your task after the beep…”)

- **Manual Input Form:**

  - Task Title
  - Description
  - Due Date (date picker)
  - Priority (Low/Medium/High)
  - Tags (comma separated)

- **Action Buttons:** Save (visual) / Cancel

---

### **5.3 Reminders**

- Static cards showing:

  - Task title
  - Reminder time/date
  - Status (Upcoming, Snoozed, Completed)

- Placeholder for "Sync Across Devices" toggle

---

### **5.4 Settings**

- Profile Section
- Device Sync (visual toggle)
- Notification Preferences (visual toggles)
- Theme: Light/Dark toggle

---

### **5.5 About**

- Mission statement: “Hands-free productivity for your busy life.”
- Future features section: “Smart AI suggestions, automatic reminders, and real-time syncing.”

---

## **6) Component Inventory**

- **Header:** App name, profile icon, voice button
- **Sidebar:** Navigation links with active state
- **Task Card:** Title, due date, priority chip, tags, static checkbox
- **Voice Capture Box:** Icon, text placeholder, wave animation (CSS only)
- **Reminders Card:** Time/date + status badge
- **Badges/Chips:** For priority (Low, Medium, High) and status (Pending, Completed)
- **Buttons:** Primary, Secondary, and Icon buttons
- **Filters:** Pills with active/inactive styles

---

## **7) Data Model (Future-Ready)**

**Task Object**

- `id`
- `title`
- `description`
- `dueDate`
- `priority` (Low/Med/High)
- `tags` (array)
- `status` (Pending/Completed)
- `reminderTime`
- `createdAt`
- `updatedAt`

**User Preferences**

- `theme`
- `syncEnabled`
- `notificationPrefs`

---

## **8) CSS Architecture**

- Use **BEM naming** for classes
- Separate layers:

  - tokens.css
  - base.css
  - utilities.css
  - components.css
  - layouts.css
  - themes.css
  - print.css

- Responsive breakpoints:

  - Small: ≤480px
  - Medium: 768px
  - Large: 1024px

---

## **9) Design System**

**Colors**

- Primary Accent: Blue
- Background: White (light mode), Dark Gray (dark mode)
- Priority Chips:

  - Low: Green
  - Medium: Amber
  - High: Red

**Typography**

- H1: 24px
- Body: 16px
- Captions: 12px

**Spacing & Radius**

- Spacing: 4, 8, 16, 24
- Radius: 8px (cards), 999px (chips)

---

## **10) Accessibility**

- Labels for all form inputs
- Visible focus rings
- High contrast for text and badges
- Semantic landmarks: `<header>`, `<nav>`, `<main>`, `<footer>`

---

## **11) Print Styles**

- Hide sidebar and buttons
- Show task lists and reminders in plain black/white text

---

## **12) Sample Folder Structure**

```
root
 ├─ index.html          (Dashboard)
 ├─ add-task.html
 ├─ reminders.html
 ├─ settings.html
 ├─ about.html
 ├─ styles/
 │   ├─ tokens.css
 │   ├─ base.css
 │   ├─ components.css
 │   ├─ layouts.css
 │   ├─ themes.css
 │   ├─ print.css
 └─ assets/
     ├─ icons/
     ├─ illustrations/
```

---

## **13) Acceptance Criteria (V1)**

- Pages load cleanly with no JS
- Voice button and “listening” placeholder visible on dashboard
- Task cards display correctly across mobile and desktop
- Reminders page shows static entries
- Print version readable and simplified
- Meets WCAG AA contrast and semantic markup guidelines

---

## **14) Future Enhancements**

- Voice-to-text capture using Web Speech API
- Cloud sync (Firebase, Supabase, or custom backend)
- AI to auto-prioritize tasks based on urgency or habits
- Smart reminders based on location or calendar events
- Offline-first PWA support

---

## **15) Sample Content Matrix**

Populate static UI with examples:

- Tasks:

  - “Call mom at 6 PM”
  - “Submit project report by Friday”
  - “Buy groceries”

- Reminders:

  - “Doctor appointment tomorrow at 9 AM”
  - “Weekly review every Sunday at 8 PM”

---

Would you like me to turn this into a **README.md** template so you can paste it directly into Cursor?
