# Sleep Coach — Static HTML + CSS Prototype

> **A beautiful, accessible sleep coaching application built with vanilla HTML and CSS**

Sleep Coach is designed to reduce bedtime friction with simple wind-down plans and soothing soundscapes. It shows your sleep patterns in a friendly, non-judgmental way, keeping the interface accessible, responsive, and easy to enhance later with JavaScript.

## 🌟 Features

### Core Functionality

- **Tonight's Sleep Plan** - Suggested bedtime with personalized wind-down routine
- **Wind-down Planner** - Customizable bedtime routines with presets
- **Sounds & Noise** - Calming music, white/brown noise, and nature sounds
- **Sleep Log** - Track daily sleep patterns and quality
- **Insights** - Weekly analysis with personalized suggestions
- **Settings** - Customizable reminders, themes, and accessibility options

### Design & Accessibility

- **Responsive Design** - Mobile-first approach with breakpoint optimization
- **Theme Support** - Light, dark, and high-contrast themes
- **Accessibility** - WCAG 2.1 AA compliance with focus management
- **Print Styles** - Optimized for printing weekly sleep reports
- **Modern CSS** - CSS Grid, Flexbox, and custom properties

## 🚀 Getting Started

### Prerequisites

- Any modern web browser
- No build tools or dependencies required

### Installation

1. Clone or download this repository
2. Open `index.html` in your web browser
3. Navigate through the different pages using the sidebar

### File Structure

```
SleepCoach/
├── index.html              # Home page (Tonight's plan)
├── planner.html            # Wind-down routine builder
├── sounds.html             # Sounds and noise library
├── log.html                # Sleep logging and tracking
├── insights.html           # Sleep analysis and insights
├── settings.html           # App configuration
├── about.html              # Information and help
├── styles/                 # CSS files
│   ├── tokens.css          # Design system variables
│   ├── base.css            # Base styles and reset
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Component styles
│   ├── layouts.css         # Layout and grid systems
│   ├── themes.css          # Theme variants
│   └── print.css           # Print styles
└── assets/                 # Placeholder directories
    ├── icons/
    ├── illustrations/
    └── audio-placeholders/
```

## 🎨 Design System

### Color Palette

- **Primary**: #5B7BD5 (Calm blue)
- **Secondary**: #7AC3B2 (Soft teal)
- **Warning**: #F59E0B (Amber)
- **Success**: #10B981 (Green)
- **Error**: #EF4444 (Red)

### Typography

- **Font Family**: System fonts (San Francisco, Segoe UI, etc.)
- **Scale**: 12px → 28px with consistent ratios
- **Line Heights**: 1.2 (headings) to 1.7 (body text)

### Spacing

- **Base Unit**: 4px
- **Scale**: 4, 8, 12, 16, 24, 32, 48, 64, 80px
- **Consistent margins and padding throughout**

### Components

- **Cards** - Content containers with subtle shadows
- **Buttons** - Primary, secondary, and outline variants
- **Forms** - Accessible input fields and controls
- **Tiles** - Metric displays with large numbers
- **Tags** - Color-coded labels for categorization
- **Badges** - Achievement and status indicators

## 📱 Responsive Design

### Breakpoints

- **Mobile**: < 640px
- **Tablet**: 640px - 1024px
- **Desktop**: > 1024px

### Mobile-First Approach

- Base styles for mobile devices
- Progressive enhancement for larger screens
- Touch-friendly interface elements
- Optimized navigation for small screens

## ♿ Accessibility Features

### WCAG 2.1 AA Compliance

- **Semantic HTML** - Proper heading hierarchy and landmarks
- **Focus Management** - Visible focus indicators
- **Screen Reader Support** - ARIA labels and descriptions
- **Keyboard Navigation** - Full keyboard accessibility
- **Color Contrast** - Meets AA contrast requirements

### Additional Features

- **Reduced Motion** - Respects user preferences
- **High Contrast** - Enhanced visibility theme
- **Font Scaling** - Adjustable text sizes
- **Dyslexia Support** - Optional dyslexia-friendly fonts

## 🖨️ Print Styles

### Weekly Sleep Report

