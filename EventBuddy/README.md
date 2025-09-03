# Event Buddy - Static HTML + CSS Prototype

> **A comprehensive event discovery and management platform built with pure HTML and CSS**

Event Buddy is a static prototype for discovering, joining, and organizing local events with ticketing and RSVP features. This v1 prototype is **JavaScript-free**—all payments, QR scanning, maps, emails, and analytics are visual placeholders that can be wired up later.

## 🎯 Project Overview

Event Buddy makes it easy to:

- **Discover** amazing local events with smart filtering
- **Join** events with easy RSVP and ticketing
- **Organize** events with comprehensive management tools
- **Check-in** attendees with QR code scanning

## 📁 Project Structure

```
EventBuddy/
├── index.html              # Home/Discover page
├── event.html              # Event detail page
├── rsvp.html               # Checkout/RSVP page
├── confirm.html            # Order confirmation
├── organizer.html          # Organizer console
├── orders.html             # Orders & check-in
├── calendar.html           # Calendar view
├── profile.html            # User profile
├── settings.html           # Settings page
├── about.html              # About page
├── styles/
│   ├── tokens.css          # Design tokens & variables
│   ├── base.css            # Reset, typography, forms
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Reusable components
│   ├── layouts.css         # Layout systems
│   ├── themes.css          # Theme management
│   └── print.css           # Print styles
└── README.md               # This file
```

## 🎨 Design System

### Color Palette

- **Light Theme**: Clean whites and blues with proper contrast
- **Dark Theme**: Dark backgrounds with accessible text colors
- **High Contrast**: Maximum accessibility for all users

### Typography

- **Display**: 28px for main headings
- **Body**: 16px for readable content
- **Tabular Numerals**: For prices and order numbers

### Components

- **Event Cards**: Consistent event display with metadata
- **Ticket Tiers**: Clear pricing and availability indicators
- **QR Placeholders**: Visual placeholders for future QR codes
- **Capacity Meters**: Visual representation of event capacity
- **Filter Chips**: Interactive filtering system

## 📱 Pages & Features

### 🏠 Home/Discover (`index.html`)

- Event discovery with smart filters
- Featured events carousel
- Category and price filtering
- Map placeholder for location-based discovery

### 🎫 Event Detail (`event.html`)

- Comprehensive event information
- Ticket tier selection with availability
- Organizer and venue details
- RSVP and ticketing functionality

### 💳 Checkout (`rsvp.html`)

- Multi-step checkout process
- Attendee information collection
- Payment method selection
- Order summary with pricing

### ✅ Confirmation (`confirm.html`)

- Order confirmation with tickets
- QR code placeholders for each ticket
- Print and wallet integration options
- Next steps and recommendations

### 🎪 Organizer Console (`organizer.html`)

- Dashboard with key metrics
- Event creation and management
- Comprehensive event form
- Event listing and status tracking

### 📊 Orders & Check-in (`orders.html`)

- Order management and tracking
- QR code check-in system
- Manual check-in functionality
- Real-time attendance tracking

### 📅 Calendar (`calendar.html`)

- Monthly calendar view
- Event indicators on dates
- Selected day event details
- Calendar navigation

### 👤 Profile (`profile.html`)

- User profile management
- Ticket history and upcoming events
- Event statistics and achievements
- Personal event journey

### ⚙️ Settings (`settings.html`)

- Account and privacy settings
- Notification preferences
- Theme and appearance options
- Payment method management

### ℹ️ About (`about.html`)

- Platform information and mission
- Community guidelines
- Safety and security policies
- Contact and support information

## 🎯 Key Features

### For Event Goers

- ✅ Smart event discovery with filters
- ✅ Easy ticket purchasing and RSVP
- ✅ Digital tickets with QR codes
- ✅ Calendar integration
- ✅ Event saving and personal lists

### For Organizers

- ✅ Comprehensive event creation tools
- ✅ Flexible ticketing with multiple tiers
- ✅ Real-time check-in management
- ✅ Analytics and insights (visual placeholders)
- ✅ Marketing and promotional tools

### Accessibility Features

- ✅ Semantic HTML structure
- ✅ Proper ARIA labels and landmarks
- ✅ Keyboard navigation support
- ✅ High contrast theme option
- ✅ Reduced motion preferences
- ✅ Screen reader compatibility

## 🖨️ Print Styles

The project includes comprehensive print styles for:

- **Tickets**: Clean, professional ticket layouts
- **Event Posters**: Marketing materials for events
- **Attendee Lists**: Check-in sheets for organizers
- **Order Confirmations**: Receipt-style layouts

## 🎨 Theme Support

- **Light Theme**: Default clean interface
- **Dark Theme**: Easy on the eyes
- **High Contrast**: Maximum accessibility
- **Reduced Motion**: For users with motion sensitivity

## 📱 Responsive Design

- **Mobile-first**: Optimized for mobile devices
- **Tablet**: Enhanced layouts for medium screens
- **Desktop**: Full-featured desktop experience
- **Print**: Optimized for printing

## 🚀 Getting Started

1. **Clone or download** the project files
2. **Open `index.html`** in your web browser
3. **Navigate** through the different pages using the sidebar
4. **Test** the responsive design on different screen sizes
5. **Print** tickets and posters to see print styles

## 🔧 Future Enhancements

This static prototype is ready for JavaScript integration:

### Phase 2: Core Functionality

- Real payment processing (UPI, Cards, PayPal)
- User authentication and profiles
- Real-time event updates
- Email notifications

### Phase 3: Advanced Features

- QR code generation and scanning
- Map integration with real locations
- Analytics and reporting
- Mobile app development

### Phase 4: Scale Features

- Multi-language support
- Advanced search and recommendations
- Community features and reviews
- API for third-party integrations

## 📋 Acceptance Criteria ✅

- [x] Discover lists ≥12 events with functional filters (visual only)
- [x] Event Detail shows tiers table, capacity meter, host & venue sections
- [x] RSVP/Checkout pages collect buyer + attendee info and show cart summary
- [x] Confirmation page displays tickets with QR placeholders and print link
- [x] Organizer Console lets you create/edit events with tiers & caps (visual)
- [x] Orders & Check-in lists attendees with check-in toggle and manual code field
- [x] Print styles output tickets, poster, and attendee list cleanly
- [x] Baseline accessibility (labels, contrast, focus) passes

## 🎉 Sample Data

The prototype includes realistic sample data:

- **Events**: Indie Night, Tech Meetup, Yoga Workshop, Food Festival
- **Ticket Tiers**: Early Bird (₹299), General (₹399), VIP (₹899)
- **Organizer Stats**: 4 upcoming events, 32 RSVPs today, 118 tickets sold
- **Attendee List**: Sample check-in data with QR placeholders

## 📞 Support

For questions about this prototype:

- **Email**: support@eventbuddy.com (placeholder)
- **Documentation**: See `about.html` for detailed information
- **Issues**: This is a static prototype - all interactions are visual placeholders

---

**Event Buddy v0.1** - Discover amazing events near you! 🎉
