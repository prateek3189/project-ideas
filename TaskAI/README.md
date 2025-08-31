# TaskAI - Voice-Driven To-Do List (v1.0)

> **A static HTML & CSS prototype of a voice-driven task management app focused on hands-free productivity.**

🎯 **Live Demo**: Open `index.html` in your browser to explore the app.

---

## 🚀 Overview

TaskAI is a **voice-driven to-do list application** designed for busy professionals, students, and families who need to capture, organize, and manage tasks hands-free. This v1.0 prototype focuses on **UI scaffolding and design patterns** using pure HTML and CSS, with placeholders for future voice recognition and AI features.

### ✨ Key Features

- **🎤 Voice Input Interface** - Visual placeholders for hands-free task creation
- **📱 Responsive Design** - Works seamlessly across desktop, tablet, and mobile
- **🌙 Dark/Light Themes** - Automatic theme switching with system preference support
- **♿ Accessibility First** - WCAG AA compliant with screen reader support
- **🖨️ Print-Friendly** - Clean print layouts for task lists and reminders
- **📊 Smart Organization** - Priority levels, tags, and due date management
- **⏰ Reminder System** - Visual notification and scheduling interface
- **🔄 Cross-Device Sync** - UI placeholders for future cloud synchronization

---

## 📁 Project Structure

```
TaskAI/
├── index.html              # Dashboard - Main task view
├── add-task.html           # Task creation with voice and manual input
├── reminders.html          # Reminder management and scheduling
├── settings.html           # User preferences and configuration
├── about.html              # Mission, features, and roadmap
├── styles/
│   ├── main.css           # Main stylesheet (imports all others)
│   ├── tokens.css         # Design system tokens and variables
│   ├── base.css           # Reset and base styling
│   ├── utilities.css      # Atomic utility classes
│   ├── components.css     # Reusable UI components
│   ├── layouts.css        # Page layouts and responsive design
│   ├── themes.css         # Theme variations and customizations
│   └── print.css          # Print-specific styling
├── assets/
│   └── icons/             # Icon assets (placeholder directory)
└── README.md              # Project documentation
```

---

## 🎨 Design System

### Color Palette

