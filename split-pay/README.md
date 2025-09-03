# Split & Pay - Group Expense Tracker

> **A static HTML + CSS prototype for tracking group expenses, splitting bills, and settling up with friends, roommates, and teams.**

## 🎯 Project Overview

Split & Pay is a comprehensive group expense tracker designed to make bill splitting simple and fair. This v1 prototype is built entirely with static HTML and CSS, providing a complete user interface without any JavaScript functionality.

## ✨ Features

### Core Functionality (Visual Only)

- **Multiple Split Types**: Equal, shares, percentages, itemized, and weights
- **Smart Settlement Plans**: Minimized transfer calculations with payment link placeholders
- **Comprehensive Tracking**: Receipt management, categories, and member balances
- **Multi-Currency Support**: Visual support for different currencies (no real conversion)
- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Accessibility**: WCAG compliant with keyboard navigation and screen reader support

### Split Types Explained

1. **Equal Split**: Everyone pays the same amount
2. **Shares Split**: Use whole numbers for different consumption levels (e.g., 1-2-1)
3. **Percentage Split**: Split by exact percentages (must sum to 100%)
4. **Itemized Split**: Assign individual items to specific people
5. **Weights Split**: Use decimal weights for precise splitting (e.g., 0.7, 0.3)

### Payment Integration (Placeholders)

- UPI (India)
- PayPal
- Paytm
- PhonePe
- Bank transfers

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+)
- No server or build process required

### Installation

1. Clone or download this repository
2. Open `index.html` in your web browser
3. Start exploring the interface!

### File Structure

```
split-pay/
├── index.html              # Dashboard
├── group.html              # Group expenses and balances
├── add-expense.html        # Add new expense form
├── members.html            # Member management
├── receipts.html           # Receipt gallery
├── settings.html           # App settings
├── about.html              # About page
├── styles/
│   ├── tokens.css          # Design tokens
│   ├── base.css            # Base styles and reset
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Component styles
│   ├── layouts.css         # Layout styles
│   ├── themes.css          # Theme variants
│   └── print.css           # Print styles
└── README.md               # This file
```

## 🎨 Design System

### CSS Architecture

- **BEM Methodology**: Consistent naming convention for maintainable CSS
- **Design Tokens**: Centralized colors, spacing, typography, and other design values
- **Component-Based**: Reusable components with consistent styling
- **Responsive**: Mobile-first approach with breakpoints
- **Accessible**: High contrast ratios and keyboard navigation support

### Themes

- **Light Theme**: Default clean and modern appearance
- **Dark Theme**: Dark mode for low-light environments
- **High Contrast**: Enhanced contrast for accessibility
- **Print Theme**: Optimized for printing expense summaries

### Color Palette

- **Primary**: Blue (#2563EB) for actions and highlights
- **Success**: Green (#16A34A) for positive balances
- **Warning**: Red (#DC2626) for negative balances
- **Info**: Blue (#3B82F6) for informational content
- **Neutral**: Grays for text and backgrounds

## 📱 Pages Overview

### Dashboard (`index.html`)

- Overview tiles showing key metrics
- Group cards with balances and quick actions
- Nudge banners for important information

### Group Page (`group.html`)

- Tabbed interface for expenses, balances, settle up, and insights
- Detailed expense list with split breakdowns
- Member balance overview
- Settlement plan with payment buttons
- Visual charts and statistics

### Add Expense (`add-expense.html`)

- Comprehensive form for adding new expenses
- Dynamic split type panels
- Participant selection and amount calculation
- Category and receipt management

### Members (`members.html`)

- Member list with payment handles
- Statistics and balance information
- Reminder and notification settings

### Receipts (`receipts.html`)

- Grid view of uploaded receipts
- Filtering by group, category, and date
- Upload placeholder with OCR information
- Receipt statistics

### Settings (`settings.html`)

- Currency and formatting preferences
- Theme and appearance options
- Privacy and data settings
- Payment provider configuration
- Notification preferences

### About (`about.html`)

- Comprehensive documentation
- Feature explanations
- Technical details
- License information

## 🔧 Technical Details

### Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers
- Print media

### Performance

- No external dependencies
- Optimized CSS with minimal redundancy
- Fast loading with system fonts
- Print-optimized stylesheets

### Accessibility

- WCAG 2.1 AA compliant
- Keyboard navigation support
- Screen reader friendly
- High contrast mode
- Reduced motion support

## 🚧 Limitations (V1)

### What's Not Functional

- **No Calculations**: All amounts and splits are visual placeholders
- **No Data Persistence**: No storage or retrieval of actual data
- **No Payment Processing**: Payment buttons are visual only
- **No Receipt Upload**: File upload is disabled
- **No Multi-Currency**: Exchange rates are not real
- **No Notifications**: Email/SMS features are visual only

### What Works

- Complete user interface
- All form interactions
- Theme switching
- Responsive design
- Print functionality
- Navigation between pages

## 🔮 Future Enhancements

### Phase 2: JavaScript Functionality

- Real expense calculations
- Data persistence with localStorage
- Dynamic form interactions
- Basic payment link generation

### Phase 3: Advanced Features

- Receipt OCR and parsing
- Multi-currency with live rates
- Email/SMS notifications
- Import/export functionality
- Advanced analytics

### Phase 4: Production Features

- User authentication
- Cloud synchronization
- Real payment integration
- Mobile app
- API for third-party integrations

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

This is a prototype project. For production use, consider:

1. Implementing JavaScript functionality
2. Adding proper data persistence
3. Integrating with real payment providers
4. Adding user authentication
5. Implementing receipt scanning
6. Adding multi-currency support

## 📞 Support

This is a prototype project. For questions or issues:

1. Check the [About page](about.html) for detailed documentation
2. Review the code comments for implementation details
3. Consider this as a starting point for your own expense tracking app

## 🎉 Acknowledgments

- Design system inspired by modern web standards
- Icons from Unicode emoji set
- Typography using system fonts for optimal performance
- Color palette based on accessibility guidelines
- Layout patterns from established design systems

---

**Split & Pay v1.0** - Making bill splitting simple and fair, one prototype at a time.
