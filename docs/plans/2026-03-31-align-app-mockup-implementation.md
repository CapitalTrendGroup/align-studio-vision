# ALIGN. Studio App Mockup — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a single-file interactive HTML mockup of the ALIGN. Studio app that Katie can open on her iPhone and navigate as if using the real app.

**Architecture:** Single HTML file with embedded CSS (design system + all screens) and vanilla JavaScript (navigation, screen transitions, simulated interactions). PWA meta tags for full-screen home screen experience. All data hardcoded in JS objects.

**Tech Stack:** HTML5, CSS3 (custom properties, flexbox, grid, keyframe animations), Vanilla JavaScript (no frameworks), Google Fonts (Playfair Display + Inter)

---

### Task 1: HTML Foundation & CSS Design System

**Files:**
- Create: `app-mockup/index.html`

**Step 1: Create the HTML scaffold**

Set up the HTML document with:
- DOCTYPE, lang="en-GB"
- Meta viewport (width=device-width, initial-scale=1, viewport-fit=cover)
- PWA meta tags: apple-mobile-web-app-capable, apple-mobile-web-app-status-bar-style, theme-color
- Google Fonts import (Playfair Display 400/600/700 + Inter 300/400/500/600)
- CSS custom properties block with all design tokens from the design doc
- Base reset and body styles
- The app shell: `<div id="app">` containing a screen container and tab bar

**Step 2: Implement CSS design tokens**

```css
:root {
  --sage: #8B9F82;
  --sage-light: #A8B8A0;
  --sage-dark: #6B7F62;
  --cream: #F5F0EB;
  --cream-light: #FAF8F5;
  --white: #FFFFFF;
  --charcoal: #2C2C2C;
  --stone: #A69F95;
  --stone-dark: #5C574F;
  --sand: #E8E0D8;
  --success: #6B8F71;
  --warning: #D4A574;
  --error: #C47A7A;
  --font-serif: 'Playfair Display', Georgia, serif;
  --font-sans: 'Inter', -apple-system, sans-serif;
  --radius-sm: 8px;
  --radius-md: 12px;
  --radius-lg: 16px;
  --shadow-card: 0 2px 8px rgba(0,0,0,0.06);
  --shadow-elevated: 0 8px 30px rgba(0,0,0,0.08);
  --transition-screen: 300ms ease-out;
  --safe-top: env(safe-area-inset-top, 20px);
  --safe-bottom: env(safe-area-inset-bottom, 0px);
}
```

**Step 3: Implement base component CSS**

- App shell: fixed 100vh, overflow hidden, cream background
- Screen container: relative, full height minus tab bar
- Cards: white bg, var(--radius-md), var(--shadow-card)
- Primary button: sage bg, white text, var(--radius-sm), full-width, 48px height, 16px font semibold
- Secondary button: white bg, 1.5px sage border, sage text
- Input fields: white bg, 1px sand border, radius-sm, sage border on focus
- Tab bar: fixed bottom, white bg, 5 equal columns, sage active / stone inactive, safe-area padding bottom
- Status bar spacer: height var(--safe-top), cream bg
- Typography classes: .heading-xl, .heading-lg, .heading-md, .body, .caption, .label

**Step 4: Implement tab bar HTML with SVG icons**

5 tabs: Home (house), Schedule (calendar), Bookings (bookmark), Content (book-open), Profile (user)
- Each tab: inline SVG icon (24x24, 1.5px stroke) + label below (11px)
- Active state class toggles sage fill/stroke + label colour
- Touch target: 44x44px minimum per tab

**Step 5: Verify**

Open `index.html` in browser. Confirm:
- Cream background fills viewport
- Tab bar is fixed at bottom with 5 icons
- Fonts load correctly (Playfair + Inter)
- On mobile viewport (DevTools), safe areas respected

---

### Task 2: Navigation JavaScript & Screen Transitions

**Files:**
- Modify: `app-mockup/index.html` (script section)

**Step 1: Implement screen management**

```javascript
// Screen container holds all screens as children, only one visible at a time
// Each screen: <div class="screen" data-screen="home"> ... </div>
// Screens: splash, onboarding, home, schedule, bookings, content, profile, admin
```

- `showScreen(name, direction)` — hides current, shows target with slide animation
- `showOverlay(name)` — slides up from bottom (class-detail, booking-confirmation)
- `hideOverlay()` — slides down
- Tab bar click handler: shows corresponding screen, updates active tab
- Track current screen in state object

**Step 2: Implement CSS transitions**