- **Primary**: Blue (#3b82f6) - Actions and interactive elements
- **Surface**: Light gray (#f8fafc) - Cards and panels
- **Priority Colors**:
  - High: Red (#ef4444)
  - Medium: Amber (#f59e0b)
  - Low: Green (#22c55e)

### Typography

- **Font Family**: System font stack (-apple-system, BlinkMacSystemFont, 'Segoe UI', etc.)
- **Sizes**: 12px, 14px, 16px, 18px, 20px, 24px, 30px
- **Weights**: Normal (400), Medium (500), Semibold (600), Bold (700)

### Spacing & Layout

- **Spacing Scale**: 4px, 8px, 12px, 16px, 20px, 24px, 32px, 40px, 48px, 64px, 80px
- **Border Radius**: 4px, 8px, 12px, 16px, 9999px (full)
- **Breakpoints**: Mobile (≤480px), Tablet (768px), Desktop (1024px)

---

## 🏗️ Architecture

### CSS Organization (ITCSS-inspired)

1. **Tokens** - Design system variables and custom properties
2. **Base** - Normalize, resets, and element defaults
3. **Utilities** - Atomic classes for rapid development
4. **Components** - Self-contained UI components
5. **Layouts** - Page structure and responsive grid
6. **Themes** - Theme variations and overrides
7. **Print** - Print-specific styles

### Component Library

- **Buttons**: Primary, secondary, ghost, icon variants
- **Cards**: Task cards, reminder cards, info panels
- **Forms**: Inputs, selects, textareas with validation states
- **Navigation**: Sidebar nav, filter tabs, breadcrumbs
- **Badges**: Priority, status, and tag indicators
- **Voice Capture**: Microphone interface with listening states
- **Toggle Switches**: For settings and preferences

---

## 📱 Pages & Features

### 🏠 Dashboard (`index.html`)

- Voice capture interface with listening animation
- Task list with interactive checkboxes (visual only)
- Priority badges and tag system
- Filter tabs (All, Today, This Week, Completed)
- Quick statistics cards

### ➕ Add Task (`add-task.html`)

- Voice input placeholder with visual feedback
- Comprehensive manual task creation form
- Priority selection and tag management
- Due date/time picker
- Reminder configuration
- Voice command examples and tips

### ⏰ Reminders (`reminders.html`)

- Upcoming reminder cards with timing
- Cross-device sync status indicator
- Snooze and completion actions (visual)
- Reminder statistics and insights
- Smart feature previews

### ⚙️ Settings (`settings.html`)

- Profile management
- Device synchronization toggles
- Voice recognition preferences
- Notification settings with quiet hours
- Theme and accessibility options
- Data export and privacy controls

### ℹ️ About (`about.html`)

- Mission statement and value proposition
- Current feature showcase
- Future AI-powered roadmap
- Technology stack information
- Contact and support details

---

## ♿ Accessibility Features

- **Semantic HTML**: Proper heading hierarchy, landmarks, and roles
- **Screen Reader Support**: ARIA labels, descriptions, and live regions
- **Keyboard Navigation**: Full keyboard accessibility with visible focus
- **High Contrast**: Support for prefers-contrast media query
- **Reduced Motion**: Respects prefers-reduced-motion preferences
- **Color Independence**: Information not conveyed by color alone
- **Text Alternatives**: All icons have appropriate labels

---

## 🖨️ Print Optimization

- Hides interactive elements (buttons, toggles, navigation)
- Converts badges to text prefixes
- Optimizes typography for print (12pt base)
- Adds page break controls
- Shows URLs for external links
- Simplified black and white layout

---

## 🌍 Browser Support

- **Modern Browsers**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **CSS Features**: Custom properties, Grid, Flexbox, CSS filters
- **Responsive**: Works across all screen sizes (320px to 2560px+)
- **Progressive Enhancement**: Graceful degradation for older browsers

---

## 🚀 Getting Started

1. **Clone or Download** the project files
2. **Open `index.html`** in your web browser
3. **Navigate** between pages using the sidebar
4. **Test Responsiveness** by resizing your browser window
5. **Try Print Preview** to see the print-optimized layout
6. **Test Accessibility** with a screen reader or keyboard navigation

### Development Workflow

```bash
# No build process required - pure HTML/CSS
# Simply edit files and refresh browser

# For live development, use any local server:
python -m http.server 8000
# or
npx serve .
# or
php -S localhost:8000
```

---

## 🔮 Future Roadmap

### Phase 2: Interactive JavaScript (Q1 2024)

- [ ] Web Speech API integration
- [ ] Local storage for task persistence
- [ ] Interactive form validation
- [ ] Theme switching functionality
- [ ] Filter and search implementation

### Phase 3: PWA & Offline (Q2 2024)

- [ ] Service Worker for offline functionality
- [ ] App manifest for installability
- [ ] IndexedDB for robust local storage
- [ ] Background sync capabilities
- [ ] Push notifications

### Phase 4: AI & Cloud (Q3-Q4 2024)

- [ ] Natural language processing for voice commands
- [ ] Smart task prioritization
- [ ] Location-based reminders
- [ ] Calendar integration
- [ ] Real-time cloud synchronization
- [ ] Productivity analytics

---

## 🤝 Contributing

This is currently a prototype project. For future development:

1. **Feedback**: Share ideas via GitHub issues
2. **Bug Reports**: Document any UI/UX issues
3. **Design Improvements**: Suggest accessibility or usability enhancements
4. **Code Quality**: Help improve CSS organization and performance

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

---

## 📞 Support

- **Documentation**: This README and inline code comments
- **Issues**: GitHub Issues for bugs and feature requests
- **Email**: support@taskai.app (placeholder)
- **Community**: Future Discord/Slack community

---

## 🙏 Acknowledgments

- **Design Inspiration**: Modern task management apps and voice interfaces
- **Accessibility**: WCAG guidelines and inclusive design principles
- **Typography**: System font stacks for optimal performance
- **Icons**: Emoji used for universal compatibility

---

**TaskAI v1.0** - Built with ❤️ for hands-free productivity

_This prototype demonstrates the UI/UX foundation for a future voice-driven productivity platform._
