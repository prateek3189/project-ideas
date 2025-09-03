# Parent-Kid Learning App

> **A static HTML + CSS prototype** for an app where parents and toddlers enjoy **interactive stories**, **rhymes**, and **pronunciation practice** together.

## 🎯 Vision & Goals

- Make screen time **co-learning time**: read stories, sing rhymes, practice words
- Encourage **speech and listening** with friendly **pronunciation cues** (visual in V1)
- Keep the UI **big-tap, low-friction, bilingual-friendly**, and **printable**
- Prepare a structure you can later enhance with audio recording, TTS, and progress tracking

## 🚀 Quick Start

1. **Clone or download** this repository
2. **Open `index.html`** in any modern web browser
3. **Navigate** through the different sections using the links
4. **Print** stories and activities using the print functionality

## 📱 What's Included (V1)

### Core Pages

- **Home** - Hero tiles for quick access to main features
- **Stories** - Library of 9+ story cards with filters
- **Story Reader** - 8-page story with vocabulary and parent tips
- **Rhymes** - 6 rhyme cards with beat animations and lyrics
- **Pronunciation Practice** - Word cards with syllable dots and mouth tips
- **Progress** - Achievement badges and learning streaks (visual)
- **Parent Mode** - Settings and controls behind parental gate
- **Settings** - Theme, accessibility, and language options
- **About** - Learning philosophy and future roadmap

### Features

- **Responsive Design** - Works on desktop, tablet, and mobile
- **Multiple Themes** - Light, dark, high-contrast, and quiet mode
- **Accessibility** - High contrast, large text, dyslexia-friendly fonts
- **Print Styles** - Storybook, flashcards, and coloring sheets
- **Bilingual Support** - English, Hindi, and Marathi content
- **Touch-Friendly** - Large buttons and clear navigation

## 🎨 Design System

### Colors

- **Background**: #FFFDF7 (warm cream)
- **Surface**: #FFFFFF (white)
- **Text**: #1F2A44 (dark blue)
- **Accent**: #FF7A59 (warm orange)
- **Secondary**: #3BB6F6 (calm blue)

### Typography

- **Titles**: 28-32px
- **Story Text**: 22-24px
- **Body**: 16-18px
- **Touch Targets**: Minimum 44px height

### Spacing

- **Scale**: 6px, 12px, 16px, 24px, 32px, 48px, 64px
- **Border Radius**: 8px, 16px, 24px, 999px (full)

## 🏗️ Architecture

### CSS Structure

```
styles/
├── tokens.css      # Design tokens & variables
├── base.css        # Reset & base styles
├── utilities.css   # Helper classes
├── components.css  # UI components
├── layouts.css     # Page layouts
├── themes.css      # Theme variations
└── print.css       # Print styles
```

### Component Classes

- **BEM Methodology**: `.story-card__cover`, `.rhyme-card__beat`
- **Modifier Classes**: `.hero-tile--primary`, `.sticker-badge--unlocked`
- **Utility Classes**: `.flex`, `.grid--3`, `.text--center`

### Responsive Breakpoints

- **Mobile**: < 480px
- **Tablet**: < 768px
- **Desktop**: 768px+

## 🎭 Content Examples

### Stories

- _The Red Ball_ - Colors, sharing, friendship
- _Mimi's Garden_ - Fruits, counting, patience
- _Animal Parade_ - Animals, sounds, cooperation

### Rhymes

- "Clap Clap Little Hands" - Action rhymes
- "Hop Hop Bunny Hop" - Movement rhymes
- "Rain Rain Go Away" - Weather rhymes

### Words

- **Animals**: cat/बिल्ली/मांजर, dog/कुत्ता/कुत्रा
- **Fruits**: apple/सेब/सफरचंद, mango/आम/आंबा
- **Colors**: red/लाल/लाल, blue/नीला/निळा

## 🖨️ Print Features

### Storybook Mode

- 2 pages per sheet
- Large illustrations
- Vocabulary chips
- Parent tips

### Flashcards

- 3×3 grid layout
- Picture + word
- Syllable dots
- Translations

### Coloring Sheets

- Outline art
- Word outlines
- Instructions

## 🔮 Future Enhancements (V2+)

### Phase 2: Interactive Features

- Speech recognition for pronunciation practice
- Text-to-speech with word highlighting
- Real progress tracking and achievements
- Custom learning playlists

### Phase 3: Advanced Learning

- AI-powered pronunciation feedback
- Adaptive content based on child's level
- Multi-device sync
- Parent dashboard with insights

### Phase 4: Community & Expansion

- Additional Indian languages
- User-generated content
- Teacher tools
- Offline content packs

## 🛠️ Technical Details

### Browser Support

- **Chrome**: 80+ (recommended)
- **Firefox**: 75+
- **Safari**: 13+
- **Edge**: 80+

### Performance

- **No JavaScript** - Pure HTML/CSS
- **Fast Loading** - Minimal assets
- **Offline Ready** - Works without internet
- **Print Optimized** - Clean A4 output

### Accessibility

- **WCAG 2.1 AA** compliant
- **Keyboard Navigation** support
- **Screen Reader** friendly
- **High Contrast** themes

## 📚 Learning Approach

### Read → Repeat → Play

1. **Read**: Start by reading stories and rhymes together
2. **Repeat**: Practice key words and phrases multiple times
3. **Play**: Make learning fun with interactive activities

### Screen Time Guidelines

- **Ages 2-3**: 10-15 minutes per session, 1-2 times daily
- **Ages 3-4**: 15-20 minutes per session, 1-2 times daily
- **Always**: Use together with your child, not as a babysitter

## 🔒 Privacy & Safety

### What We Do

- Local storage only (no external servers)
- No personal data collection
- No advertising or commercial content
- Age-appropriate content curation

### What We Don't Do

- No external links or websites
- No social media integration
- No usage analytics or tracking
- No third-party services

## 🤝 Contributing

### Feedback Welcome

- Content ideas and suggestions
- Feature requests
- Bug reports
- Success stories

### Development

- This is a static prototype (V1)
- Future versions will include JavaScript
- Focus on content quality and UX
- Accessibility-first approach

## 📄 License

This project is created for educational and family use. All content is original or public domain.

## 📞 Support

For questions, feedback, or support:

- Check the **About** page for detailed information
- Review **Parent Mode** for settings and tips
- Use **Print** features for offline activities

---

**Built with ❤️ for families learning together**

_Version 0.1 - December 2024_
