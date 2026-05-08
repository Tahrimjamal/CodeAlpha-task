# Random Quote Generator - Specification

## 1. Project Overview
- **Project Name:** Random Quote Generator
- **Type:** Single-page web application (HTML/CSS/JS)
- **Core Functionality:** Display random inspirational quotes from a curated collection, allowing users to get new quotes on demand
- **Target Users:** Anyone seeking daily inspiration or motivation

## 2. UI/UX Specification

### Layout Structure
- **Container:** Centered card on a full-viewport background
- **Card dimensions:** Max-width 680px, padding 48px
- **Layout:** Vertical stack - quote text area, author, button
- **Responsive:** Single column, scales down padding on mobile

### Visual Design
- **Color Palette:**
  - Background: `#1a1a2e` (deep navy)
  - Card background: `#16213e` (dark slate blue)
  - Quote text: `#eaeaea` (soft white)
  - Author text: `#7f8c8d` (muted gray)
  - Accent/Button: `#e94560` (vibrant coral red)
  - Button hover: `#ff6b6b` (lighter coral)
- **Typography:**
  - Quote text: "Playfair Display", serif, 28px, italic
  - Author: "Source Sans Pro", sans-serif, 18px
  - Button: "Source Sans Pro", sans-serif, 16px, uppercase, letter-spacing 2px
- **Spacing:**
  - Card border-radius: 16px
  - Quote to author gap: 24px
  - Author to button gap: 36px
  - Button padding: 14px 36px
- **Visual Effects:**
  - Card: subtle box-shadow `0 25px 50px rgba(0,0,0,0.3)`
  - Quote fade-in animation on change (0.4s ease)
  - Button: slight scale on hover (1.02), smooth transitions

### Components
1. **Quote Display**
   - Large quotation marks as decorative elements
   - Quote text in italic serif font
   - Left-aligned or center-aligned based on length
2. **Author Display**
   - Prefix with em-dash "—"
   - Muted gray color
3. **New Quote Button**
   - Solid coral background
   - White text
   - Pill-shaped (border-radius 30px)
   - Hover state with lighter shade

## 3. Functionality Specification

### Core Features
- **Quote Collection:** Array of 20+ curated quotes with authors
- **Random Selection:** Math.random() with shuffle or Fisher-Yates for true randomness
- **Display:** Show quote text and author on load and button click
- **Initial Load:** Auto-display a random quote on page load

### User Interactions
- Click "New Quote" button → Display a different random quote with fade animation
- Page load → Display a random quote immediately

### Edge Cases
- Avoid showing the same quote twice consecutively
- Handle empty quote collection gracefully

## 4. Acceptance Criteria
- [ ] Page displays a random quote on initial load
- [ ] Clicking "New Quote" button shows a different quote
- [ ] Quote text is clearly readable in italic serif font
- [ ] Author name is displayed with em-dash prefix
- [ ] UI is centered and visually clean
- [ ] Fade animation plays on quote change
- [ ] No Console errors