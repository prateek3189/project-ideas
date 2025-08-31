# TreeNotes Style Guide

A comprehensive style guide for consistent design and development of the TreeNotes application.

## 🎨 Design Tokens

### Colors

#### Light Theme
```css
--color-bg-primary: #ffffff      /* Main background */
--color-bg-secondary: #f8fafc    /* Secondary background */
--color-bg-tertiary: #f1f5f9     /* Tertiary background */
--color-text-primary: #1e293b    /* Primary text */
--color-text-secondary: #64748b  /* Secondary text */
--color-text-muted: #94a3b8      /* Muted text */
--color-accent-primary: #3b82f6  /* Primary accent */
```

#### Dark Theme
```css
--color-bg-primary: #0f172a      /* Main background */
--color-bg-secondary: #1e293b    /* Secondary background */
--color-bg-tertiary: #334155     /* Tertiary background */
--color-text-primary: #f8fafc    /* Primary text */
--color-text-secondary: #cbd5e1  /* Secondary text */
--color-text-muted: #64748b      /* Muted text */
--color-accent-primary: #06b6d4  /* Primary accent */
```

#### Semantic Colors
```css
--color-success: #10b981         /* Success states */
--color-warning: #f59e0b         /* Warning states */
--color-error: #ef4444           /* Error states */
--color-info: #06b6d4            /* Information states */
```

#### Tag Colors
```css
--color-tag-learning: #10b981    /* Learning content */
--color-tag-work: #3b82f6        /* Work projects */
--color-tag-personal: #8b5cf6    /* Personal notes */
--color-tag-urgent: #ef4444      /* Urgent items */
```

### Typography

#### Font Families
```css
--font-family-primary: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
--font-family-mono: 'SF Mono', Monaco, 'Cascadia Code', 'Roboto Mono', Consolas, 'Courier New', monospace;
```

#### Font Sizes
```css
--font-size-xs: 0.75rem    /* 12px - Captions */
--font-size-sm: 0.875rem   /* 14px - Small text */
--font-size-base: 1rem     /* 16px - Body text */
--font-size-lg: 1.125rem   /* 18px - Large text */
--font-size-xl: 1.25rem    /* 20px - H3 headings */
--font-size-2xl: 1.5rem    /* 24px - H1 headings */
```

#### Font Weights
```css
--font-weight-normal: 400      /* Regular text */
--font-weight-medium: 500      /* Medium emphasis */
--font-weight-semibold: 600    /* Strong emphasis */
--font-weight-bold: 700        /* Bold text */
```

### Spacing

#### Spacing Scale (8px grid)
```css
--space-1: 0.25rem   /* 4px */
--space-2: 0.5rem    /* 8px */
--space-3: 0.75rem   /* 12px */
--space-4: 1rem      /* 16px */
--space-5: 1.25rem   /* 20px */
--space-6: 1.5rem    /* 24px */
--space-8: 2rem      /* 32px */
--space-10: 2.5rem   /* 40px */
--space-12: 3rem     /* 48px */
--space-16: 4rem     /* 64px */
```

### Border Radius
```css
--radius-sm: 0.25rem   /* 4px - Small elements */
--radius-md: 0.5rem    /* 8px - Cards, buttons */
--radius-lg: 0.75rem   /* 12px - Large cards */
--radius-xl: 1rem      /* 16px - Modals */
--radius-full: 9999px  /* Pills, badges */
```

### Shadows
```css
--shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
--shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
--shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
```

## 🧩 Components

### Buttons

#### Primary Button
```css
.btn--primary {
  background-color: var(--color-accent-primary);
  color: white;
  padding: var(--space-3) var(--space-4);
  border-radius: var(--radius-md);
  font-weight: var(--font-weight-medium);
}
```

#### Secondary Button
```css
.btn--secondary {
  background-color: var(--color-bg-secondary);
  color: var(--color-text-primary);
  border: 1px solid var(--color-border-medium);
}
```

#### Ghost Button
```css
.btn--ghost {
  background-color: transparent;
  color: var(--color-text-secondary);
}
```

### Cards

#### Basic Card
```css
.card {
  background-color: var(--color-bg-primary);
  border: 1px solid var(--color-border-light);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-sm);
}
```

### Badges/Tags

#### Learning Badge
```css
.badge--learning {
  background-color: var(--color-tag-learning);
  color: white;
  padding: var(--space-1) var(--space-2);
  border-radius: var(--radius-full);
  font-size: var(--font-size-xs);
}
```

### Tree Components

