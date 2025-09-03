# Anonymous Mental Health Chat - V1 Prototype

> **A static HTML + CSS prototype for an anonymous, text-based mental health chat platform that connects help-seekers with trained listeners.**

## 🎯 Project Overview

This is a **JavaScript-free V1 prototype** for an anonymous mental health chat platform. All matching, chat, moderation, and safety escalations are **visual placeholders** that can be wired up with real functionality later.

### Key Features

- **Anonymous by default** - No personal information required
- **Trained listeners** - Peer support from trained, non-clinical listeners
- **Safety-first design** - Clear crisis pathways and safety tools
- **Accessible & responsive** - Works on all devices with accessibility features
- **Multiple themes** - Light, dark, high-contrast, and reduced-motion themes
- **Print-friendly** - Resource packs and session summaries can be printed

## 🏗️ Project Structure

```
MentalHealthCheck/
├── index.html              # Home page with hero and scope notice
├── support.html            # Support flow (consent → mood → queue → session)
├── session.html            # Chat room with safety toolbar
├── listeners.html          # Listener console and training info
├── moderation.html         # Reports queue and triage board
├── resources.html          # Crisis help and grounding exercises
├── settings.html           # Theme, accessibility, and privacy settings
├── about.html              # Mission, values, and disclaimers
├── styles/
│   ├── tokens.css          # Design system tokens and variables
│   ├── base.css            # Reset, typography, and base styles
│   ├── utilities.css       # Utility classes for layout and spacing
│   ├── components.css      # Reusable component styles
│   ├── layouts.css         # Page layouts and grid systems
│   ├── themes.css          # Theme switching and accessibility
│   └── print.css           # Print styles for resource packs
└── assets/
    ├── icons/              # Icon assets (placeholder)
    └── placeholders/       # Image placeholders
```

## 🎨 Design System

### Color Palette

**Light Theme:**

- Background: `#f6f8fb` (Primary), `#ffffff` (Secondary)
- Text: `#0f172a` (Primary), `#475569` (Secondary)
- Primary: `#2563eb` (Blue)
- Success: `#16a34a` (Green)
- Warning: `#f59e0b` (Orange)
- Danger: `#dc2626` (Red)

**Dark Theme:**

- Background: `#0b1020` (Primary), `#121826` (Secondary)
- Text: `#e5e7eb` (Primary), `#9ca3af` (Secondary)

### Typography

- **Font Stack:** System fonts (SF Pro, Segoe UI, Roboto, etc.)
- **Scale:** 12px to 36px with consistent line heights
- **Weights:** 400 (Normal), 500 (Medium), 600 (Semibold), 700 (Bold)

### Components

- **Buttons:** Primary, secondary, success, warning, danger, crisis variants
- **Cards:** Elevated, crisis, and standard variants
- **Chips:** Mood, tag, and status indicators
- **Chat Bubbles:** Seeker and listener variants with typing indicators
- **Modals:** Crisis, resources, and standard modals
- **Forms:** Inputs, checkboxes, and validation states

## 📱 Pages & Features

### 1. Home Page (`index.html`)

- Hero section with clear value proposition
- Scope notice explaining peer support vs. therapy
- Crisis banner with emergency resources
- Two main CTAs: "Get Support" and "Become a Listener"
- Feature highlights and safety information

### 2. Support Flow (`support.html`)

- **Step 1:** Consent and house rules agreement
- **Step 2:** Mood check-in with emotion and topic chips
- **Step 3:** Queue with progress bar and grounding exercise
- **Step 4:** Chat room with safety toolbar (visual prototype)

### 3. Session Room (`session.html`)

- Full-screen chat interface
- Message bubbles with timestamps
- Typing indicators (CSS animation)
- Safety toolbar with resources, report, crisis, and end buttons
- Resource sidebar and crisis modal

### 4. Listener Console (`listeners.html`)

- Availability status toggle
- Incoming request management
- Training reminders and tips
- Sample dialogue examples
- Application process overview

### 5. Moderation Dashboard (`moderation.html`)

- Reports triage board (Crisis, High, Normal)
- Active sessions monitor
- Listener management tools
- Safety policies and audit log

### 6. Resources (`resources.html`)

- Crisis support with emergency numbers
- Grounding exercises (4-7-8 breathing, 5-4-3-2-1 senses)
- Self-care and wellness resources
- Professional help directory
- Printable resource pack

### 7. Settings (`settings.html`)

- Theme selection (Light, Dark, High Contrast, Reduced Motion)
- Accessibility options
- Privacy and anonymity controls
- Language and region settings
- Data management options

### 8. About (`about.html`)

- Mission, vision, and values
- What we do vs. what we don't do
- Privacy and safety policies
- Listener training information
- Legal disclaimers

