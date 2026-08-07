# Design System & Explanation - North Star Bakery

## Overview

The North Star Bakery website employs a warm, welcoming design system that reflects the artisan, handcrafted nature of the business. Every design decision supports readability, accessibility, and an inviting user experience.

---

## 1. Color Palette

### Primary Colors

| Color | Hex Code | Usage | Purpose |
|-------|----------|-------|---------|
| Cream | #FFF8F0 | Background, header | Warm, inviting base that evokes fresh baked goods |
| Dark Brown | #6B3E26 | Headings, text, borders | Professional, grounded, represents quality ingredients |
| Peach | #D88C5A | Accents, hover states, borders | Energetic warmth that draws attention to interactive elements |
| Charcoal | #2F2A26 | Body text, footer background | High contrast for readability |
| Soft Beige | #eaddd3 | Card backgrounds | Visual separation while maintaining warmth |

### Rationale

The color scheme evokes a bakery aesthetic:
- **Cream background** mimics the color of fresh flour and dough
- **Dark brown** represents chocolate, whole grains, and earth tones
- **Peach accent** adds energy without overwhelming, like a glaze or frosting
- The palette is warm, not cold, creating an emotional connection to comfort and tradition

### Accessibility

- All text meets WCAG AA contrast ratios
- Color alone is never used to convey information
- The palette is colorblind-friendly

---

## 2. Typography

### Font Families

**Headings: Playfair Display (Serif)**
- Font-weight: 700 (Bold)
- Used for: h1, h2, h3, .site-title
- Rationale: Elegant, sophisticated serif font conveys craftsmanship and tradition. High visual hierarchy.

**Body Text: Open Sans (Sans-serif)**
- Font-weight: 400 (Regular), 600 (Semibold)
- Used for: Paragraph text, labels, navigation links
- Rationale: Clean, modern sans-serif ensures excellent readability across devices and sizes.

### Font Sizing Strategy

| Element | Size | Line Height | Purpose |
|---------|------|-------------|---------|
| h1 | 2.5rem (Mobile: 2rem) | 1.6 | Page titles, prominent visual anchor |
| h2 | 1.75rem (Mobile: 1.5rem) | 1.6 | Section headers, clear content hierarchy |
| h3 | 1.25rem | 1.6 | Card titles, subsection headers |
| p | 1.05rem | 1.6 | Body text, optimal for scanning |

### Rationale

- **2 font families** keeps design cohesive without feeling repetitive
- **Large font sizes** ensure readability on all devices
- **Line-height of 1.6** provides breathing room for comfortable reading
- **Consistent sizing** creates a predictable, scannable hierarchy

---

## 3. Responsive Layout Strategy

### Mobile-First Approach

The stylesheet begins with mobile styles, then enhances for larger screens. This ensures:
- **Performance** - Simpler styles load first
- **Usability** - Touch targets and spacing optimized for small screens
- **Progressive Enhancement** - Advanced layouts appear on capable devices

### Breakpoint: 600px

```css
@media (min-width: 600px) {
  /* Tablet and larger screens */
}
```

### Layout Changes by Breakpoint

#### Mobile (< 600px)
- **Header**: Vertical flexbox (stacked)
- **Navigation**: Vertical menu (column direction)
- **Padding**: 5% on sides for screen efficiency
- **Cards**: Single column layout
- **Font sizes**: Reduced for mobile optimization

#### Tablet/Desktop (≥ 600px)
- **Header**: Horizontal flexbox (row with space-between)
- **Navigation**: Horizontal menu (row direction)
- **Padding**: 10% on sides for desktop spacing
- **Cards**: 2-3 column grid layout using flexbox wrap
- **Font sizes**: Full size for desktop reading
- **Main max-width**: 1200px prevents lines from becoming too long

---

## 4. Flexbox Implementation

### Header Layout
```css
header {
  display: flex;
  flex-direction: column;      /* Mobile: vertical */
  align-items: center;
  gap: 1rem;
}

@media (min-width: 600px) {
  header {
    flex-direction: row;        /* Desktop: horizontal */
    justify-content: space-between;
  }
}
```
**Purpose**: Logo/title on left, navigation on right on desktop; stacked on mobile.

### Navigation Layout
```css
nav ul {
  list-style: none;
  display: flex;
  flex-direction: column;       /* Mobile: vertical stack */
  align-items: center;
  gap: 0.75rem;
}

@media (min-width: 600px) {
  nav ul {
    flex-direction: row;        /* Desktop: horizontal menu */
    gap: 2rem;
  }
}
```
**Purpose**: Vertical menu for touch screens; horizontal for mouse/keyboard users.

