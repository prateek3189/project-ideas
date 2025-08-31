# AI Nutrition Guide - Static HTML & CSS Prototype

A comprehensive nutrition tracking application prototype built with **static HTML and CSS only**, demonstrating the user experience and interface design for an AI-powered nutrition guide.

## 🚀 Overview

AI Nutrition Guide is designed to help users make better food choices through intelligent meal recognition, personalized recommendations, and detailed nutritional insights. This prototype demonstrates the core functionality using visual placeholders and static data.

## ✨ Key Features

- **📸 Photo Recognition Placeholders** - Visual representation of AI meal identification
- **🔄 Smart Food Swaps** - Healthier alternative suggestions with explanations
- **📊 Comprehensive Tracking** - Calories, macros, vitamins, and minerals
- **🔗 Fitness App Integration** - Visual sync status with popular health apps
- **🎨 Multiple Themes** - Light, dark, and high-contrast modes
- **📱 Responsive Design** - Mobile-first approach with desktop optimization
- **♿ Accessibility** - Built with accessibility best practices
- **🖨️ Print Styles** - Clean, printable reports and summaries

## 🛠️ Technical Stack

- **HTML5** - Semantic markup with native patterns
- **CSS3** - Modern CSS with custom properties and Grid/Flexbox
- **Vanilla JavaScript** - Minimal JS for UI enhancements only
- **BEM Methodology** - CSS naming convention for maintainability
- **CSS Architecture** - Layered approach with tokens, base, utilities, components, layouts, themes, and print

## 📁 Project Structure

```
AINutritionGuide/
├── index.html              # Dashboard (main page)
├── onboarding.html         # User setup and preferences
├── log-meal.html          # Meal logging with photo upload
├── food.html              # Food details and swap suggestions
├── diary.html             # Daily food diary
├── insights.html          # Nutrition insights and analytics
├── integrations.html      # Fitness app connections
├── settings.html          # User preferences and account
├── about.html             # App information and help
├── styles/
│   ├── tokens.css         # Design system variables
│   ├── base.css           # Reset and base styles
│   ├── utilities.css      # Utility classes
│   ├── components.css     # UI component styles
│   ├── layouts.css        # Page and layout structures
│   ├── themes.css         # Theme management
│   └── print.css          # Print-specific styles
└── README.md              # This file
```

## 🚀 Getting Started

### Prerequisites

- Modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- Local web server (optional, for development)

### Installation

1. **Clone or download** the project files
2. **Open `index.html`** in your web browser
3. **Navigate** through the different pages using the sidebar

### Development Setup

For the best development experience, serve the files through a local web server:

```bash
# Using Python 3
python -m http.server 8000

# Using Node.js (if you have http-server installed)
npx http-server

# Using PHP
php -S localhost:8000
```

Then open `http://localhost:8000` in your browser.

## 🎯 Core Functionality

### 1. Dashboard (`index.html`)

- Overview of daily nutrition progress
- Quick action buttons for common tasks
- Recent meals and hydration tracking
- Macro balance visualization

### 2. Meal Logging (`log-meal.html`)

- Photo upload interface (visual placeholder)
- AI recognition results display
- Portion adjustment tools
- Meal categorization and notes

### 3. Food Details (`food.html`)

- Comprehensive nutrition facts
- Healthier alternative suggestions
- Portion size recommendations
- Nutritional comparison charts

### 4. Daily Diary (`diary.html`)

- Organized meal sections
- Nutritional summaries
- Progress tracking
- Print-friendly format

### 5. Insights (`insights.html`)

- Weekly and monthly trends
- Achievement badges
- Macro balance analysis
- Personalized recommendations

### 6. Integrations (`integrations.html`)

- Fitness app connections
- Data sync status
- Privacy controls
- Troubleshooting guides

### 7. Settings (`settings.html`)

- User preferences
- Nutrition goals
- Dietary restrictions
- Privacy and data management

### 8. About (`about.html`)

- App information
- Privacy policy
- Help and support
- FAQ section

## 🎨 Design System

### Color Themes

- **Light Theme** - Clean, modern interface
- **Dark Theme** - Easy on the eyes in low-light
- **High-Contrast Theme** - Enhanced accessibility

### Typography

