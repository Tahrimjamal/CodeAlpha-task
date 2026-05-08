# Fitness Tracker App - Specification

## 1. Project Overview

- **Project Name**: FitTrack - Fitness Tracker
- **Type**: Single-page web application (HTML/CSS/JS)
- **Core Functionality**: Allow users to log and track daily fitness activities including steps, workouts, calories burned, with visual progress indicators and data persistence via localStorage
- **Target Users**: Health-conscious individuals who want to track their daily fitness activities

## 2. UI/UX Specification

### Layout Structure

- **Navigation**: Fixed bottom tab bar with 3 main sections
  - Dashboard (home)
  - Log Activity
  - History/Stats
- **Main Content**: Scrollable area above the navigation

### Responsive Design
- Mobile-first design (320px - 480px primary)
- Tablet/Desktop: max-width 600px centered container
- Breakpoints: 480px (mobile), 600px+ (tablet/desktop)

### Visual Design

#### Color Palette
- **Primary**: `#10B981` (Emerald Green - represents health/vitality)
- **Secondary**: `#1E293B` (Dark Slate - backgrounds)
- **Accent**: `#F59E0B` (Amber - highlights/warnings)
- **Background**: `#0F172A` (Dark Blue-Black)
- **Surface**: `#1E293B` (Card backgrounds)
- **Text Primary**: `#F8FAFC` (Off-white)
- **Text Secondary**: `#94A3B8` (Muted gray)
- **Success**: `#22C55E` (Green)
- **Danger**: `#EF4444` (Red)

#### Typography
- **Font Family**: "Outfit" (Google Fonts) - modern, clean geometric sans-serif
- **Headings**: 
  - H1: 28px, weight 700
  - H2: 22px, weight 600
  - H3: 18px, weight 600
- **Body**: 14px, weight 400
- **Small**: 12px, weight 400

#### Spacing System
- Base unit: 8px
- Padding: 16px (cards), 24px (sections)
- Margin: 8px, 16px, 24px
- Border radius: 12px (cards), 8px (buttons), 24px (pills)

#### Visual Effects
- Card shadows: `0 4px 20px rgba(0, 0, 0, 0.3)`
- Subtle gradient on progress rings
- Smooth transitions: 0.3s ease for all interactive elements
- Hover scale: 1.02 on cards
- Glassmorphism effect on navigation: `backdrop-filter: blur(10px)`

### Components

#### 1. Dashboard View
- **Date Header**: Current date display with greeting
- **Stats Cards Grid** (2x2):
  - Steps card with circular progress ring
  - Calories card with flame icon
  - Workouts count card with dumbbell icon
  - Active minutes card with clock icon
- **Weekly Overview Bar Chart**: 7-day horizontal bars showing calories burned
- **Recent Activities List**: Last 5 activities with quick delete option

#### 2. Log Activity View
- **Activity Type Selector**: Grid of activity types (Walking, Running, Cycling, Gym, Swimming, Yoga, Other)
- **Input Fields**:
  - Duration (minutes) - number input with increment/decrement
  - Calories Burned - number input
  - Steps - number input
  - Notes - optional text area
- **Date/Time Picker**: Default to current datetime
- **Save Button**: Primary action button

#### 3. History View
- **Date Filter**: Week/Month/All toggle
- **Summary Stats**: Total steps, calories, workouts for selected period
- **Activity Timeline**: Grouped by date, showing all logged activities
- **Empty State**: Illustration and prompt when no data

#### Navigation Bar
- Fixed bottom, 3 tabs with icons and labels
- Active state: Primary color highlight
- Inactive: Text secondary color

### Interactive Behaviors
- Tab switching: smooth fade transition between views
- Progress rings: animate on load (0 to value over 1s)
- Form validation: inline error messages
- Toast notifications: success/error feedback
- Pull to refresh on history (mobile)

## 3. Functionality Specification

### Core Features

1. **Activity Logging**
   - Select from predefined activity types
   - Enter duration, calories, steps
   - Optional notes
   - Automatic timestamp (editable)
   - Save to localStorage

2. **Dashboard Display**
   - Today's aggregated stats
   - Progress toward daily goals
   - Weekly calorie chart
   - Recent activities quick view

3. **Data Visualization**
   - Circular progress rings for daily goals
   - Horizontal bar chart for weekly overview
   - Color-coded activity cards

4. **History/Statistics**
   - View all past activities
   - Filter by date range
   - Delete individual entries
   - Aggregate statistics

5. **Data Persistence**
   - localStorage for all user data
   - JSON structure for activities array
   - Auto-save on every action

### User Interactions
- Tap activity type to select
- +/- buttons for numeric inputs
- Swipe to delete activity (history)
- Tap tabs to switch views
- Tap save to log activity

### Data Model
```json
{
  "activities": [
    {
      "id": "uuid",
      "type": "walking|running|cycling|gym|swimming|yoga|other",
      "duration": 30,
      "calories": 200,
      "steps": 3000,
      "notes": "Optional note",
      "date": "2026-04-07T10:30:00.000Z",
      "createdAt": "timestamp"
    }
  ],
  "goals": {
    "dailySteps": 10000,
    "dailyCalories": 500,
    "dailyWorkouts": 1
  }
}
```

### Edge Cases
- Empty state: Show encouraging message to start tracking
- Invalid inputs: Show validation errors, prevent save
- Date edge cases: Handle timezone correctly
- Storage limit: Warn if localStorage is full (unlikely)

## 4. Acceptance Criteria

### Visual Checkpoints
- [ ] Dark theme with emerald accent colors applied
- [ ] Outfit font loaded and applied
- [ ] Bottom navigation visible and functional
- [ ] Dashboard shows 4 stat cards with progress rings
- [ ] Weekly chart displays 7 bars
- [ ] Activity type selector shows 7 options in grid
- [ ] History shows grouped activities by date

### Functional Checkpoints
- [ ] Can add new activity with all fields
- [ ] Activity appears in dashboard immediately after save
- [ ] Weekly chart updates with new data
- [ ] History shows all past activities
- [ ] Can delete individual activities
- [ ] Data persists after page refresh
- [ ] Tab navigation switches views smoothly
- [ ] Form validation prevents invalid submissions

### Technical Checkpoints
- [ ] No console errors on load
- [ ] localStorage correctly saves/loads data
- [ ] Responsive on mobile (320px) to desktop (600px+)
- [ ] All animations run smoothly (60fps)