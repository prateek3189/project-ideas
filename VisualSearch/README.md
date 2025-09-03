# Visual Search App - Static HTML/CSS Prototype

A **static HTML + CSS v1 prototype** for a visual search app where users can upload or take photos to find similar items for shopping or learning. This is a JavaScript-free demonstration that showcases the UI/UX design and user flows.

## 🎯 Project Overview

This prototype demonstrates a visual search application with two main modes:

- **Shop Mode**: Find similar products for purchase with prices and store information
- **Learn Mode**: Identify objects, plants, landmarks, and artworks with educational content

## ✨ Features

### Core Functionality

- **Upload Interface**: Drag & drop and camera capture UI (visual only)
- **Mode Switching**: Toggle between Shop and Learn modes
- **Visual Similarity**: Confidence scores and similarity sliders
- **Object Detection**: Bounding boxes and detection overlays (static)
- **Filtering**: Price, color, brand, style, and category filters
- **Collections**: Save and organize favorite items
- **Comparison**: Side-by-side item comparison
- **Print Support**: Print-friendly layouts for results and collections

### Design System

- **Responsive Design**: Mobile-first approach with desktop enhancements
- **Theme Support**: Light, dark, and high-contrast themes
- **Accessibility**: WCAG compliant with keyboard navigation and screen reader support
- **Print Styles**: Optimized layouts for printing results and collections

## 📁 Project Structure

```
VisualSearch/
├── index.html              # Home/Search page
├── results.html            # Search results with filters
├── detail.html             # Product/Entity detail page
├── compare.html            # Item comparison page
├── collections.html        # Saved items and collections
├── settings.html           # User preferences and settings
├── about.html              # About page with privacy info
├── styles/
│   ├── tokens.css          # Design tokens (colors, spacing, typography)
│   ├── base.css            # Reset and base styles
│   ├── utilities.css       # Utility classes
│   ├── components.css      # Reusable components
│   ├── layouts.css         # Page layouts and grid systems
│   ├── themes.css          # Theme variations
│   └── print.css           # Print-specific styles
└── README.md               # This file
```

## 🚀 Getting Started

1. **Clone or download** the project files
2. **Open `index.html`** in a web browser
3. **Navigate** through the different pages to explore the interface
4. **Test responsive design** by resizing your browser window
5. **Try print preview** (Ctrl/Cmd + P) to see print layouts

## 🎨 Design System

### Colors

- **Primary**: #2563EB (Blue)
- **Shop Accent**: #10B981 (Green)
- **Learn Accent**: #8B5CF6 (Purple)
- **Warning**: #F59E0B (Orange)
- **Danger**: #DC2626 (Red)

### Typography

- **Font Family**: System fonts (-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto)
- **Scale**: 12px (small) to 28px (display)
- **Tabular Numbers**: For prices and scores

### Spacing

- **Scale**: 4px, 8px, 12px, 16px, 24px, 32px, 48px, 64px, 80px
- **Border Radius**: 4px (small), 6px (medium), 12px (large), 999px (full)

## 📱 Pages Overview

### Home (`index.html`)

- Upload/camera interface
- Mode selection (Shop/Learn)
- Example searches
- Recent searches
- Privacy notice

### Results (`results.html`)

- Search results grid
- Filter sidebar
- Similarity slider
- Object detection overlays
- Mode switching

### Detail (`detail.html`)

- Large product/entity image
- Detection boxes
- Price and availability
- Attributes table
- Related items
- Why this match explanations

### Collections (`collections.html`)

- Saved items grid
- Folder organization
- Print preview
- Collection management

### Compare (`compare.html`)

- Side-by-side comparison
- Similarity meters
- Pros/cons lists
- Summary recommendations

### Settings (`settings.html`)

- Region and currency
- Theme selection
- Search preferences
- Privacy controls
- Data management

### About (`about.html`)

- How it works
- Features overview
- Technology details
- Privacy policy
- Accessibility info

## 🎯 User Stories (Visual-Only)

1. **Upload/Capture** an image → choose **Shop** or **Learn** → see **results grid**
2. Use **crop** (static overlay) to focus on an object; toggle **detect boxes** (visual)
3. Apply **filters** (price, color, style) or **similarity slider** (CSS range)
4. Open **Result Detail**: product/info card with "why this match" copy
5. Save to **Collections** and **print/share** a result sheet (print stylesheet)

## 🔧 Technical Details

### CSS Architecture

- **BEM Methodology**: Block\_\_Element--Modifier naming
- **CSS Custom Properties**: For theming and consistency
- **Mobile-First**: Responsive design with progressive enhancement
- **Print Styles**: Separate stylesheet for print optimization

### Accessibility Features

- **Semantic HTML**: Proper heading hierarchy and landmarks
- **Keyboard Navigation**: All interactive elements are keyboard accessible
- **Screen Reader Support**: ARIA labels and descriptions
- **High Contrast**: Support for high contrast themes
- **Reduced Motion**: Respects user motion preferences

### Browser Support

- **Modern Browsers**: Chrome, Firefox, Safari, Edge (last 2 versions)
- **CSS Grid**: Used for layouts (with fallbacks)
- **CSS Custom Properties**: For theming
- **Print Media Queries**: For print styles

## 🚧 Limitations (V1 Prototype)

- **No JavaScript Functionality**: All interactions are visual placeholders
- **No Real Camera Access**: Camera button shows permission copy only
- **No Image Uploads**: Upload interface is non-functional
- **No AI Processing**: All "AI" features are static demonstrations
- **No Real Data**: All products and information are placeholder content
- **No Backend**: No server-side functionality or data persistence

## 🔮 Future Enhancements

### Phase 2 (JavaScript Integration)

- Real camera access and image uploads
- Image preprocessing and optimization
- Basic client-side image analysis
- Local storage for collections

### Phase 3 (AI Integration)

- Computer vision model integration
- Object detection and classification
- Visual similarity matching
- Real product database connections

### Phase 4 (Full Application)

- Backend API and database
- User accounts and authentication
- Real-time product data
- Mobile app development

## 📄 License

This is a demonstration prototype created for educational and portfolio purposes. All placeholder content and designs are for demonstration only.

## 🤝 Contributing

This is a static prototype demonstration. For a production version, contributions would be welcome for:

- Accessibility improvements
- Performance optimizations
- Additional theme variations
- Enhanced print layouts
- Mobile-specific enhancements

## 📞 Contact

This is a prototype demonstration. In a production version, contact information would be provided here.

---

**Note**: This is a static HTML/CSS prototype demonstrating the UI/UX design for a visual search application. All functionality is simulated and no real image processing or AI capabilities are implemented.
