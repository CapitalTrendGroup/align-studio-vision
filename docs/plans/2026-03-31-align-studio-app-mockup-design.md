# ALIGN. Studio App — Mockup Design Document

**Version**: 1.0
**Date**: 31 March 2026
**Author**: Product Research & Development Team
**Format**: Single-file interactive HTML mockup (PWA-ready)
**Delivery**: Katie opens on iPhone Safari, navigates as if using the real app

---

## 1. Approach

### Format
Single HTML file with embedded CSS and vanilla JavaScript. No external dependencies beyond Google Fonts. PWA meta tags allow Katie to add to home screen for full-screen app experience.

### Technical Constraints
- Viewport locked to device height (100vh), scroll only within screen content
- Bottom tab bar fixed, 5 tabs with SVG icons
- Screen transitions: 300ms ease-out slide left/right
- All data simulated via JavaScript objects (no backend)
- Responsive: designed for iPhone but works on any mobile browser

---

## 2. Visual Design System

### Colour Palette (from PRD Section 8.1)

| Token | Hex | Usage |
|-------|-----|-------|
| Sage | `#8B9F82` | Buttons, active icons, CTAs, accents |
| Cream | `#F5F0EB` | App background |
| White | `#FFFFFF` | Cards, modals, inputs |
| Charcoal | `#2C2C2C` | Primary text |
| Stone | `#A69F95` | Secondary text, inactive icons |
| Sand | `#E8E0D8` | Dividers, subtle backgrounds |
| Success | `#6B8F71` | Booking confirmed, payment success |
| Warning | `#D4A574` | Low spots, expiring packs |
| Error | `#C47A7A` | Payment failed, validation errors |

### Typography (from PRD Section 8.2)

| Element | Font | Weight | Size |
|---------|------|--------|------|
| Logo / Screen headings | Playfair Display (serif) | SemiBold | 22-32px |
| Section headings | Inter (sans-serif) | SemiBold | 18px |
| Body text | Inter | Regular | 16px |
| Captions / metadata | Inter | Regular | 13-14px |
| Buttons | Inter | SemiBold | 16px |

### Component Styling (from PRD Section 8.3)

- **Cards**: white bg, 12px border-radius, shadow `0 2px 8px rgba(0,0,0,0.06)`
- **Primary buttons**: sage bg, white text, 8px radius, full-width on forms
- **Secondary buttons**: white bg, sage border + text
- **Input fields**: white bg, 1px sand border, 8px radius, sage border on focus
- **Tab bar**: white bg, sage active icon, stone inactive icon
- **Touch targets**: minimum 44x44px

### Animations (from PRD Section 8.7)

- Screen transitions: 300ms ease-out slide
- Button press: scale(0.97) with 100ms
- Booking confirmed: CSS checkmark animation
- Card interactions: subtle translateY(-2px) on active
- Everything calm, intentional — zero aggressive motion

---

## 3. Screen Map (12 screens)

### Tab Bar
```
[ Home | Schedule | Bookings | Content | Profile ]
```

### Screen 0 — Splash
- Cream background with subtle radial gradient
- "ALIGN." in Playfair Display, large, centred, sage-dark
- Green dot (.) brand mark
- "Movement. Knowledge. Community." tagline
- Auto-transition to Home after 2s

### Screen 1 — Onboarding (4-step wizard)
Progress indicator: 4 dots (sage = completed, sand = pending)

**Step 1 — Create Account**
- Heading: "Welcome to ALIGN." (Playfair)
- Fields: First name, Last name, Email, Password
- Button: "Continue" (sage, full-width)

**Step 2 — Medical Form (PAR-Q)**
- Heading: "A few health questions"
- Subtext: "This helps us keep you safe"
- 7 Yes/No toggle questions (elegant pill toggles)
- Additional fields: injuries, medications, pregnancy status

**Step 3 — Waiver**
- Scrollable text in white card
- Checkbox: "I have read and agree to the terms"
- Button: "Accept & Continue"

**Step 4 — Welcome**
- Minimalist reformer illustration (sage line art)
- "You're ready." (Playfair, large)
- Button: "Book your first class" → navigates to Home

