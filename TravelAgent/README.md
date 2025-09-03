# AI Travel Agent - Static HTML/CSS Prototype

A comprehensive travel planning application that creates personalized itineraries based on budget and preferences. This is a **static HTML + CSS v1 prototype** with no JavaScript functionality - everything dynamic is a placeholder for future implementation.

## 🎯 Project Overview

**Goal:** Build a static HTML + CSS v1 prototype for an AI travel planner that auto-generates itineraries and visually books flights, stays, and activities based on budget and preferences.

**V1 Constraints:**

- No JavaScript functionality (no live prices, availability, payments, logins, or maps)
- Everything dynamic is a placeholder
- Pure CSS for meters, charts, and interactions
- Semantic HTML with accessibility features

## 📁 Project Structure

```
/
├── index.html              # Home / Plan Trip page
├── itinerary.html          # Day-by-day itinerary view
├── bookings.html           # Flights, stays, and activities
├── budget.html             # Budget tracker and breakdown
├── collections.html        # Neighborhoods and curated spots
├── settings.html           # User preferences and customization
├── about.html              # Project information
├── styles/
│   ├── tokens.css          # Design tokens (colors, spacing, typography)
│   ├── base.css            # Reset and typography
│   ├── utilities.css       # Grid, flex, spacing utilities
│   ├── components.css      # Cards, chips, buttons, forms
│   ├── layouts.css         # Page layouts and shell
│   ├── themes.css          # Light/dark/high-contrast themes
│   └── print.css           # Print styles for itineraries
└── README.md
```

## 🚀 Features Implemented

### ✅ Core Pages

- **Home Page:** Trip form with AI plan summary and budget meter
- **Itinerary:** Day tabs, timeline blocks, transport chips, "why this" notes
- **Bookings:** Flight/hotel/activity cards with mock cart and confirmation
- **Budget:** Tiles, category bars, and money-saving tips
- **Collections:** Neighborhood cards, cafes, kid-friendly spots, sunset locations
- **Settings:** Currency, language, theme, accessibility preferences
- **About:** Project information, data sources, limitations

### ✅ Design System

- **BEM CSS methodology** with semantic class names
- **Design tokens** for consistent colors, spacing, and typography
- **Responsive design** that works on all devices
- **Accessibility features** including ARIA labels, keyboard navigation, and screen reader support
- **Print styles** for clean itinerary and ticket printing

### ✅ Components

- Trip form with chips and sliders
- Cost meter progress bars
- Timeline blocks with transport chips
- Booking cards for flights, stays, and activities
- Budget bars and category breakdowns
- Collection cards for neighborhoods and POIs
- Theme toggle and accessibility controls

### ✅ Themes & Accessibility

- **Light theme** (default)
- **Dark theme** with proper contrast
- **High contrast theme** for accessibility
- **Reduced motion** support
- **Print-optimized** layouts

## 🎨 Design System

### Colors

- **Light Theme:** Clean whites and blues with proper contrast
- **Dark Theme:** Dark backgrounds with light text
- **Category Colors:** Flights (blue), Stay (purple), Food (green), Transit (orange), Sights (cyan)

### Typography

- **Display:** 28px for main headings
- **H1:** 24px for page titles
- **H2:** 20px for section headers
- **Body:** 16px for main content
- **Caption:** 12-13px for small text
- **Tabular numbers** for prices and times

### Spacing

- **Scale:** 4/8/12/16/24/32px
- **Border radius:** 12px for cards, 999px for chips
- **Shadows:** Subtle elevation system

## 📱 Responsive Design

- **Desktop:** Full sidebar navigation and two-column layouts
- **Tablet:** Collapsible sidebar, adjusted grid layouts
- **Mobile:** Single column, touch-friendly interface
- **Print:** Optimized layouts for itinerary and ticket printing

## ♿ Accessibility Features

- **Semantic HTML** with proper landmarks and headings
- **ARIA labels** for interactive elements
- **Keyboard navigation** support
- **Screen reader** optimization
- **High contrast** mode
- **Reduced motion** preferences
- **Focus indicators** for all interactive elements

## 🖨️ Print Styles

- **Itinerary printing:** Clean day-by-day layout with times and addresses
- **Ticket printing:** Flight, hotel, and activity confirmations with QR placeholders
- **Optimized layouts:** Black text on white background, proper page breaks

## 🔧 Technical Implementation

### CSS Architecture

1. **tokens.css** - Design system variables
2. **base.css** - Reset and typography
3. **utilities.css** - Helper classes
4. **components.css** - Reusable UI components
5. **layouts.css** - Page structure
6. **themes.css** - Theme variations
7. **print.css** - Print-specific styles

### JavaScript (Minimal)

- Theme toggle functionality
- Form interactions (budget slider, chip selection)
- Tab switching
- Settings persistence (localStorage)

## 📊 Sample Data

The prototype includes realistic sample data for a 4-day Singapore trip:

- **Budget:** ₹85,000 total
- **Flights:** IndiGo with 1 stop (₹49,000)
- **Accommodation:** Hotel 81 Bugis (₹28,800)
- **Activities:** Night Safari, Gardens by the Bay, River Cruise
- **Daily breakdown:** Morning, midday, and evening activities

## 🚧 Limitations (V1)

- **No real-time data:** All prices and availability are static examples
- **No booking functionality:** Cart and checkout are visual only
- **No user accounts:** All data stored locally in browser
- **Limited destinations:** Currently focused on Singapore
- **No maps integration:** Map boxes are placeholders
- **No payment processing:** Checkout flow is mockup only

## 🔮 Future Enhancements

- Real search/booking integrations (GDS/OTAs)
- Live pricing and availability
- Map routing and navigation
- User accounts and data persistence
- Multi-city planning
- Social features and collaboration
- Mobile app development
- Offline capabilities

## 🛠️ Development

### Getting Started

1. Clone or download the project files
2. Open `index.html` in a web browser
3. Navigate through the different pages using the sidebar
4. Test responsive design by resizing the browser window
5. Try the print functionality (Ctrl/Cmd + P)

### Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari 14+, Chrome Mobile 90+)

### Customization

- Modify design tokens in `styles/tokens.css`
- Add new components in `styles/components.css`
- Update layouts in `styles/layouts.css`
- Customize themes in `styles/themes.css`

## 📄 License

This project is open source and available for educational and development purposes.

## 🤝 Contributing

This is a prototype demonstration. For production use, consider:

- Adding real API integrations
- Implementing user authentication
- Adding database persistence
- Enhancing accessibility features
- Optimizing performance

---

**AI Travel Agent v0.1** - Static HTML/CSS Prototype
Built with ❤️ for the travel planning community
