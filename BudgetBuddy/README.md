# Budget Buddy - Personal Finance App

> **A static HTML + CSS prototype for a personal finance app that tracks expenses automatically via SMS parsing and UPI activity**

## 🎯 Project Overview

Budget Buddy is a privacy-first personal finance application designed to make expense tracking effortless and automatic. By parsing SMS messages from banks and UPI transactions, it automatically categorizes spending and provides insights into financial habits.

## ✨ Key Features

### 🔒 Privacy-First Design

- **Local Processing Only**: All data processing happens on your device
- **No External Servers**: No personal financial information is sent to external servers
- **Complete Data Control**: You have full control over your data

### 🤖 Automatic Expense Tracking

- **SMS Parsing**: Automatically extract transaction details from bank SMS messages
- **UPI Integration**: Parse UPI transaction data and UTR references
- **CSV Import**: Upload and map transaction data from CSV files
- **Auto-Categorization**: Smart categorization based on merchant names and rules

### 📊 Rich Analytics & Insights

- **Dashboard**: Overview of spending, budgets, and financial health
- **Transaction History**: Detailed transaction list with filtering and search
- **Budget Tracking**: Category-based budget management with progress bars
- **Insights**: Spending patterns, merchant analysis, and trends
- **Recurring Detection**: Automatically identify recurring bills and subscriptions

### 🎨 Modern UI/UX

- **Responsive Design**: Works on desktop, tablet, and mobile devices
- **Dark Mode**: Light and dark theme support
- **Accessibility**: High contrast mode, reduced motion, keyboard navigation
- **Print-Friendly**: Clean layouts for printing statements and reports

## 🏗️ Technical Architecture

### CSS Architecture

The project follows a modular CSS architecture with clear separation of concerns:

```
styles/
├── tokens.css      # Design tokens (colors, spacing, typography)
├── base.css        # Reset, base elements, typography
├── utilities.css   # Utility classes (flex, grid, spacing)
├── components.css  # Reusable components (tiles, pills, bars)
├── layouts.css     # Layout structures (header, sidebar, main)
├── themes.css      # Theme variations (light, dark, high-contrast)
└── print.css       # Print-specific styles
```

### Design System

- **BEM Methodology**: Consistent naming convention for CSS classes
- **CSS Custom Properties**: Design tokens for maintainable theming
- **Responsive Grid**: Flexible layouts that adapt to different screen sizes
- **Component-Based**: Reusable UI components with consistent styling

## 📱 Pages & Features

### 1. Dashboard (`index.html`)

- Financial overview with key metrics
- Budget health indicators
- Recent transactions
- Alerts and notifications

### 2. Transactions (`transactions.html`)

- Complete transaction history
- Advanced filtering and search
- Category and merchant filtering
- Transaction details and tags

### 3. Budgets (`budgets.html`)

- Category-based budget management
- Progress bars and spending indicators
- Budget drill-down with transaction details
- Budget health overview

### 4. Insights (`insights.html`)

- Spending analysis by category and merchant
- Monthly trends and comparisons
- Recurring bills detection
- Cashflow analysis

### 5. Import (`import.html`)

- SMS message parsing interface
- UPI transaction import
- CSV file upload and mapping
- Parse preview and validation

### 6. Accounts (`accounts.html`)

- Account management (banks, cards, UPI)
- Auto-categorization rules
- Account statements
- Import status and history

### 7. Receipts (`receipts.html`)

- Receipt image management
- OCR processing (conceptual)
- Receipt-transaction linking
- Digital receipt storage

### 8. Settings (`settings.html`)

- Currency and format preferences
- Category management
- Auto-categorization rules
- Privacy and security settings
- Accessibility options

### 9. About (`about.html`)

- App overview and methodology
- Privacy policy and data handling
- Supported banks and services
- Disclaimers and version information

## 🚀 Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- No additional dependencies required

### Installation

1. Clone or download the project files
2. Open `index.html` in your web browser
3. Navigate through the different pages using the sidebar

### File Structure