### Screen 2 — Home (Tab 1) — Content Hub + Quick Booking
This is the key differentiator. Home is NOT a booking dashboard — it's a wellness content hub that also makes booking effortless.

**Layout (top to bottom):**
1. **Greeting**: "Good morning, Sarah" (Playfair) + date
2. **Next class card** (if booked): date, time, class type, reformer position — tap to view
3. **Quick actions**: "Book a Class" | "View Schedule" — two sage outline buttons
4. **Katie's Corner**: featured blog post card with Katie's photo, title, excerpt, "Read" link
5. **Free Content**: horizontal scroll — mindfulness audio card, home workout card, breathwork card — each with mini play button or duration badge
6. **Community**: next Walk & Talk or Coffee Morning event card with date + "RSVP" button
7. **New This Week**: badge "New" on fresh content

### Screen 3 — Schedule (Tab 2)
**Layout:**
1. **Filter chips**: All | Reformer | Mat | S&C | Breathwork
2. **Week selector**: horizontal scrollable Mon-Sun, active day in sage circle
3. **Class cards** (vertical list):
   - Time: "07:00 — 07:50"
   - Class name + icon (reformer silhouette / mat)
   - Instructor: "Katie"
   - Duration: "50 min"
   - Spots: colour-coded indicator (sage 3-4, warning 1-2, error full)
   - Tap → opens Class Detail

### Screen 4 — Class Detail (slide-up overlay)
1. **Header**: class name + level badge (Beginner / All Levels / Intermediate)
2. **Info row**: duration, instructor, date, time
3. **Description**: 2-3 sentences (from PRD class descriptions)
4. **Instructor mini-bio**: Katie's photo + qualifications
5. **Reformer spot selection** (reformer classes only):
   ```
   ┌─────────────────────────────┐
   │         INSTRUCTOR           │
   │                              │
   │  ┌───┐  ┌───┐  ┌───┐  ┌───┐ │
   │  │ 1 │  │ 2 │  │ 3 │  │ 4 │ │
   │  └───┘  └───┘  └───┘  └───┘ │
   │                              │
   │          ENTRANCE →          │
   └─────────────────────────────┘
   ```
   States: sage outline = available, stone filled = taken, sage filled = your selection
6. **Cancellation policy** (small stone text)
7. **CTA**: "Book This Class — £20" (sage, full-width, fixed bottom)

### Screen 5 — Booking Confirmation (modal overlay)
- Animated checkmark (CSS keyframes, sage colour)
- "You're booked!" (Playfair, large)
- Class details: name, date, time, reformer position
- "Add to Calendar" (secondary button)
- "Book this class every week?" toggle option
- "Done" button → Home with updated next class card

### Screen 6 — My Bookings (Tab 3)
**Sections:**
1. **Upcoming** (default view): cards with date, time, class name, reformer position, "Cancel" button
2. **Past**: compact list with stone text, class attended, date
3. **Waitlist**: if any, shows position ("You are #2")
4. **Empty state**: reformer line illustration + "No upcoming classes. Time to book one?" + "Browse Schedule" button

### Screen 7 — Content (Tab 4)
The Eduardo Ecosystem content platform.

**Layout:**
1. **Featured article**: large card with image placeholder, title, Katie's name, read time
2. **Category tabs**: Blog | Free Resources | Events
3. **Blog**: article cards (Pilates science, wellness tips, mindfulness)
4. **Free Resources**:
   - Audio cards with play button + duration (e.g., "5-min Morning Breathwork")
   - Home workout cards with level + duration (e.g., "20-min Core — Beginner")
5. **Events**:
   - Walk & Talk — next date, location, "RSVP" button
   - Coffee Morning @ Coffi Lab — date, "RSVP"
   - Farm Retreat — teaser card with "Coming Soon" or "Learn More"

### Screen 8 — Profile (Tab 5)
1. **Avatar**: circle with initials (or placeholder)
2. **Name + email**
3. **Membership card**: sage background, plan name, remaining credits, renewal date
4. **Progress**: "12 classes attended" + streak "3 weeks in a row" (subtle, not gamified)
5. **Menu sections** (tappable rows):
   - Personal Details
   - Medical Form (PAR-Q)
   - Payment Methods
   - Payment History
   - Notification Preferences
   - Settings (logout, delete account)
