# Sleep Coach - Static HTML + CSS Prototype

A **JavaScript-free v1 prototype** for a sleep coaching app that analyzes patterns, suggests bedtime routines, and offers calming music/white noise.

## 🎯 Project Goals

- Reduce bedtime friction with simple wind-down plans and soothing soundscapes
- Show sleep patterns in a friendly, non-judgmental way
- Keep UI accessible, responsive, printable, and easy to enhance later with JS/AI

## 🚀 Quick Start

1. **Clone or download** this repository
2. **Open `index.html`** in your web browser
3. **Navigate** through the different pages using the sidebar
4. **Try different themes** using the theme toggle in the sidebar
5. **Print a report** using the print button in the header

## 📁 Project Structure

```
SleepCoach/
├── index.html              # Home / Tonight page
├── planner.html            # Wind-down Planner
├── sounds.html             # Calming Music & White Noise
├── log.html                # Sleep Log
├── insights.html           # Sleep Insights & Analytics
├── settings.html           # App Settings
├── about.html              # About & Help
├── styles/
│   ├── tokens.css          # Design tokens (colors, spacing, etc.)
│   ├── base.css            # Reset and base element styles
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Reusable component styles
│   ├── layouts.css         # Page layout styles
│   ├── themes.css          # Theme variations
│   └── print.css           # Print-specific styles
└── assets/
    ├── icons/              # SVG icons (using Heroicons)
    ├── illustrations/      # Placeholder for illustrations
    └── audio-placeholders/ # Placeholder audio files
```

## 🎨 Design System

### Colors

- **Light Theme**: Calm blues and greens with high contrast
- **Dark Theme**: Deep blues with warm accents
- **High Contrast**: Black/white with blue accents for accessibility

### Typography

- **System Fonts**: Uses native system fonts for performance
- **Scale**: 12px → 28px with consistent line heights
- **Monospace**: Used for times and durations

### Components

- **BEM Methodology**: Consistent CSS naming convention
- **Responsive**: Mobile-first design with breakpoints
- **Accessible**: WCAG 2.1 AA compliant

## 📱 Features

### ✅ Implemented (v0.1)

- **Visual sleep pattern analysis** with trend charts
- **Wind-down routine planner** with customizable steps
- **Sound library** with categories (music, noise, nature)
- **Sleep log** with tags, notes, and quality ratings
- **Insights dashboard** with personalized suggestions
- **Multiple themes** (light, dark, high-contrast)
- **Print-friendly reports** for offline use
- **Responsive design** for all screen sizes
- **Keyboard navigation** and screen reader support

### 🚧 Future Enhancements

- Real-time sleep tracking via wearables
- AI-powered bedtime suggestions
- Audio playback and mixing capabilities
- Smart notifications and reminders
- Health app integrations (Apple Health, Google Fit)
- Advanced analytics and machine learning
- Social features and sharing

## 🎵 Audio Features

The app includes placeholder audio controls for:

- **Calming Music**: Piano, strings, ambient pads
- **Noise**: White, brown, and pink noise variants
- **Nature**: Rain, ocean, forest, fan sounds

_Note: Audio files are placeholders. In a real implementation, you would add actual audio files and implement custom controls._

## 🖨️ Print Support

The app includes comprehensive print styles for:

- **Weekly sleep reports** with charts and tables
- **Sleep logs** with all entries and summaries
- **Insights** with trend visualizations
- **Clean formatting** optimized for A4 paper

## ♿ Accessibility

- **WCAG 2.1 AA compliant** with proper contrast ratios
- **Keyboard navigation** for all interactive elements
- **Screen reader friendly** with semantic HTML and ARIA labels
- **High contrast theme** for visual impairments
- **Reduced motion support** for vestibular disorders
- **Focus management** with visible focus indicators

## 🔧 Technical Details

### Architecture

- **Pure HTML5 + CSS3** - No JavaScript dependencies
- **BEM CSS methodology** for maintainable styles
- **CSS Custom Properties** for theming
- **CSS Grid & Flexbox** for layouts
- **Progressive enhancement** approach

### Browser Support

- **Modern browsers** (Chrome, Firefox, Safari, Edge)
- **Mobile browsers** (iOS Safari, Chrome Mobile)
- **Graceful degradation** for older browsers

### Performance

- **System fonts** for fast loading
- **Optimized CSS** with minimal redundancy
- **No external dependencies** or CDN requests
- **Lightweight** - entire app under 100KB

## 🚀 Getting Started with Development

### Prerequisites

- A modern web browser
- A text editor or IDE
- Basic knowledge of HTML and CSS

### Development Setup

1. **Clone the repository**
2. **Open in your preferred editor**
3. **Start a local server** (optional but recommended):

   ```bash
   # Using Python
   python -m http.server 8000

   # Using Node.js
   npx serve .

   # Using PHP
   php -S localhost:8000
   ```

4. **Open `http://localhost:8000`** in your browser

### Making Changes

- **HTML**: Edit the `.html` files directly
- **CSS**: Modify the `.css` files in the `styles/` directory
- **Themes**: Update `themes.css` for new theme variations
- **Components**: Add new components to `components.css`

## 📊 Data Model (Future-Ready)

The app is designed to work with this data structure when JavaScript is added:

```javascript
// Sleep Session
{
  id: "session_123",
  date: "2024-01-15",
  bedTime: "23:15",
  wakeTime: "06:40",
  awakenings: 1,
  quality1to5: 4,
  tags: ["workout"],
  notes: "Fell asleep quickly after workout"
}

// Routine
{
  id: "routine_456",
  name: "Classic Calm",
  targetBedTime: "22:30",
  steps: [
    { title: "Lights dim", minutes: 15, enabled: true },
    { title: "Shower", minutes: 10, enabled: true }
  ]
}
```

## 🤝 Contributing

This is a prototype project, but contributions are welcome:

1. **Fork the repository**
2. **Create a feature branch**
3. **Make your changes**
4. **Test across different browsers**
5. **Submit a pull request**

### Contribution Guidelines

- Follow the existing CSS naming conventions (BEM)
- Maintain accessibility standards
- Test with different themes
- Ensure print styles work correctly
- Keep the JavaScript-free constraint for v1

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## ⚠️ Disclaimer

**This is not medical advice.** Sleep Coach is an educational tool and should not replace professional medical advice. If you have persistent sleep issues, please consult a healthcare professional.

## 🙏 Acknowledgments

- **Heroicons** for the beautiful SVG icons
- **Sleep research community** for evidence-based sleep hygiene practices
- **Accessibility community** for WCAG guidelines and best practices
- **CSS community** for modern layout techniques and design patterns

---

**Sleep Coach v0.1** - Built with ❤️ for better sleep
