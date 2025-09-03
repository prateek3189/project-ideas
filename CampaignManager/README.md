# Campaign Manager - Static HTML + CSS Prototype

A comprehensive marketing campaign management platform built with vanilla HTML and CSS. This is a v1 prototype that demonstrates the complete user experience for creating, scheduling, and tracking email and SMS marketing campaigns.

## 🎯 Project Overview

Campaign Manager is designed to provide an end-to-end flow for marketing teams: **Brief → Audience → Content → Schedule → Review → Track**. The platform supports both Email and SMS campaigns with templates, A/B testing, UTM building, and visual journey automation.

## ✨ Key Features

### Core Functionality

- **Campaign Creation Wizard** - 5-step process for building campaigns
- **Audience Management** - Segment contacts and manage suppression lists
- **Template Library** - Pre-built email and SMS templates with blocks
- **Journey Builder** - Visual automation workflows with triggers and delays
- **Performance Reports** - Detailed analytics with A/B test results
- **Compliance Tools** - Built-in consent management and opt-out handling

### Design System

- **Responsive Design** - Works on all device sizes
- **Accessibility** - WCAG 2.1 AA compliant with proper ARIA labels
- **Print Support** - Optimized print styles for reports and briefs
- **Theme Support** - Light, dark, and high-contrast themes
- **Component Library** - Reusable UI components with BEM methodology

## 📁 Project Structure

```
CampaignManager/
├── index.html              # Dashboard
├── campaigns.html          # Campaign list
├── campaign-new.html       # Campaign creation wizard
├── reports.html            # Performance reports
├── journeys.html           # Journey builder
├── audiences.html          # Audience management
├── templates.html          # Template library
├── assets.html             # Asset management
├── settings.html           # Configuration
├── about.html              # About page
├── styles/
│   ├── tokens.css          # Design tokens
│   ├── base.css            # Reset and fundamentals
│   ├── utilities.css       # Utility classes
│   ├── components.css      # UI components
│   ├── layouts.css         # Page layouts
│   ├── themes.css          # Theme variations
│   └── print.css           # Print styles
└── README.md
```

## 🎨 Design System

### Color Palette

- **Primary**: #2563EB (Blue)
- **Success**: #16A34A (Green)
- **Warning**: #F59E0B (Orange)
- **Danger**: #DC2626 (Red)
- **Email**: #8B5CF6 (Purple)
- **SMS**: #10B981 (Teal)

### Typography

- **Font Family**: Inter (system font stack)
- **Scale**: 12px to 36px with consistent line heights
- **Tabular Numbers**: For rates and counts

### Spacing & Layout

- **Grid System**: CSS Grid with responsive breakpoints
- **Spacing Scale**: 4px base unit (4, 8, 12, 16, 24, 32px)
- **Border Radius**: 4px to 16px with full radius for pills

## 🚀 Getting Started

1. **Clone or Download** the project files
2. **Open** `index.html` in a web browser
3. **Navigate** through the different pages using the sidebar
4. **Test** the responsive design by resizing your browser
5. **Print** any page to see the print-optimized layouts

## 📱 Pages Overview

### Dashboard (`index.html`)

- KPI tiles showing campaign performance metrics
- Recent campaigns table with status indicators
- Alerts for domain authentication and bounce rates

### Campaign Wizard (`campaign-new.html`)

- **Step 1**: Campaign brief and objectives
- **Step 2**: Audience selection with filters
- **Step 3**: Content creation (email builder, SMS composer, UTM tracking)
- **Step 4**: Scheduling and compliance checks
- **Step 5**: Review and approval workflow

### Reports (`reports.html`)

- Performance overview with key metrics
- Trend charts showing engagement over time
- Link performance with click share analysis
- A/B test results with winner selection
- Device and client breakdowns

### Journeys (`journeys.html`)

- Visual journey builder with drag-and-drop nodes
- Trigger, delay, email, SMS, branch, and exit nodes
- Journey statistics and completion rates
- Configuration panels for each node type

### Audiences (`audiences.html`)

- Audience segments with size estimates
- Suppression list management
- Segment creation with filters
- Consent management and compliance tracking

### Templates (`templates.html`)

- Email templates with preview
- SMS templates with character counting
- Reusable email blocks
- Content guidelines and best practices

### Assets (`assets.html`)

- Image upload and management
- Brand kit with colors and typography
- Logo variations and guidelines
- Document storage and organization

### Settings (`settings.html`)

- Email and SMS channel configuration
- Provider integrations (SendGrid, Twilio)
- Tracking and UTM settings
- Compliance and team management

## 🎯 Compliance Features

### Email Compliance

- **CAN-SPAM Act**: Automatic unsubscribe links and sender identification
- **Physical Address**: Required in email footers
- **Domain Authentication**: SPF, DKIM, DMARC status indicators

### SMS Compliance

- **TCPA**: Express consent tracking and opt-out mechanisms
- **Quiet Hours**: Automatic enforcement of send time restrictions
- **Unsubscribe Keywords**: Configurable opt-out terms

### Data Protection

- **GDPR**: Consent management and right to be forgotten
- **Data Retention**: Configurable retention periods
- **Audit Logs**: Compliance tracking and reporting

## 🔧 Technical Implementation

### CSS Architecture

- **Design Tokens**: Centralized color, spacing, and typography variables
- **BEM Methodology**: Block-Element-Modifier naming convention
- **Utility Classes**: Atomic CSS for rapid development
- **Component Library**: Reusable UI components
- **Responsive Design**: Mobile-first approach with breakpoints

### Accessibility

- **Semantic HTML**: Proper heading hierarchy and landmarks
- **ARIA Labels**: Screen reader support
- **Keyboard Navigation**: Full keyboard accessibility
- **Color Contrast**: WCAG AA compliant color combinations
- **Focus Management**: Visible focus indicators

### Print Optimization

- **Print Styles**: Dedicated CSS for printing
- **Page Breaks**: Proper content flow for reports
- **Black & White**: Optimized for monochrome printing
- **Page Numbers**: Automatic pagination

## 🚧 Limitations (V1 Prototype)

This is a static prototype with the following limitations:

- **No JavaScript**: All interactions are visual placeholders
- **No Backend**: No real data persistence or API integrations
- **No Real Sending**: Email/SMS sending is simulated
- **No Analytics**: Performance data is mock data
- **No User Authentication**: No login or user management

## 🔮 Future Enhancements

### Phase 2 Features

- Real SMTP/SMS gateway integrations
- Contact import and list management
- Live analytics and reporting
- User authentication and roles
- API for custom integrations

### Phase 3 Features

- AI-powered content suggestions
- Advanced segmentation rules
- Multi-workspace support
- White-label customization
- Mobile app companion

## 📄 License

This project is a demonstration prototype. All data shown is fictional and for display purposes only.

## 🤝 Contributing

This is a prototype project. For production use, consider:

- Adding JavaScript for interactivity
- Implementing backend services
- Adding real data persistence
- Integrating with email/SMS providers
- Adding user authentication

## 📞 Support

For questions about this prototype:

- Review the code comments for implementation details
- Check the `about.html` page for methodology information
- Refer to the design system in `styles/tokens.css`

---

**Campaign Manager v0.1** - A comprehensive marketing campaign management platform prototype built with HTML and CSS.