#### Tree Item
```css
.tree-item__content {
  display: flex;
  align-items: center;
  gap: var(--space-2);
  padding: var(--space-2) var(--space-3);
  border-radius: var(--radius-md);
}
```

#### Tree Children Indentation
```css
.tree-item__children {
  margin-left: var(--space-6);
  padding-left: var(--space-4);
  border-left: 1px solid var(--color-border-light);
}
```

## 📏 Layout Guidelines

### Grid System

#### Dashboard Layout
```css
.dashboard__stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: var(--space-4);
}
```

#### Two Column Layout
```css
.two-column {
  display: grid;
  grid-template-columns: 1fr 320px;
  gap: var(--space-8);
}
```

### Responsive Breakpoints
```css
/* Mobile */
@media (max-width: 640px) { }

/* Tablet */
@media (min-width: 641px) and (max-width: 1024px) { }

/* Desktop */
@media (min-width: 1025px) { }
```

## ♿ Accessibility Standards

### Focus States
```css
.focusable:focus {
  outline: 2px solid var(--color-accent-primary);
  outline-offset: 2px;
}
```

### Screen Reader Support
```html
<!-- Use semantic HTML -->
<nav aria-label="Main navigation">
<main aria-label="Main content">
<aside aria-label="Sidebar">

<!-- Provide descriptive labels -->
<button aria-label="Toggle theme">
<input aria-describedby="help-text">
```

### Color Contrast
- **Normal text**: 4.5:1 contrast ratio minimum
- **Large text**: 3:1 contrast ratio minimum
- **Interactive elements**: Clear focus indicators

## 🎯 Usage Guidelines

### Button Usage
- **Primary**: Main actions (Save, Create, Submit)
- **Secondary**: Secondary actions (Cancel, Edit, View)
- **Ghost**: Tertiary actions (Delete, Reset, Clear)

### Color Usage
- **Success**: Completed tasks, positive feedback
- **Warning**: Attention needed, caution
- **Error**: Failed actions, validation errors
- **Info**: Neutral information, tips

### Typography Hierarchy
```css
h1 { font-size: var(--font-size-2xl); }  /* Page titles */
h2 { font-size: var(--font-size-xl); }   /* Section titles */
h3 { font-size: var(--font-size-lg); }   /* Subsection titles */
p  { font-size: var(--font-size-base); } /* Body text */
```

### Spacing Consistency
- **Card padding**: `var(--space-4)` (16px)
- **Button padding**: `var(--space-3) var(--space-4)` (12px 16px)
- **Section gaps**: `var(--space-6)` (24px)
- **Element gaps**: `var(--space-4)` (16px)

## 🔄 State Management

### Interactive States
```css
/* Hover */
.interactive:hover {
  background-color: var(--color-bg-secondary);
}

/* Active */
.interactive:active {
  transform: translateY(1px);
}

/* Disabled */
.interactive:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

### Loading States
```css
.loading {
  opacity: 0.7;
  pointer-events: none;
}
```

## 📱 Mobile Guidelines

### Touch Targets
- **Minimum size**: 44px × 44px
- **Recommended**: 48px × 48px
- **Spacing**: 8px between targets

### Mobile Typography
```css
@media (max-width: 640px) {
  .main__title {
    font-size: var(--font-size-xl); /* Smaller on mobile */
  }
}
```

## 🖨️ Print Styles

### Print-Specific Rules
```css
@media print {
  /* Hide interactive elements */
  .no-print { display: none !important; }
  
  /* Force light colors */
  * {
    color: black !important;
    background: white !important;
  }
  
  /* Expand all content */
  details { display: block !important; }
}
```

## 🎨 Animation Guidelines

### Transitions
```css
.transition {
  transition: all 0.2s ease;
}

.transition-colors {
  transition: color 0.2s ease, background-color 0.2s ease;
}
```

### Respect Motion Preferences
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    transition-duration: 0.01ms !important;
  }
}
```

## 🚀 Performance Guidelines

### CSS Organization
1. **tokens.css** - Variables first
2. **base.css** - Reset and base styles
3. **utilities.css** - Utility classes
4. **components.css** - Reusable components
5. **layouts.css** - Page-specific layouts
6. **themes.css** - Theme variations
7. **print.css** - Print optimizations

### Best Practices
- Use CSS custom properties for consistency
- Minimize specificity conflicts
- Group related styles together
- Comment complex calculations
- Use semantic class names (BEM methodology)

---

This style guide ensures consistent design and development across the TreeNotes application. Follow these guidelines when adding new features or modifying existing components.