```
BudgetBuddy/
├── index.html              # Dashboard (main page)
├── transactions.html       # Transaction history
├── budgets.html           # Budget management
├── insights.html          # Analytics and insights
├── import.html            # Data import interface
├── accounts.html          # Account management
├── receipts.html          # Receipt management
├── settings.html          # App settings
├── about.html             # About and help
├── styles/                # CSS files
│   ├── tokens.css
│   ├── base.css
│   ├── utilities.css
│   ├── components.css
│   ├── layouts.css
│   ├── themes.css
│   └── print.css
└── README.md              # This file
```

## 🎨 Design Features

### Color System

- **Light Theme**: Clean, modern interface with subtle shadows
- **Dark Theme**: Eye-friendly dark mode with proper contrast
- **High Contrast**: Accessibility-focused high contrast mode
- **Category Colors**: Distinct colors for different expense categories

### Typography

- **System Fonts**: Uses system fonts for optimal performance
- **Tabular Numerals**: Monospace numbers for financial data
- **Responsive Sizing**: Scales appropriately across devices

### Components

- **Stat Tiles**: Key metrics with icons and trends
- **Budget Bars**: Visual progress indicators
- **Transaction Rows**: Detailed transaction information
- **Filter Pills**: Interactive filtering interface
- **Alert Banners**: Important notifications and warnings

## 🔧 Customization

### Adding New Categories

1. Update `styles/tokens.css` with new category colors
2. Add category styles in `styles/components.css`
3. Update category options in relevant HTML pages

### Modifying Themes

1. Edit color tokens in `styles/tokens.css`
2. Adjust theme-specific styles in `styles/themes.css`
3. Test across all pages for consistency

### Adding New Pages

1. Create new HTML file following existing structure
2. Include all CSS files in the `<head>` section
3. Add navigation link in sidebar
4. Follow existing layout patterns

## 📱 Responsive Design

The app is fully responsive and works across:

- **Desktop**: Full sidebar navigation and multi-column layouts
- **Tablet**: Collapsible sidebar and adapted grid layouts
- **Mobile**: Stacked layouts and touch-friendly interfaces

## ♿ Accessibility

- **Keyboard Navigation**: Full keyboard support for all features
- **Screen Reader Support**: Proper ARIA labels and semantic HTML
- **High Contrast Mode**: Enhanced visibility for users with visual impairments
- **Reduced Motion**: Respects user preferences for motion
- **Focus Management**: Clear focus indicators and logical tab order

## 🖨️ Print Support

- **Clean Print Layouts**: Optimized for printing statements and reports
- **Hide Interactive Elements**: Removes buttons and forms from print
- **Proper Page Breaks**: Ensures content flows correctly across pages
- **Black & White Friendly**: Works well in grayscale printing

## 🔮 Future Enhancements

### Phase 2 (JavaScript Implementation)

- Real SMS parsing with regex patterns
- UPI integration and transaction sync
- CSV file processing and validation
- Local data storage with IndexedDB
- Offline functionality with service workers

### Phase 3 (Advanced Features)

- OCR for receipt processing
- Bank email parsing
- Recurring transaction detection
- Budget alerts and notifications
- Data export in multiple formats
- Multi-currency support

### Phase 4 (Mobile App)

- Native mobile applications
- Camera integration for receipt capture
- Push notifications for budget alerts
- Biometric authentication
- Cloud sync (optional)

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Contributing

This is a prototype project, but contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test across different browsers and devices
5. Submit a pull request

## ⚠️ Important Notes

### Privacy & Security

- This is a **static prototype** - no real data processing occurs
- All parsing, imports, and sync features are **visual placeholders**
- No actual SMS reading or bank integration is implemented
- All data shown is **mock data** for demonstration purposes

### Disclaimers

- This is a **proof-of-concept** and not a production-ready application
- Real implementation would require proper security measures
- Always verify financial data against official bank statements
- Consult with financial advisors for personalized advice

## 📞 Support

For questions, issues, or feature requests:

- Check the About page for detailed information
- Review the Settings page for configuration options
- All pages include help text and tooltips

---

**Budget Buddy v1.0.0** - Making personal finance tracking effortless and private.