### Content Grid Layout
```css
.section-grid {
  display: flex;
  flex-direction: column;       /* Mobile: single column */
  gap: 2rem;
}

@media (min-width: 600px) {
  .section-grid {
    flex-direction: row;        /* Desktop: multiple columns */
    flex-wrap: wrap;
  }
  
  .card {
    flex: 1;                    /* Equal width cards */
    min-width: 250px;           /* Minimum card width */
  }
}
```
**Purpose**: Responsive card layouts that stack on mobile, organize in rows on desktop.

### Flexbox Advantages

✨ **Flexible** - Adapts to any content size  
♿ **Accessible** - No grid gaps or layout issues  
📱 **Mobile-friendly** - Easy to change direction for smaller screens  
🎯 **Maintainable** - Fewer media queries needed than float layouts  

---

## 5. Visual Hierarchy & Readability

### Heading Strategy
- **h1**: Site/page title, large with peach underline for emphasis
- **h2**: Major section dividers, establishes content blocks
- **h3**: Card titles, sub-section headings within cards

### Content Scanning
Users should be able to skim headings and understand page structure without reading full text.

### Spacing Strategy
- **Margin-bottom on paragraphs**: 1.25rem for separation
- **Gap between cards**: 2rem for clear visual distinction
- **Padding inside cards**: 1.5rem for internal breathing room
- **Padding around main**: 5-10% for edge margins

### Form Readability
- **Fieldset borders**: Visual grouping of form elements
- **Label placement**: Above inputs for mobile clarity
- **Input focus state**: 2px peach outline for clear indication
- **Full-width inputs**: Touch-friendly on mobile

---

## 6. Consistent Element Styling

### Navigation Links
- Color: Dark brown (#6B3E26)
- Hover/Focus: Peach (#D88C5A) - clear feedback
- Transition: 0.3s ease for smooth interaction

### Buttons
- Background: Dark brown (#6B3E26)
- Text: Cream (#FFF8F0)
- Hover: Peach (#D88C5A) background
- Padding: 0.75rem 2rem for adequate click target

### Images & Figures
- Border-radius: 8px for soft edges
- Border: 1px dark brown for definition
- Max-width: 100% for responsiveness
- Figure background: Soft beige for context

### Form Inputs
- Border: 1px solid dark brown
- Focus outline: 2px peach
- Padding: 0.75rem for comfortable typing
- Background: White for contrast

---

## 7. Design Principles Applied

### 1. Consistency
- Same colors, fonts, and spacing across all pages
- Repeated component styles (cards, buttons, forms)
- Navigation identical on every page

### 2. Simplicity
- 2 font families (not 3+)
- 4 main colors (not 8+)
- Clean, minimal layout
- No unnecessary decorations

### 3. Readability
- Large font sizes (1.05rem minimum for body)
- High contrast text
- Ample line-height (1.6)
- Generous spacing and padding

### 4. Accessibility
- Semantic HTML (header, nav, main, section, footer)
- Proper heading hierarchy (h1 → h2 → h3)
- Form labels associated with inputs
- Focus states clearly visible

### 5. Mobile-First
- Start simple, enhance for larger screens
- Touch-friendly spacing and buttons
- Readable without horizontal scrolling
- Performance-optimized

### 6. Warmth & Personality
- Warm color palette evokes bakery aesthetic
- Serif headings suggest craftsmanship
- Soft borders and rounded corners feel inviting
- Overall tone: welcoming, professional, trustworthy

---

## 8. Browser Compatibility

The design uses modern CSS features supported by:
- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ⚠️ IE 11 (limited support - flexbox works, but may have spacing issues)

### Key Technologies
- Flexbox (primary layout method)
- CSS Grid (not used, but could enhance desktop)
- Media queries (responsive breakpoints)
- CSS Transitions (interactive feedback)
- Google Fonts (external typography)

---

## 9. Future Enhancements

Potential improvements while maintaining design consistency:

- 📸 Add hero image sections with background overlays
- 🎬 Subtle animations on card hover (transform, shadow)
- 🔍 Additional breakpoints for ultra-wide displays
- 🌙 Dark mode theme option
- ♿ Enhanced keyboard navigation indicators
- 📊 Product image galleries
- 🗺️ Embedded Google Map on contact page

---

## Conclusion

The North Star Bakery design system balances **warmth and professionalism**, using a carefully chosen color palette, paired fonts, and flexible flexbox layouts to create an inviting, accessible, and responsive website. Every design decision supports the business's commitment to quality, tradition, and customer experience.

The mobile-first, responsive approach ensures the website works beautifully on devices from 320px (small phones) to 1920px (desktop monitors), while maintaining consistent visual identity and readability throughout.
