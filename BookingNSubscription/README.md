# Booking & Subscription Management System

A comprehensive static HTML + CSS prototype for managing bookings, memberships, and subscriptions for multi-service businesses including gyms, salons, co-working spaces, and wellness centers.

## 🎯 Project Overview

This is a **v1 prototype** built with pure HTML and CSS (no JavaScript) that provides a complete booking and subscription management interface. All dynamic behaviors are visual placeholders that can be wired up later with JavaScript and backend integration.

## ✨ Key Features

### 📊 Dashboard

- KPI tiles with key business metrics
- Resource utilization bars
- Upcoming bookings list
- Alert notifications
- Quick action buttons

### 📅 Calendar Management

- Day/Week/Month views
- Staff and resource lanes
- Booking slot management
- Conflict detection (visual)
- Quick booking creation

### 📝 Booking Management

- Comprehensive booking forms
- Recurring booking support
- Payment integration (visual)
- Confirmation workflows
- Waitlist management

### 👥 Member Management

- Detailed member profiles
- Plan and usage tracking with visual rings
- Activity history
- Contact management
- Usage analytics

### 💳 Plans & Products

- Membership plan management
- Class pack creation
- Add-on services
- Coupon system
- Tax configuration

### 💰 Billing & Invoicing

- Invoice generation
- Payment tracking
- Failed payment handling
- Payout management
- Financial reporting

### 📈 Analytics

- Business performance metrics
- Revenue breakdowns
- Occupancy heatmaps
- Member retention cohorts
- Staff performance tracking

### ⚙️ Settings & Configuration

- Business settings
- Location management
- Booking policies
- Notification preferences
- Branding customization
- Privacy & legal compliance

## 🏗️ Architecture

### File Structure

```
/
├── index.html              # Dashboard
├── calendar.html           # Calendar views
├── bookings.html           # Booking management
├── members.html            # Member profiles
├── plans.html              # Plans & products
├── resources.html          # Resource management
├── staff.html              # Staff management
├── billing.html            # Billing & invoices
├── analytics.html          # Analytics dashboard
├── settings.html           # Settings & configuration
├── about.html              # About & documentation
├── styles/
│   ├── tokens.css          # Design tokens & CSS variables
│   ├── base.css            # Reset & typography
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Reusable components
│   ├── layouts.css         # Layout systems
│   ├── themes.css          # Theme variations
│   └── print.css           # Print styles
└── README.md               # This file
```

### CSS Architecture

The CSS follows a modular architecture with clear separation of concerns:

1. **tokens.css** - Design tokens, CSS custom properties, and theme variables
2. **base.css** - CSS reset, typography, and base element styles
3. **utilities.css** - Utility classes for spacing, layout, and common patterns
4. **components.css** - Reusable UI components (buttons, cards, badges, etc.)
5. **layouts.css** - Layout systems and page structures
6. **themes.css** - Theme variations (light, dark, high-contrast)
7. **print.css** - Print-optimized styles for invoices and reports

## 🎨 Design System

### Color Palette

- **Primary Blue**: #2563EB
- **Success Green**: #16A34A
- **Warning Orange**: #F59E0B
- **Danger Red**: #DC2626
- **Info Blue**: #3B82F6

### Typography

- **Display**: 28px, Bold
- **H1**: 24px, Semibold
- **H2**: 20px, Semibold
- **Body**: 16px, Regular
- **Mono**: 13px, Monospace

### Spacing Scale

- 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px, 96px

### Border Radius

- Small: 4px
- Medium: 6px
- Large: 8px
- Extra Large: 12px
- Full: 50%

## ♿ Accessibility Features

- **WCAG 2.1 AA Compliance**
- Keyboard navigation support
- Visible focus indicators
- High contrast mode support
- Screen reader compatibility
- Reduced motion preferences
- Semantic HTML structure
- Proper heading hierarchy
- Form labels and descriptions
- Descriptive link text
- Alt text for images

## 🖨️ Print Support

Comprehensive print styles for:

- **Invoices** - Professional invoice layouts
- **Rosters** - Staff schedules and assignments
- **Schedules** - Resource and room schedules
- **Member Statements** - Account summaries
- **Reports** - Analytics and performance reports

## 🌙 Theme Support

- **Light Theme** (default)
- **Dark Theme** - Optimized for low-light environments
- **High Contrast** - Enhanced accessibility
- **Auto Theme** - Respects system preferences

## 📱 Responsive Design

- **Desktop First** approach
- **Mobile Optimized** layouts
- **Tablet Friendly** interfaces
- **Touch-Friendly** interactions
- **Flexible Grid** systems

## 🚀 Getting Started

1. **Clone or Download** the project files
2. **Open** `index.html` in a modern web browser
3. **Navigate** through the different sections using the sidebar
4. **Test** the responsive design on different screen sizes
5. **Print** any page to see the print-optimized layouts

## 🔧 Browser Support

- **Chrome** 90+ (Recommended)
- **Firefox** 88+
- **Safari** 14+
- **Edge** 90+
- **Internet Explorer** 11 (Not supported)

## 📋 Sample Data

The system includes realistic sample data for:

- **72 bookings** across different services
- **12 staff members** with various roles
- **Multiple membership plans** and class packs
- **Resource utilization** metrics
- **Financial data** and invoices
- **Performance analytics** and KPIs

## 🎯 Use Cases

Perfect for:

- **Fitness Centers** - Gym memberships and class bookings
- **Beauty Salons** - Appointment scheduling and service packages
- **Co-working Spaces** - Desk and meeting room reservations
- **Wellness Centers** - Therapy sessions and wellness programs
- **Multi-service Businesses** - Combined service offerings

## 🔮 Future Enhancements

When ready to add JavaScript and backend integration:

- **Real Payment Processing** (Stripe, Razorpay)
- **Calendar Integration** (Google Calendar, Outlook)
- **SMS/Email Notifications** (Twilio, SendGrid)
- **Mobile App** (React Native, Flutter)
- **API Integration** (RESTful APIs)
- **Real-time Updates** (WebSockets)
- **Advanced Analytics** (Charts.js, D3.js)
- **Multi-language Support**
- **Advanced Reporting** (PDF generation)

## 📄 License

This project is a prototype/demo system. Please ensure compliance with your local regulations and business requirements when implementing payment processing and data handling.

## 🤝 Contributing

This is a static prototype. For production use, consider:

- Adding JavaScript for interactivity
- Implementing backend APIs
- Adding database integration
- Implementing user authentication
- Adding real payment processing
- Enhancing security measures

## 📞 Support

For questions about this prototype:

- Review the `about.html` page for detailed system information
- Check the `settings.html` page for configuration options
- Examine the CSS files for styling customization

---

**Note**: This is a visual prototype. All booking confirmations, payment processing, and data persistence are simulated for demonstration purposes.