- Clean, professional layout
- All navigation elements hidden
- Optimized typography for printing
- Page breaks handled appropriately
- Includes summary statistics and charts

### Print Features

- **Header** - App name and date range
- **Summary** - Key metrics and totals
- **Data Table** - Nightly sleep records
- **Charts** - Visual representations of patterns
- **Suggestions** - Personalized recommendations

## 🔧 Customization

### Themes

The app supports multiple theme variants:

- **Light** - Default theme with soft colors
- **Dark** - Night-friendly dark mode
- **High Contrast** - Enhanced visibility
- **Auto** - Follows system preferences

### CSS Customization

All design tokens are defined in `styles/tokens.css`:

```css
:root {
  --color-accent: #5b7bd5;
  --space-4: 16px;
  --font-size-h1: 24px;
  /* ... more variables */
}
```

## 📊 Sample Data

The prototype includes realistic sample data to demonstrate functionality:

### Weekly Sleep Log

- **Monday**: 23:15 → 06:40 (7h 25m, Quality 4, Workout)
- **Tuesday**: 00:05 → 06:45 (6h 40m, Quality 3, Screens)
- **Wednesday**: 22:55 → 06:30 (7h 35m, Quality 4)
- **Thursday**: 23:40 → 06:20 (6h 40m, Quality 3, Late caffeine)
- **Friday**: 00:20 → 07:30 (7h 10m, Quality 4)
- **Saturday**: 23:30 → 07:00 (7h 30m, Quality 4, Workout)
- **Sunday**: 22:45 → 06:15 (7h 30m, Quality 5)

### Insights

- **Average Sleep**: 7h 12m (Target: 7h 30m)
- **Bedtime Consistency**: 43% (3/7 nights on target)
- **Sleep Debt**: 2h 06m accumulated
- **Chronotype**: Early-Intermediate

## 🚧 Future Enhancements

### Phase 2: JavaScript Functionality

- Real-time sleep tracking
- Data persistence with localStorage
- Interactive charts and graphs
- Audio playback and mixing
- Export/import functionality

### Phase 3: Advanced Features

- Machine learning insights
- Integration with health apps
- Cloud synchronization
- Social features and sharing
- Advanced analytics

### Phase 4: Mobile App

- React Native or Flutter app
- Native device integration
- Push notifications
- Offline functionality
- Wearable device support

## 🧪 Testing

### Browser Compatibility

- **Chrome** 90+ ✅
- **Firefox** 88+ ✅
- **Safari** 14+ ✅
- **Edge** 90+ ✅

### Testing Checklist

- [ ] Responsive design on all breakpoints
- [ ] Keyboard navigation works correctly
- [ ] Screen reader compatibility
- [ ] Print styles render properly
- [ ] Theme switching functions
- [ ] All links and navigation work
- [ ] Forms are accessible
- [ ] Color contrast meets standards

## 📝 Development Notes

### CSS Architecture

- **BEM Methodology** for component naming
- **CSS Custom Properties** for theming
- **Utility Classes** for common patterns
- **Component-based** organization
- **Mobile-first** responsive design

### Performance Considerations

- Minimal CSS (no frameworks)
- Efficient selectors
- Optimized media queries
- Print styles loaded separately
- No JavaScript dependencies

## 🤝 Contributing

This is a prototype project, but contributions are welcome:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Development Guidelines

- Follow the existing CSS architecture
- Maintain accessibility standards
- Test on multiple devices
- Keep the design system consistent
- Document any new components

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## ⚠️ Important Disclaimers

### Medical Disclaimer

Sleep Coach is not a medical device and does not provide medical advice, diagnosis, or treatment. Always consult with qualified healthcare professionals for medical concerns.

### Educational Purpose

This application is designed for educational and self-improvement purposes. Individual results may vary based on personal circumstances and adherence to recommendations.

### Safe Use

Sleep Coach is safe for general use. If you experience any adverse effects or have concerns about your sleep, discontinue use and consult a healthcare provider.

## 📞 Support

- **Documentation**: This README and inline code comments
- **Issues**: Report bugs or request features via GitHub
- **Questions**: Review the About page for detailed information

---

**Sleep Coach v0.1** - Built with ❤️ and modern web standards

_Last updated: January 2024_
