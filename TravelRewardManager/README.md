# Travel Reward Manager

A **static HTML + CSS v1 prototype** for a wallet that tracks **loyalty points** across airlines, hotels, and banks; helps plan **redemptions** for flights/hotels/experiences; and visualizes **transfers, expirations, and value**.

## 🎯 Project Goals

- **Centralize** all loyalty programs in one **Points Wallet**
- Make it easy to **plan redemptions**: target trip, required points, transfer paths, estimated value
- Prevent **point loss** with expiry alerts and activity nudges
- Keep UI **semantic, accessible, responsive, and printable**

## 🚀 Features

### ✅ Implemented (V1)

- **Dashboard** with stats tiles, expirations list, and quick actions
- **Wallet** with programs & accounts (airlines, hotels, banks)
- **Program Cards** with balances, expiry bars, status chips, and program rules
- **Responsive Design** with mobile-first approach
- **Theme System** (Light, Dark, High-Contrast)
- **Print Styles** for redemption plans and statements
- **Accessibility** features (ARIA labels, keyboard navigation, focus management)

### 🔄 Planned for Future Versions

- **Trip Goals** planning and gap analysis
- **Award Finder** search and results
- **Transfer Hub** partner mappings
- **Insights** analytics and trends
- **Alerts & Deals** notifications
- **Settings** customization
- **About** documentation

## 🏗️ Architecture

### CSS Architecture (BEM Methodology)

```
styles/
├── tokens.css          # Design system variables
├── base.css           # CSS reset & base elements
├── utilities.css      # Utility classes (grid, flex, spacing)
├── components.css     # UI components (cards, buttons, forms)
├── layouts.css        # Layout structure (header, sidebar, main)
├── themes.css         # Theme variations (light, dark, high-contrast)
└── print.css          # Print-specific styles
```

### Component Examples

- `.program-card__balance` - Program card balance
- `.expiry-bar__fill--warning` - Warning state expiry bar
- `.award-card--flight` - Flight variant award card
- `.valuation-chip--good` - Good value chip
- `.transfer-tile__ratio` - Transfer ratio display

## 📱 Pages

### 1. Dashboard (`index.html`)

- **4 Stats Tiles**: Total Points, Est. Value, Expiring Soon, Trips Planned
- **Upcoming Expirations** with "Keep Alive" suggestions
- **Quick Actions**: Add Program, New Trip Goal, Award Finder

### 2. Wallet (`wallet.html`)

- **Program Tabs**: Airlines, Hotels, Banks
- **Program Cards** with:
  - Logo, name, type
  - Balance (tabular numerals)
  - Status chip (Gold, Silver, Platinum, Elite)
  - Expiry bar with visual indicators
  - Last activity information
  - Program rules (expandable)
  - View transactions button

### 3. Future Pages

- `goals.html` - Trip planning and goal setting
- `awards.html` - Award search and results
- `transfers.html` - Transfer partner mappings
- `insights.html` - Analytics and trends
- `alerts.html` - Notifications and deals
- `settings.html` - User preferences
- `about.html` - Documentation and help

## 🎨 Design System

### Colors

- **Light Theme**: Clean whites and blues (#F7FAFC, #2563EB)
- **Dark Theme**: Deep blues and grays (#0B1220, #60A5FA)
- **High Contrast**: Black and white with blue accents
- **Semantic Colors**: Success (green), Warning (orange), Danger (red), Info (blue)

### Typography

- **Font Family**: System fonts (San Francisco, Segoe UI, Roboto)
- **Scale**: 12px → 36px (xs to 4xl)
- **Tabular Numerals**: For balances and financial data

### Spacing

- **Scale**: 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px
- **Consistent**: Using CSS custom properties for maintainability

### Components

- **Cards**: Elevated surfaces with hover effects
- **Chips**: Status indicators and tags
- **Bars**: Progress indicators (expiry, gap analysis)
- **Buttons**: Primary, secondary, and variant styles
- **Forms**: Search inputs and filters

## 🔧 Technical Details

### Browser Support

- **Modern Browsers**: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+
- **CSS Features**: Grid, Flexbox, Custom Properties, CSS Grid Areas
- **Fallbacks**: Graceful degradation for older browsers

### Performance

- **No JavaScript Dependencies**: Pure HTML + CSS
- **Optimized CSS**: Efficient selectors and minimal repaints
- **Print Optimization**: Dedicated print stylesheets

### Accessibility

- **WCAG 2.1 AA** compliance target
- **Keyboard Navigation**: Full keyboard support
- **Screen Readers**: Semantic HTML and ARIA labels
- **High Contrast**: Dedicated high-contrast theme
- **Reduced Motion**: Respects user preferences

## 📖 Usage

### Getting Started

1. **Clone** the repository
2. **Open** `index.html` in a web browser
3. **Navigate** through the pages using the sidebar
4. **Print** pages using the print button or Ctrl+P

### Navigation

- **Dashboard**: Overview and quick actions
- **Wallet**: Manage loyalty programs
- **Sidebar**: Consistent navigation across all pages
- **Header**: Currency switching and print functionality

### Themes

- **Light**: Default theme (recommended for most users)
- **Dark**: Low-light environments
- **High-Contrast**: Accessibility and visibility
- **Auto**: Follows system preference

## 🚧 Development

### File Structure

```
TravelRewardManager/
├── index.html              # Dashboard
├── wallet.html             # Programs & Accounts
├── goals.html              # Trip Goals (planned)
├── awards.html             # Award Finder (planned)
├── transfers.html          # Transfer Hub (planned)
├── insights.html           # Insights (planned)
├── alerts.html             # Alerts & Deals (planned)
├── settings.html           # Settings (planned)
├── about.html              # About (planned)
├── styles/
│   ├── tokens.css          # Design tokens
│   ├── base.css            # Base styles
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Component styles
│   ├── layouts.css         # Layout styles
│   ├── themes.css          # Theme variations
│   └── print.css           # Print styles
├── assets/                 # Images, icons, etc.
└── README.md               # This file
```

### CSS Naming Convention

- **BEM (Block Element Modifier)** methodology
- **Consistent spacing** using CSS custom properties
- **Semantic class names** for clarity and maintainability

### Adding New Components

1. **Define** component in `components.css`
2. **Use BEM** naming convention
3. **Include** responsive variants
4. **Add** print styles if needed
5. **Test** across themes and screen sizes

## 🔮 Future Enhancements

### Phase 2: Interactive Features

- **JavaScript Integration**: Theme switching, form handling
- **Local Storage**: Save user preferences and data
- **Progressive Web App**: Offline support and installability

### Phase 3: Real Data

- **API Integration**: Live balance updates
- **Award Search**: Real-time availability
- **Transfer Tracking**: Live transfer status

### Phase 4: Advanced Features

- **Family Pooling**: Multi-account management
- **Trip Planning**: Calendar integration
- **Notifications**: Expiry alerts and deals

## 📄 License

This project is a prototype and demonstration of modern CSS architecture and design systems. Feel free to use as a reference for your own projects.

## 🤝 Contributing

While this is currently a static prototype, suggestions and feedback are welcome:

1. **Fork** the repository
2. **Create** a feature branch
3. **Make** your changes
4. **Test** across browsers and themes
5. **Submit** a pull request

## 📞 Support

For questions or feedback about this prototype:

- **Issues**: Use GitHub issues for bugs or feature requests
- **Discussions**: Use GitHub discussions for general questions
- **Documentation**: Check the About page (when implemented)

---

**Note**: This is a **static prototype** - all award search, transfers, and valuations are **visual placeholders** that can be wired up to real functionality in future versions.