- **Primary Font** - System fonts for optimal performance
- **Font Sizes** - Responsive scale from 12px to 48px
- **Line Heights** - Optimized for readability

### Spacing

- **Base Unit** - 4px grid system
- **Spacing Scale** - 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px

### Components

- **Cards** - Information containers with shadows
- **Buttons** - Primary, secondary, and outline variants
- **Forms** - Accessible input elements
- **Navigation** - Sidebar with active states
- **Tables** - Data presentation with responsive design

## ♿ Accessibility Features

- **Semantic HTML** - Proper heading hierarchy and landmarks
- **Keyboard Navigation** - Full keyboard support
- **Screen Reader Support** - ARIA labels and descriptions
- **Focus Management** - Visible focus indicators
- **Color Contrast** - WCAG AA compliant color ratios
- **Alternative Text** - Descriptive text for images
- **Respectful Language** - Inclusive and clear communication

## 🖨️ Print Styles

The application includes comprehensive print styles for:

- **Daily Diaries** - Clean meal summaries
- **Weekly Reports** - Progress overviews
- **Nutrition Insights** - Data visualizations
- **Settings** - User preferences

Print styles automatically hide navigation elements and optimize layouts for paper output.

## 🔧 Customization

### Adding New Pages

1. Create new HTML file following the existing structure
2. Include all CSS files in the `<head>` section
3. Use the standard sidebar navigation
4. Follow BEM naming conventions for CSS classes

### Modifying Themes

1. Edit `styles/tokens.css` for color and spacing changes
2. Update `styles/themes.css` for theme-specific adjustments
3. Test across all three themes (light, dark, high-contrast)

### Adding Components

1. Create component styles in `styles/components.css`
2. Follow BEM methodology for class names
3. Include responsive design considerations
4. Test accessibility and print compatibility

## 🚫 Limitations (Prototype Version)

This is a **static prototype** with the following limitations:

- **No Backend** - All data is simulated/static
- **No AI Recognition** - Photo upload shows visual placeholders
- **No Data Persistence** - Changes reset on page refresh
- **No Real Integrations** - Fitness app sync is visual only
- **No User Accounts** - Single demo user experience

## 🔮 Future Enhancements

When moving to a full application:

- **Backend API** - Node.js/Python server with database
- **AI Integration** - Computer vision for food recognition
- **User Authentication** - Secure login and account management
- **Data Persistence** - Local storage and cloud synchronization
- **Real Integrations** - API connections to fitness platforms
- **Mobile Apps** - React Native or Flutter applications

## 🧪 Testing

### Browser Testing

- Test across different browsers and versions
- Verify responsive design on various screen sizes
- Check theme switching functionality
- Validate print styles

### Accessibility Testing

- Use screen readers (NVDA, JAWS, VoiceOver)
- Test keyboard-only navigation
- Verify color contrast ratios
- Check ARIA implementation

### Print Testing

- Test print styles in different browsers
- Verify page breaks and layouts
- Check color and contrast in print preview

## 📱 Responsive Design

The application is designed with a **mobile-first approach**:

- **Mobile** (< 768px) - Single column layout, collapsed sidebar
- **Tablet** (768px - 1024px) - Two column layout, expanded sidebar
- **Desktop** (> 1024px) - Full layout with persistent sidebar

## 🎯 Performance Considerations

- **CSS Optimization** - Minimal unused styles
- **Image Optimization** - Placeholder images are lightweight
- **Font Loading** - System fonts for fast rendering
- **Minimal JavaScript** - Only essential UI enhancements

## 🤝 Contributing

This is a prototype project, but contributions are welcome:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test across different browsers and devices
5. Submit a pull request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- Design inspiration from modern nutrition and fitness applications
- Accessibility guidance from WCAG 2.1 guidelines
- CSS architecture patterns from industry best practices
- Icon usage from emoji standards

## 📞 Support

For questions or feedback about this prototype:

- **Email** - feedback@ainutritionguide.com
- **Issues** - Use the project's issue tracker
- **Documentation** - Refer to the inline code comments

---

**Note**: This is a prototype version designed to demonstrate the user experience and interface design. All functionality is simulated using static HTML and CSS with minimal JavaScript for UI enhancements.