## ♿ Accessibility Features

- **Keyboard Navigation:** Full keyboard support with visible focus indicators
- **Screen Reader Support:** Semantic HTML and ARIA labels
- **High Contrast Mode:** Enhanced visibility for low vision users
- **Reduced Motion:** Respects `prefers-reduced-motion` setting
- **Text Scaling:** Responsive text sizes and flexible layouts
- **Color Blind Support:** Patterns and shapes in addition to colors

## 🖨️ Print Support

- **Resource Packs:** Crisis contacts, grounding exercises, self-care tips
- **Session Summaries:** Tips discussed, resource links (no transcripts)
- **Clean Layout:** Optimized for black and white printing
- **No Interactive Elements:** Buttons and forms hidden in print

## 🎭 Theme System

### Available Themes

1. **Light Theme** (Default)

   - Clean, professional appearance
   - High contrast text on light backgrounds

2. **Dark Theme**

   - Reduced eye strain in low light
   - Dark backgrounds with light text

3. **High Contrast Theme**

   - Maximum contrast for accessibility
   - Bold borders and enhanced focus indicators

4. **Reduced Motion Theme**
   - Disables animations and transitions
   - Respects user motion preferences

### Theme Switching

- Visual theme toggle in header
- System preference detection
- Persistent theme selection
- Smooth transitions between themes

## 🚨 Safety & Crisis Support

### Crisis Detection

- Prominent crisis buttons throughout the interface
- Crisis modal with emergency resources
- Immediate escalation pathways
- Clear boundaries between peer support and crisis intervention

### Safety Tools

- Report/flag functionality
- Moderation dashboard for safety monitoring
- Clear scope limitations
- Resource quick-access sidebar

## 🔒 Privacy & Anonymity

### Privacy Features

- No personal information collection
- Anonymous pseudonyms (e.g., "Seeker-Sky", "Listener-Willow")
- No registration required
- Session data not permanently stored
- Clear privacy policies and data handling

### Anonymity Controls

- Pseudonym regeneration
- Hide typing indicators
- Auto-delete session history
- Opt-out of analytics

## 🛠️ Technical Implementation

### CSS Architecture

- **BEM Methodology:** Consistent naming convention
- **CSS Custom Properties:** Theme variables and design tokens
- **Mobile-First:** Responsive design starting from mobile
- **Progressive Enhancement:** Works without JavaScript

### Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- CSS Grid and Flexbox support
- CSS Custom Properties support
- Print media query support

## 🚀 Getting Started

1. **Clone or download** the project files
2. **Open `index.html`** in a web browser
3. **Navigate** through the different pages to explore features
4. **Test themes** using the theme toggle in the header
5. **Try print styles** by printing the resources page

## 🔮 Future Enhancements

### Phase 2 (JavaScript Integration)

- Real-time chat with WebSocket/WebRTC
- Queue and matching system
- User authentication and session management
- Moderation tools and reporting system

### Phase 3 (Advanced Features)

- Crisis keyword detection
- Listener training modules
- Multilingual support
- Mobile app development
- Analytics and insights dashboard

### Phase 4 (AI & ML)

- Automated moderation assistance
- Sentiment analysis
- Crisis detection algorithms
- Personalized resource recommendations

## 📋 Acceptance Criteria (V1)

✅ **Home page** shows scope, crisis banner, and two CTAs  
✅ **Support flow** renders consent, mood check-in, queue, and session room  
✅ **Session room** includes chat bubbles, typing indicator, and safety toolbar  
✅ **Listener console** displays availability and incoming requests  
✅ **Moderation** shows reports queue with severity chips and triage columns  
✅ **Resources** surfaces immediate help and supportive exercises  
✅ **Print stylesheet** outputs clean resource packs  
✅ **Accessibility** passes baseline a11y requirements

## 📄 License & Disclaimers

### Medical Disclaimer

This service provides **peer support only** and is not a substitute for:

- Professional mental health care
- Medical advice or diagnosis
- Crisis intervention services
- Therapy or counseling

### Crisis Situations

If you're in immediate danger or having thoughts of self-harm, please contact:

- Emergency services (911/112)
- National crisis hotlines
- Local mental health crisis centers

### Privacy Policy

- No personal information is collected or stored
- Conversations are anonymous and confidential
- Anonymous usage data may be collected for safety monitoring only

## 🤝 Contributing

This is a prototype for demonstration purposes. For production use, additional considerations include:

- Security audit and penetration testing
- Legal compliance review
- Professional mental health consultation
- User testing and feedback integration
- Performance optimization
- Scalability planning

---

**Built with ❤️ for mental health support and accessibility**

_Last updated: January 2024_