```css
.screen {
  position: absolute; inset: 0;
  opacity: 0; pointer-events: none;
  transform: translateX(30px);
  transition: opacity 300ms ease-out, transform 300ms ease-out;
}
.screen.active {
  opacity: 1; pointer-events: auto;
  transform: translateX(0);
}
.overlay {
  position: fixed; inset: 0; z-index: 50;
  transform: translateY(100%);
  transition: transform 350ms cubic-bezier(0.32, 0.72, 0, 1);
}
.overlay.active { transform: translateY(0); }
```

**Step 3: Implement splash auto-transition**

- Splash screen shows on load
- After 2s, transitions to home screen
- Tab bar hidden during splash, visible after

**Step 4: Verify**

- Page loads with splash, transitions to home after 2s
- Tab bar appears, clicking tabs switches screens
- Transitions are smooth 300ms slides

---

### Task 3: Splash Screen

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build splash screen HTML + CSS**

- Full-screen cream background with subtle radial gradient (same as strategic doc hero)
- "ALIGN" text in Playfair Display, 48px, sage-dark, letter-spacing 6px
- Green dot span (12px sage circle) after the text
- Tagline: "Movement. Knowledge. Community." — Inter 14px, stone, letter-spacing 2px, uppercase
- Fade-in animation: 800ms ease-in from opacity 0 + slight translateY

**Step 2: Verify**

- Opens with elegant fade-in
- Brand feels premium and calm
- Auto-transitions to Home after 2 seconds

---

### Task 4: Onboarding Flow (4 Steps)

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build onboarding container with progress dots**

- 4 dots at top: sage = current/completed, sand = upcoming
- Back arrow (left) on steps 2-4
- Each step is a sub-screen within the onboarding screen

**Step 2: Step 1 — Create Account**

- Heading: "Welcome to ALIGN." (Playfair, 24px)
- Subtext: "Create your account to get started" (Inter, stone)
- 4 input fields: First name, Last name, Email, Password
- Button: "Continue" (primary, full-width)
- Tapping Continue advances to Step 2

**Step 3: Step 2 — PAR-Q Medical Form**

- Heading: "A few health questions"
- Subtext: "This helps us keep you safe"
- 7 toggle questions (pill-style Yes/No toggles)
- Additional fields below: Injuries (textarea), Medications (textarea), Pregnancy (3-option selector)
- Scrollable content area
- Button: "Continue"

**Step 4: Step 3 — Waiver**

- Heading: "Liability Waiver"
- Scrollable white card with waiver text (lorem-style placeholder)
- Checkbox at bottom: "I have read and agree to the terms"
- Button: "Accept & Continue" (disabled until checkbox)

**Step 5: Step 4 — Welcome**

- Minimalist reformer SVG illustration (sage stroke, simple lines)
- "You're ready." (Playfair, 28px, sage-dark)
- "Welcome to ALIGN. Book your first class." (Inter, stone)
- Button: "Let's go" → navigates to Home, shows tab bar

**Step 6: Verify**

- Progress dots update on each step
- Back arrow works on steps 2-4
- Toggle pills are interactive
- Waiver button stays disabled until checkbox
- Final step transitions to Home with tab bar

---

### Task 5: Home Screen (Content Hub + Quick Booking)

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build Home screen layout**

Scrollable content area above tab bar:

1. **Status bar spacer** (safe-area-inset-top)
2. **Greeting section**: "Good morning, Sarah" (Playfair, 22px) + "Monday, 31 March" (Inter, stone, 13px)
3. **Next class card**: white card with sage left accent border, showing "Reformer Dynamic — Mon 07:00 — Reformer #3", with subtle arrow icon right
4. **Quick actions row**: two buttons side by side — "Book a Class" (primary) | "View Schedule" (secondary)
5. **Katie's Corner section**: label "Katie's Corner" (Inter semibold, 13px uppercase, letter-spacing), then a featured card with placeholder image area (sage-light bg with a quote icon), title "Why Your Core Is Not What You Think It Is", excerpt, "Read →" link in sage
6. **Free Content section**: label "Free This Week" + horizontal scroll container with 3 cards:
   - "5-Min Morning Breathwork" — audio icon, play button circle
   - "20-Min Mat Flow" — exercise icon, "Beginner" badge
   - "Mindful Movement Journal" — document icon
   Each card: white bg, rounded, compact (140px wide), sage accent elements
7. **Community section**: label "Community" + event card: "Walk & Talk — Saturday 9am, Wye Valley Trail" with "RSVP" sage button

