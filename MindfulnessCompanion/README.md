# Mindfulness Companion

A **static HTML + CSS v1 prototype** for a calm, guided mindfulness experience that offers meditation sessions, breathing exercises, and stress-level tracking. V1 is **JavaScript-free**—all timers, audio, sensors, and analytics are **visual placeholders** you can wire up later.

## 🌟 Vision & Goals

- Help users reduce stress via **short, guided practices** they can do anywhere
- Provide **gentle structure**: daily plan, quick breathing, and longer meditations
- Show **stress trends** with compassionate language—not guilt
- Deliver **accessible, responsive, printable** UI scaffolding that's easy to enhance later

## 🚀 Features

### Core Functionality

- **Home / Today** — Quick start tiles, daily plan, gentle nudge
- **Meditate** — Session catalog with themes and durations
- **Breathe** — Breathing patterns library and visual coach
- **Check-in** — Stress & mood entry with body awareness
- **Insights** — Trends, stats, and progress tracking
- **Library** — Meditation scripts and soundscapes
- **Settings** — Customization and accessibility options
- **About** — Information and compassionate guidance

### Design System

- **Light/Dark/High-Contrast** themes
- **Responsive design** for all devices
- **Accessibility-first** approach
- **Print-friendly** styles for reflection reports
- **BEM methodology** for clean, maintainable CSS

## 📁 Project Structure

```
MindfulnessCompanion/
├── index.html              # Home / Today page
├── meditate.html           # Meditation sessions
├── breathe.html            # Breathing coach
├── checkin.html            # Stress & mood check-in
├── insights.html           # Progress insights
├── library.html            # Scripts & resources
├── settings.html           # App customization
├── about.html              # Information & help
├── styles/
│   ├── tokens.css          # Design system variables
│   ├── base.css            # CSS reset & base styles
│   ├── utilities.css       # Utility classes
│   ├── components.css      # UI components
│   ├── layouts.css         # Page layouts
│   ├── themes.css          # Theme switching
│   └── print.css           # Print styles
└── README.md               # This file
```

## 🎨 Design System

### Colors

- **Primary**: Calm teal (#4F9A94)
- **Accent**: Gentle blue (#6C8EE7)
- **Background**: Soft mint (#F6FAF8)
- **Text**: Deep slate (#0F172A)

### Typography

- **System fonts** for optimal performance
- **Generous line-height** (1.5–1.7)
- **Accessible font sizes** with responsive scaling

### Spacing

- **4px base unit** with consistent scale
- **Generous whitespace** for calm, uncluttered feel
- **Responsive margins** that adapt to screen size

## 🚀 Getting Started

### Prerequisites

- Any modern web browser
- No build tools or dependencies required

### Installation

1. Clone or download this repository
2. Open `index.html` in your browser
3. Navigate through the different sections

### Development

- All files are ready to use as-is
- CSS is organized in logical layers
- HTML follows semantic best practices
- Easy to customize and extend

## 🔧 Customization

### Adding New Pages

1. Copy an existing HTML file
2. Update the navigation and content
3. Add any new CSS classes to `components.css`

### Modifying Styles

- **Design tokens**: Edit `tokens.css` for global changes
- **Components**: Modify `components.css` for UI updates
- **Layouts**: Adjust `layouts.css` for structural changes
- **Themes**: Update `themes.css` for new color schemes

### Adding JavaScript

- The HTML structure is ready for JavaScript enhancement
- Form elements have proper names and IDs
- Interactive components can be easily wired up

## 📱 Responsive Design

### Breakpoints

- **Mobile**: < 640px
- **Tablet**: 640px - 1024px
- **Desktop**: > 1024px

### Mobile-First Approach

- Sidebar collapses to top navigation on mobile
- Grid layouts adapt to single column
- Touch-friendly button sizes
- Optimized spacing for small screens

## ♿ Accessibility Features

### Built-in Support

- **Semantic HTML** with proper landmarks
- **ARIA labels** and roles
- **Keyboard navigation** support
- **Screen reader** friendly
- **High contrast** theme option
- **Reduced motion** support

### WCAG Compliance

- **AA contrast ratios** for all themes
- **Focus indicators** for keyboard users
- **Alternative text** for visual elements
- **Logical tab order** throughout

## 🖨️ Print Support

### Print Styles

- **Weekly reflection reports** with clean formatting
- **Practice logs** in table format
- **Hidden navigation** for clean output
- **Optimized typography** for paper

### Print Features

- Page breaks at logical points
- Professional formatting
- All content accessible in print
- Custom headers and footers

## 🔮 Future Enhancements

### Phase 2 (JavaScript)

- Real timers and countdowns
- Audio playback for sessions
- Local storage for user data
- Interactive breathing animations

### Phase 3 (Advanced)

- HRV/sensor integration
- Adaptive practice recommendations
- Social sharing features
- Offline PWA capabilities

### Phase 4 (Professional)

- Clinician dashboard
- Progress analytics
- Export/import functionality
- Multi-user support

## 🧪 Testing

### Browser Compatibility

- **Chrome/Edge**: Full support
- **Firefox**: Full support
- **Safari**: Full support
- **Mobile browsers**: Full support

### Testing Checklist

- [ ] All pages load correctly
- [ ] Navigation works on all devices
- [ ] Print styles render properly
- [ ] Theme switching functions
- [ ] Forms are accessible
- [ ] Responsive breakpoints work

## 📚 Resources

### Mindfulness Information

- [Mindful.org](https://www.mindful.org/) - General mindfulness resources
- [UCLA Mindful Awareness Research Center](https://www.uclahealth.org/marc) - Research and practices
- [Mindful Schools](https://www.mindfulschools.org/) - Educational resources

### Development Resources

- [BEM Methodology](https://en.bem.info/) - CSS naming conventions
- [CSS Custom Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) - CSS variables
- [CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) - Modern layout system

## 🤝 Contributing

### Guidelines

- Follow the existing code structure
- Use BEM methodology for CSS
- Maintain accessibility standards
- Test across different devices
- Update documentation as needed

### Areas for Contribution

- Additional meditation scripts
- New breathing patterns
- Enhanced accessibility features
- Additional theme options
- Performance optimizations

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- **Mindfulness teachers** who inspired the compassionate approach
- **Accessibility advocates** who ensure inclusive design
- **Open source community** for tools and inspiration
- **Users** who provide feedback and suggestions

## 📞 Support

### Getting Help

- Check the **About** page for mindfulness guidance
- Review **Settings** for app customization
- Explore **Library** for practice resources

### Technical Issues

- Ensure you're using a modern browser
- Check that all CSS files are loading
- Verify file paths are correct
- Test on different devices if needed

---

**Remember**: Mindfulness is a journey, not a destination. Every moment of practice counts, no matter how small. Take care of yourself. 🌱
