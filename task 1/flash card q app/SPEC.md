# Flashcard Quiz App Specification

## 1. Project Overview

- **Project Name**: FlashMind
- **Type**: Single-page web application (HTML/CSS/JS)
- **Core Functionality**: A flashcard study app where users can create, browse, edit, and delete flashcards with question/answer pairs, navigating through them with Next/Previous controls
- **Target Users**: Students and learners

## 2. UI/UX Specification

### Layout Structure

- **Header**: App title centered at top
- **Main Area**: 
  - Flashcard display container (centered, prominent)
  - Card counter (current/total)
- **Controls**:
  - Navigation buttons (Previous/Next) below card
  - Show Answer button on card face
- **CRUD Panel**: Bottom section for managing flashcards
  - Add new card form
  - Edit/Delete controls for current card

### Visual Design

**Color Palette**
- Background: `#1a1a2e` (deep navy)
- Card background: `#fefefe` (off-white)
- Card border: `#e94560` (coral accent)
- Primary text: `#16213e` (dark blue)
- Secondary text: `#533483` (purple)
- Accent/Buttons: `#e94560` (coral)
- Button hover: `#ff6b6b` (light coral)
- Success: `#00d9a5` (mint green)
- Delete: `#ff4757` (red)

**Typography**
- Font family: `'Nunito', sans-serif` (from Google Fonts)
- Title: 32px, bold
- Card question/answer: 24px, medium
- Buttons: 16px, semi-bold
- Form labels: 14px, regular

**Spacing**
- Card padding: 40px
- Section margins: 24px
- Button padding: 12px 24px
- Card border-radius: 16px

**Visual Effects**
- Card flip animation: 3D transform (0.6s ease)
- Button hover: scale(1.05) with color transition
- Card entrance: fade-in with slight scale
- Soft box-shadow on card: `0 10px 40px rgba(233, 69, 96, 0.15)`

### Components

1. **Flashcard**
   - Front: shows question
   - Back: shows answer (revealed on click)
   - States: front-facing, back-facing (flipped)

2. **Navigation Buttons**
   - Previous: disabled on first card
   - Next: disabled on last card

3. **CRUD Form**
   - Question input field
   - Answer textarea
   - Add button
   - Edit/Delete buttons (visible when card selected)

4. **Empty State**
   - Message: "No flashcards yet. Add your first card below!"

## 3. Functionality Specification

### Core Features

1. **View Flashcards**
   - Display current card's question
   - Click "Show Answer" to flip and reveal answer
   - Auto-flip back to question on next/prev

2. **Navigate Cards**
   - Next button: advance to next card
   - Previous button: go to previous card
   - Display "Card X of Y" counter

3. **Add Flashcard**
   - Input question text
   - Input answer text
   - Click "Add Card" to save
   - Validates both fields required
   - New card becomes current card

4. **Edit Flashcard**
   - Click "Edit" to populate form with current card data
   - Modify and save updates
   - Cancel returns to normal view

5. **Delete Flashcard**
   - Click "Delete" removes current card
   - Confirmation prompt
   - Next available card becomes current

### User Interactions

- Click card or "Show Answer" to flip
- Click Next/Previous to navigate
- Form submission with Enter key or button click
- Edit mode: click Edit to load, click Save to confirm, click Cancel to abort

### Data Handling

- LocalStorage persistence
- Keys: `flashcard_data` (JSON array)
- Each card: `{ id: timestamp, question: string, answer: string }`
- Load on page init, save on any change

### Edge Cases

- Empty state: show message, hide navigation
- Single card: disable Next/Previous appropriately
- Last card deletion: navigate to previous or show empty state
- Form validation: require non-empty question and answer

## 4. Acceptance Criteria

1. App loads with previously saved flashcards (or default demo cards)
2. Clicking "Show Answer" flips card with smooth 3D animation
3. Next/Previous navigates correctly, updates counter
4. Adding card: form clears, new card appears, persists on refresh
5. Editing card: updates both display and storage
6. Deleting card: removes from array, updates counter, persists
7. All animations smooth (no jank)
8. Works in modern browsers (Chrome, Firefox, Edge)