**Step 2: Implement interactions**

- Next class card: tappable (shows class detail overlay)
- "Book a Class" → switches to Schedule tab
- "View Schedule" → switches to Schedule tab
- Audio play button toggles play/pause icon (visual only)
- RSVP button toggles to "Going ✓" state

**Step 3: Verify**

- Content scrolls smoothly within screen bounds
- Cards have proper shadows and rounded corners
- Quick actions navigate to Schedule
- Audio and RSVP buttons are interactive
- Feels like a content platform, not a booking-only tool

---

### Task 6: Schedule Screen

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build Schedule layout**

1. **Header**: "Schedule" (Playfair, 22px)
2. **Filter chips row**: horizontal scroll — All (active default), Reformer, Mat, S&C, Breathwork. Active chip: sage bg white text. Inactive: sand bg stone text.
3. **Week selector**: horizontal row of 7 day pills (Mon-Sun). Each shows day abbreviation + date number. Active: sage circle bg. Past: stone text, not tappable. Today highlighted.
4. **Class list**: vertical scrolling list of class cards for selected day

**Step 2: Build class card component**

Each card (white, radius-md, shadow-card, 16px padding):
- Left column: Time block — "07:00" large (Inter semibold 16px) + "50 min" small (caption, stone)
- Right column: Class name (Inter semibold), "Katie" (caption stone), spots indicator
- Spots indicator: coloured dot + text — sage "3 spots left", warning "1 spot left", error "Full — Waitlist"
- Small reformer/mat icon next to class name
- Tap → opens Class Detail overlay

**Step 3: Populate with sample data**

Monday schedule (5 classes from design doc):
- 07:00 Reformer Dynamic — 1/4 (warning)
- 10:00 Mat Pilates — 4/6 (sage)
- 12:00 Reformer Core/Beginners — 3/4 (sage)
- 18:00 Candlelight Pilates — 0/4 (error, Full)
- 19:30 Reformer + Breathwork — 2/4 (sage)

Tuesday-Sunday: 2-3 classes each with varied data

**Step 4: Implement filter and day switching**

- Tapping filter chip: toggles active, filters class list
- Tapping day pill: changes active day, updates class list
- Smooth list update (no jarring reload)

**Step 5: Verify**

- Filter chips toggle correctly
- Day selector highlights active day
- Class cards show correct spot colours
- Tapping a card opens detail overlay (next task)

---

### Task 7: Class Detail & Reformer Spot Selection

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build class detail overlay**

Slide-up overlay (full screen, white bg, rounded top corners):
1. **Handle bar**: 40px wide, 4px height, sand colour, centred at top (drag-to-close visual cue)
2. **Close button**: X icon top-right
3. **Class header**: name (Playfair 22px) + level badge (pill: "All Levels" sage-light bg)
4. **Info row**: 3 items inline — "50 min" | "Monday, 07:00" | "Katie" — each with small icon
5. **Description**: 2-3 sentences from PRD class descriptions (Inter, 15px)
6. **Instructor section**: Katie's small circular avatar placeholder + "Katie Peckham" + "YMCA Level 3 Mat & Reformer Pilates" (caption)
7. **Reformer spot selection** (reformer classes only)
8. **Cancellation policy**: small stone text
9. **CTA fixed bottom**: "Book This Class — £20" sage button, full width, with safe-area bottom padding

**Step 2: Build reformer spot selection UI**

```
┌──────────────────────────────┐
│        INSTRUCTOR             │
│     (label, 11px, stone)      │
│                               │
│   ┌────┐ ┌────┐ ┌────┐ ┌────┐│
│   │  1 │ │  2 │ │  3 │ │  4 ││
│   └────┘ └────┘ └────┘ └────┘│
│                               │
│       ENTRANCE →              │
│    (label, 11px, stone)       │
└──────────────────────────────┘
```