6. **Admin toggle** (Katie only): "Switch to Admin" at bottom

### Screen 9 — Admin Dashboard (Katie's view)
1. **Header**: "Good morning, Katie" + "Admin" badge (sage)
2. **Today's classes**: cards showing time, class name, booking count (e.g., "4/4 FULL"), tap to view roster
3. **Alerts card**: new signups with PAR-Q flag warnings (warning colour)
4. **Revenue today**: £ amount in large Playfair
5. **Quick actions**: View Full Roster | Client List | Send Notification
6. **Toggle**: "Switch to Client View" at bottom

---

## 4. Navigation & Interaction Model

### Tab Bar Navigation
- 5 tabs: Home, Schedule, Bookings, Content, Profile
- Active tab: sage icon + label, inactive: stone icon only
- Tap switches screens with slide transition (left/right based on tab position)

### Screen Stack
- Tab screens are primary (slide horizontally)
- Detail screens overlay (slide up from bottom)
- Modals (confirmation, onboarding steps) fade in with backdrop blur

### Simulated Interactions
- Reformer spot selection: tap to toggle available spots
- Filter chips on Schedule: toggle active/inactive
- Week selector: tap to change day, updates class list
- Booking flow: Class card → Detail → Select spot → Confirm → Success modal
- Admin/Client toggle: switches between Profile and Admin Dashboard
- Audio play buttons: visual state change (play/pause icon) — no actual audio

### Back Navigation
- Detail overlays: "X" close button or swipe down
- Onboarding: "Back" arrow to previous step
- Tab bar always accessible (except during onboarding and modals)

---

## 5. Content & Data (Simulated)

### Sample Classes (Monday schedule)
| Time | Class | Spots | Status |
|------|-------|-------|--------|
| 07:00 | Reformer Dynamic | 1 of 4 | Almost full (warning) |
| 10:00 | Mat Pilates | 4 of 6 | Available (sage) |
| 12:00 | Reformer Core/Beginners | 3 of 4 | Available (sage) |
| 18:00 | Candlelight Pilates | 0 of 4 | Full — Waitlist (error) |
| 19:30 | Reformer + Breathwork | 2 of 4 | Available (sage) |

### Sample User
- Name: Sarah Mitchell
- Membership: Monthly 8-Class (5 remaining)
- Next class: Monday 07:00 Reformer Dynamic, Reformer #3
- Classes attended: 12 total, 3-week streak

### Sample Content
- Blog: "Why Your Core Is Not What You Think It Is" by Katie
- Audio: "5-Minute Morning Breathwork" (free)
- Workout: "20-Min Mat Flow — Beginner" (free)
- Event: "Walk & Talk — Saturday 9am, Wye Valley Trail"
- Event: "Coffee Morning @ Coffi Lab — First Saturday of the Month"

### Admin Sample Data
- Today's bookings: 14 across 5 classes
- New signup: Helen Davies, PAR-Q flag (joint problem)
- Revenue today: £160

---

## 6. Delivery

### Files
- `app-mockup/index.html` — the complete interactive mockup
- Saved in both:
  - `/avant-garde_design/` (working project)
  - `/Align_Studio/` (client documentation folder)

### How Katie Uses It
1. Receives link or file
2. Opens on iPhone Safari
3. Taps "Share" → "Add to Home Screen"
4. Opens from home screen — full-screen, no browser chrome
5. Navigates between tabs, taps through booking flow, explores content
6. Sees the app as it will feel when built

---

## 7. What This Mockup Proves

1. **Not another TeamUp** — Content-first home screen shows ALIGN. is a wellness platform
2. **Premium brand experience** — Every screen feels like walking into the studio
3. **Booking in 3 taps** — Schedule → Class → Confirm (returning users)
4. **Community built-in** — Events, Katie's Corner, free content
5. **Eduardo Ecosystem Chain** — Content drives engagement beyond booking
6. **Katie's admin reality** — 30-second morning check, all info at a glance
7. **Gender-neutral** — Sage/cream palette, no feminine cues, inclusive language