Each reformer spot (60x60px, rounded 8px):
- Available: sage 1.5px border, white bg, sage number
- Taken: stone bg, white number, not tappable
- Selected (user's choice): sage bg, white number

Pre-set: spot 2 is taken (stone), rest available. Tapping toggles selection (only one at a time).

**Step 3: Implement booking flow**

- Tap "Book This Class" → if reformer class and no spot selected, shake the spot selection area
- If spot selected or mat class → show booking confirmation overlay (next task)
- Button text changes for full classes: "Join Waitlist" (secondary style)

**Step 4: Verify**

- Overlay slides up smoothly
- Reformer spots are tappable, visual states correct
- Only one spot selectable at a time
- CTA button works and transitions to confirmation

---

### Task 8: Booking Confirmation Modal

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build confirmation modal**

Centred modal with backdrop blur:
1. **Animated checkmark**: CSS-drawn circle (sage border) + checkmark stroke, animate draw-in over 600ms
2. **"You're booked!"** (Playfair, 24px, sage-dark)
3. **Details card**: white card with class name, date, time, reformer position (#3)
4. **"Add to Calendar"** (secondary button)
5. **"Book this every week?"** — toggle row with text + pill toggle
6. **"Done"** (primary button) → closes modal, returns to Home with next class card updated

**Step 2: Implement checkmark animation**

```css
@keyframes checkmark-circle {
  0% { stroke-dashoffset: 166; }
  100% { stroke-dashoffset: 0; }
}
@keyframes checkmark-check {
  0% { stroke-dashoffset: 50; }
  100% { stroke-dashoffset: 0; }
}
```

SVG checkmark with stroke-dasharray/dashoffset animation on the circle and check paths.

**Step 3: Verify**

- Modal appears with smooth backdrop blur
- Checkmark animates elegantly
- "Done" returns to Home
- Feels celebratory but calm

---

### Task 9: My Bookings Screen

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build Bookings screen**

1. **Header**: "My Classes" (Playfair, 22px)
2. **Segment toggle**: "Upcoming" | "Past" — underline style toggle, sage active
3. **Upcoming list** (default): 3 sample booking cards:
   - Card: white, date header ("Monday, 31 March"), class name, time, reformer position, "Cancel" text button (error colour)
   - Upcoming cards have sage left accent border
4. **Past list**: compact rows, stone text, no actions
   - "Reformer Dynamic — 24 March — Katie"
   - "Mat Pilates — 22 March — Katie"
   - 5-6 entries

**Step 2: Implement cancel interaction**

- Tapping "Cancel" shows confirmation inline: "Cancel this booking?" with "Yes, cancel" (error) and "Keep" (sage) buttons
- Tapping "Yes, cancel" removes the card with fade-out animation

**Step 3: Verify**

- Segment toggle switches between Upcoming and Past
- Cancel flow works with confirmation
- Empty state not needed (always show sample data in mockup)

---

### Task 10: Content Screen (Eduardo Ecosystem)

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build Content screen**

1. **Header**: "Explore" (Playfair, 22px)
2. **Category tabs**: Blog | Free Resources | Events — horizontal, underline active in sage
3. **Featured article** (Blog tab, default): large card with sage-light placeholder image area (with editorial-style quote overlay), title "Why Your Core Is Not What You Think It Is", "By Katie Peckham · 5 min read", excerpt text
4. **Article list below**: 2-3 smaller cards:
   - "The Science Behind Reformer Pilates"
   - "Breathwork: Why 5 Minutes Changes Everything"
   - "Pilates for Rugby Players — Yes, Really"
   Each: title, read time, small category badge

**Step 2: Build Free Resources tab**

- **Audio section**: label "Mindfulness & Breathwork"
  - Card: "5-Min Morning Breathwork" — play circle button, duration, "Free" badge
  - Card: "10-Min Evening Wind-Down" — play circle, duration, "Free" badge
- **Workouts section**: label "Home Workouts"
  - Card: "20-Min Mat Flow" — Beginner badge, duration
  - Card: "15-Min Core Blast" — Intermediate badge, duration
- Play button toggles visual state (play icon → pause icon)

**Step 3: Build Events tab**

- Event cards with date block (sage bg, white text, day number large + month small), title, description, "RSVP" button
- Events:
  - "Walk & Talk" — Saturday 5 April, Wye Valley Trail, 9:00 AM
  - "Coffee Morning @ Coffi Lab" — Saturday 12 April, First Saturday monthly
  - "Farm Retreat — Coming Autumn 2026" — teaser card with "Notify Me" button instead of RSVP

**Step 4: Verify**

- Category tabs switch content correctly
- Play buttons toggle state
- RSVP buttons toggle to "Going ✓"
- Content feels editorial and premium, not generic

---

### Task 11: Profile Screen

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build Profile screen**

1. **Header area**:
   - Avatar circle (56px, sage-light bg, "SM" initials in white Playfair)
   - "Sarah Mitchell" (Playfair, 20px)
   - "sarah.mitchell@email.com" (caption, stone)
2. **Membership card**: sage gradient background, white text, rounded-lg
   - "Monthly 8-Class" plan name
   - "5 classes remaining" with circular progress indicator
   - "Renews 15 April 2026" small text
3. **Progress row**: "12 classes attended" + "3-week streak 🔥" — subtle, inline, stone text with sage accent number
4. **Menu sections** (tappable rows with chevron right):
   - Personal Details
   - Medical Form (PAR-Q)
   - Payment Methods
   - Payment History
   - Notification Preferences
   - Settings
5. **Admin toggle** (bottom): "Switch to Admin View →" text button, sage, only visible in mockup as demonstrable feature

**Step 2: Implement admin toggle**

- Tapping "Switch to Admin View" hides Profile, shows Admin Dashboard (screen 9)
- Admin Dashboard has reverse toggle: "Switch to Client View →"

**Step 3: Verify**

- Membership card looks premium with sage gradient
- Progress is subtle and encouraging, not gamified
- Menu items have hover/active states
- Admin toggle switches screens

---

### Task 12: Admin Dashboard (Katie's View)

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Build Admin Dashboard**

1. **Header**: "Good morning, Katie" (Playfair, 22px) + "Admin" badge (sage pill)
2. **Today's revenue**: "£160" (Playfair, 36px, sage-dark) + "Today's revenue" label
3. **Today's classes**: 3 cards:
   - "07:00 Reformer Dynamic" — "4/4" badge (FULL, error bg) — tap to expand roster
   - "10:00 Mat Pilates" — "4/6" badge (sage bg)
   - "18:00 Candlelight Pilates" — "3/4" badge (sage bg)
4. **Alerts section**: warning card with left amber border:
   - "New signup: Helen Davies"
   - "PAR-Q flag: bone/joint problem"
   - "Review →" link
5. **Quick actions**: 3 buttons in grid:
   - "View Roster" (primary)
   - "Client List" (secondary)
   - "Send Notification" (secondary)
6. **Toggle**: "Switch to Client View →" at bottom

**Step 2: Build expandable roster (mini)**

- Tapping a class card expands to show:
  - Reformer positions 1-4 with client names
  - e.g., "1: Sarah M." / "2: Tom R." / "3: Helen D. ⚠️" / "4: Available"
  - Flag icon on Helen (PAR-Q alert)

**Step 3: Verify**

- Revenue number is prominent and Playfair
- Alert card stands out with warning colour
- Roster expands/collapses smoothly
- Toggle returns to Profile/Client view

---

### Task 13: Final Polish & Delivery

**Files:**
- Modify: `app-mockup/index.html`

**Step 1: Add PWA manifest inline and meta tags**

Ensure apple-mobile-web-app-capable, theme-color (#F5F0EB), status-bar-style, and appropriate meta tags for full-screen iPhone experience.

**Step 2: Add micro-interactions polish**

- Button press: scale(0.97) on :active
- Card tap: subtle background colour shift
- Tab switch: icon morphs with subtle scale
- Scroll: momentum scrolling (-webkit-overflow-scrolling: touch)
- Focus states on all inputs (sage border glow)

**Step 3: Test on mobile viewport**

Open in Chrome DevTools, test on:
- iPhone 14 Pro (390x844)
- iPhone SE (375x667)
- iPhone 15 Pro Max (430x932)

Confirm: tab bar doesn't overlap content, safe areas work, text is readable, touch targets are adequate.

**Step 4: Copy to Align Studio folder**

```bash
cp app-mockup/index.html "/Users/macbookjoaohomem/Documents/VSCode_Projects/Product Research & Development/Align_Studio/app-mockup/index.html"
```

**Step 5: Verify final delivery**

Open on actual iPhone (or closest simulation). Navigate through complete flow:
1. Splash → 2. Home → 3. Schedule → 4. Class Detail → 5. Reformer Selection → 6. Booking Confirmation → 7. My Bookings → 8. Content → 9. Profile → 10. Admin Dashboard

Every screen must feel premium, calm, and unmistakably ALIGN.

---

## Execution Notes

- **Single file**: all HTML, CSS, and JS in one `index.html` — no external dependencies beyond Google Fonts
- **No build step**: open the file directly in any browser
- **Data is hardcoded**: all sample classes, content, and user data are JS objects at the top of the script section
- **Working directory**: `/Users/macbookjoaohomem/Documents/VSCode_Projects/avant-garde_design/app-mockup/`
- **Final delivery also copied to**: `/Users/macbookjoaohomem/Documents/VSCode_Projects/Product Research & Development/Align_Studio/app-mockup/`
