# ALIGN. Studio App — Product Requirements Document

**Version**: 1.0
**Date**: 26 March 2026
**Author**: Product Research & Development Team
**Developer**: Eduardo Garufi
**Stakeholder**: Katie Peckham, Founder — ALIGN. Studio

---

## 1. Product Overview

### 1.1 Vision Statement

> "An app that shows Align isn't just a studio, it's also a community, and a brand committed to bringing you knowledgeable information and guidance from beyond the studio."
> — Katie Peckham

The ALIGN. app is not a booking tool with a logo on it. It is the digital embodiment of the ALIGN. brand — premium, warm, inclusive, and community-driven. Every screen, every interaction, and every notification must feel like walking into the studio itself: calm, considered, and unmistakably ALIGN.

### 1.2 Key Differentiators vs Existing Platforms

| Feature | TeamUp / Mindbody / Glofox | ALIGN. App |
|---------|---------------------------|------------|
| Branding | Generic fitness platform skin | Fully bespoke ALIGN. brand experience |
| Reformer booking | Basic class booking | Visual spot selection (choose your reformer) |
| Medical intake | External forms or none | In-app PAR-Q+ integrated into onboarding |
| Community | Non-existent or bolted on | Content feed, events, messaging — native |
| Feel | "Just a platform" (Katie's words) | Premium, warm, personal |
| Payment | Platform-controlled | Stripe direct (2-3% fees, not 30%) |

### 1.3 Platform & Technical Summary

| Attribute | Detail |
|-----------|--------|
| Platforms | iOS (15+) and Android (10+) |
| Framework | React Native (Expo) |
| Payment | Stripe API (brick-and-mortar exemption — no Apple/Google IAP required) |
| Timeline | Mockup: 2-3 days. Full MVP build: 2 weeks. Launch target: June 2026 |
| App Store | "ALIGN. Pilates" — submit 3-4 weeks before launch (review takes 2-5 days) |

### 1.4 Design Philosophy

The app must feel like an extension of the physical studio: serene, premium, and unmistakably ALIGN. It is not a utility — it is a brand experience. Every screen should pass the test: *"Would this feel at home on a mood board next to the studio interior?"*

---

## 2. User Personas

### Persona 1 — Sarah, 28, Working Professional

| Attribute | Detail |
|-----------|--------|
| Occupation | Marketing manager, commutes to Bristol |
| Goal | Early morning reformer classes before work |
| Behaviour | Books on Sunday evening for the whole week. Values speed and reliability. |
| Pain point | Hates clunky booking apps. Wants to book in 3 taps. |
| App usage | Books classes, checks schedule, pays via stored card |
| Quote | "I just want to tap, book, done." |

### Persona 2 — Tom, 35, Rugby Player

| Attribute | Detail |
|-----------|--------|
| Occupation | Semi-professional rugby, works in construction |
| Goal | Injury recovery and flexibility improvement |
| Behaviour | Sceptical about Pilates at first. Discovered ALIGN. through Instagram rugby content. |
| Pain point | Intimidated by "wellness" spaces. Needs the app to feel neutral, not feminine. |
| App usage | Checks class descriptions carefully, reads instructor bio, books single sessions |
| Quote | "I didn't think this was for me, but the app didn't make me feel like an outsider." |

### Persona 3 — Helen, 52, Nervous Beginner

| Attribute | Detail |
|-----------|--------|
| Occupation | Retired teacher |
| Goal | Start exercising after GP recommendation. Slightly anxious about group classes. |
| Behaviour | Needs reassurance. Will read every class description and FAQ before booking. |
| Pain point | Confused by complex apps. Needs clear guidance through medical form and first booking. |
| App usage | Reads content, checks "what to expect", books beginner classes |
| Quote | "I just want to know I won't be the only one who doesn't know what they're doing." |

### Persona 4 — Walk-In Visitor

| Attribute | Detail |
|-----------|--------|
| Context | Tourist walking past, scans QR code on the studio door, or enters on impulse |
| Goal | Try a class today or tomorrow |
| Behaviour | Low commitment. Needs frictionless sign-up. May use the in-studio iPad. |
| Pain point | Will abandon if sign-up takes more than 3 minutes. |
| App usage | Quick profile, medical form, single class purchase |
| Quote | "I'm only in town for the weekend but this looks lovely." |

### Persona 5 — Katie (Admin / Instructor)

| Attribute | Detail |
|-----------|--------|
| Role | Sole instructor and business owner at launch |
| Goal | See today's bookings, review new clients' medical forms, manage schedule, communicate with clients |
| Behaviour | Checks app first thing in the morning and between classes |
| Pain point | Cannot spend more than 5 minutes on admin between classes. Needs a dashboard that gives her everything at a glance. |
| App usage | Admin panel: bookings, client list, medical forms, schedule management, messaging |
| Quote | "I need to see who's coming, if anyone's new, and whether they have any medical flags — in 30 seconds." |

---

## 3. Information Architecture

### 3.1 Client App — Screen Map

```
[Tab Bar: Home | Schedule | Bookings | Content | Profile]

Home
├── Welcome banner (personalised greeting)
├── Next upcoming class card
├── Quick actions (Book a class, View schedule)
├── Latest content preview (1-2 cards)
└── Community event highlight

Schedule
├── Week view (default) / Month view toggle
├── Date selector (3-month forward window)
├── Class cards (filterable by type)
│   ├── Time, duration, type, instructor
│   ├── Spots remaining indicator
│   └── Tap → Class detail → Book
└── Filter: Class type, instructor, time of day

Bookings (My Classes)
├── Upcoming bookings (chronological)
│   └── Each: class details, cancel button, add to calendar
├── Past bookings (history)
└── Waitlist entries

Content
├── Blog articles (Pilates science, wellness)
├── Free resources (mindfulness audio, home workouts)
├── Community events (Walk & Talk, Coffee mornings)
└── Studio announcements

Profile
├── Personal details (edit)
├── Medical form (PAR-Q) — view/edit
├── Membership / class pack status
├── Payment methods (Stripe)
├── Payment history / receipts
├── Emergency contact
├── Notification preferences
├── Settings (logout, delete account, privacy)
```

### 3.2 Admin Panel — Screen Map (Katie's View)

```
Admin Dashboard
├── Today's overview (classes, bookings, new signups)
├── Revenue snapshot
└── Alerts (new medical forms to review, cancellations)

Class Management
├── Create / edit / cancel class
├── View class roster
├── Manual booking (phone / walk-in)
└── Recurring class templates

Client Management
├── Client list (searchable)
├── Client detail → profile, medical form, booking history, notes
└── New client (manual creation for phone bookings)

Messaging
├── Broadcast to all clients
├── Class-specific announcement
└── Direct message inbox

Schedule Management
├── Weekly timetable view
├── Drag-and-drop schedule editor (Phase 2)
└── Instructor assignment (Phase 2)

Payments
├── Transaction history
├── Revenue by period
└── Refund processing
```

### 3.3 Navigation Structure

**Client app**: Bottom tab bar with 5 tabs — Home, Schedule, Bookings, Content, Profile. This is the standard pattern for booking-centric apps and provides one-tap access to all primary functions.

**Admin panel**: Separate admin section accessible via a toggle in Katie's profile (she uses the same app, with an admin role). The admin panel uses a sidebar or top-tab navigation.

---

## 4. Feature Specification — MVP (Phase 1)

> **MVP Definition**: Everything in this section MUST be built for the June 2026 launch. This is what Eduardo delivers in the 2-week build window.

---

### 4.1 Onboarding & Authentication

**Description**: First-time users create an account, complete their medical screening, and set up a profile before they can book any class. The flow must feel welcoming, not bureaucratic.

**User Stories**

| # | As a... | I want to... | So that... |
|---|---------|-------------|------------|
| 1 | New user | Sign up with email and password | I can create my account |
| 2 | New user | Complete the PAR-Q medical form | The studio knows my health status before my first class |
| 3 | New user | Accept the liability waiver | I can proceed to book classes |
| 4 | New user | Add my name, photo (optional), and emergency contact | My profile is complete |
| 5 | Walk-in user | Create a profile on the studio iPad | I can book without downloading the app immediately |
| 6 | Returning user | Log in with email/password | I can access my account |

**Acceptance Criteria**

- Sign-up requires: email, password (min 8 chars), first name, last name
- Social login (Apple Sign-In, Google) — include if achievable within timeline, otherwise email-only for MVP
- PAR-Q form is mandatory before first booking. User cannot skip it.
- PAR-Q answers are stored and visible to admin (Katie)
- Waiver text is displayed in full; user must scroll to bottom and tap "I Agree"
- Profile photo is optional (camera or gallery)
- Emergency contact: name, relationship, phone number — mandatory
- iPad mode: simplified flow (no app download required — could be a web view or a dedicated kiosk mode within the app)

**PAR-Q Medical Form — Standard Questions (UK)**

The following 7 questions must be presented as Yes/No toggles:

1. Has your doctor ever said that you have a heart condition and that you should only do physical activity recommended by a doctor?
2. Do you feel pain in your chest when you do physical activity?
3. In the past month, have you had chest pain when you were not doing physical activity?
4. Do you lose your balance because of dizziness or do you ever lose consciousness?
5. Do you have a bone or joint problem that could be made worse by a change in your physical activity?
6. Is your doctor currently prescribing drugs for your blood pressure or heart condition?
7. Do you know of any other reason why you should not do physical activity?

**Additional fields:**
- Current injuries or conditions (free text)
- Medications (free text)
- Pregnancy status (Yes/No/Prefer not to say)
- Date of last medical check-up (optional)
- GP name and surgery (optional)

**If any PAR-Q answer is "Yes"**: Display message — *"We recommend consulting your GP before attending classes. You may still book, but please speak with Katie before your first session."* Flag the profile for Katie's review in the admin panel.

**Edge Cases**
- User closes app mid-onboarding: save progress, resume on next open
- User refuses waiver: cannot proceed to booking. Display message explaining why the waiver is required.
- iPad walk-in: must still complete PAR-Q. No shortcuts on medical screening.
- Under 16: require parent/guardian consent field (name + signature checkbox)

**UI Notes**
- Onboarding should be a multi-step wizard (progress indicator at top)
- Steps: 1) Create account → 2) Medical form → 3) Waiver → 4) Profile details → 5) Welcome screen
- Welcome screen shows a warm message: *"Welcome to ALIGN. You're ready to book your first class."*
- Use the Cream background, Sage accent buttons, serif heading for "Welcome to ALIGN."

---

### 4.2 Class Schedule & Booking

**Description**: The core of the app. Clients browse the schedule, view class details, select a reformer spot (for reformer classes), and book. The experience must be fast — 3 taps from schedule to confirmed booking for returning users.

**User Stories**

| # | As a... | I want to... | So that... |
|---|---------|-------------|------------|
| 1 | Client | See the weekly class schedule | I can plan when to attend |
| 2 | Client | Filter classes by type (Reformer, Mat, S&C) | I find the class I want quickly |
| 3 | Client | See how many spots remain | I know if there is space |
| 4 | Client | Choose my specific reformer position | I get my preferred spot |
| 5 | Client | Book a class with one tap (if payment method stored) | Booking is frictionless |
| 6 | Client | Cancel a booking within the cancellation window | I free up the spot for others |
| 7 | Client | Join a waitlist when a class is full | I get notified if a spot opens |
| 8 | Client | Set a recurring weekly booking | I don't have to re-book every week |
| 9 | Admin | See who is booked into each class | I can prepare for the session |
| 10 | Admin | Manually add a booking for a phone/walk-in client | All bookings are in one system |

**Class Types & Capacities**

| Class Type | Capacity | Spot Selection | Room Config |
|------------|----------|----------------|-------------|
| Reformer Dynamic | 4 | Yes — choose reformer 1-4 | Reformer layout |
| Reformer Core/Beginners | 4 | Yes — choose reformer 1-4 | Reformer layout |
| Reformer + Breathwork | 4 | Yes — choose reformer 1-4 | Reformer layout |
| Candlelight Pilates (Reformer) | 4 | Yes — choose reformer 1-4 | Reformer layout |
| Mat Pilates | 6 | No — first come, first served | Mat layout |
| Strength & Conditioning | 6 | No | Mat layout |
| Outdoor Pilates | 8-10 | No | N/A (outdoor) |

**Reformer Spot Selection UI**

Display a top-down visual diagram of the studio room showing 4 reformer positions. Each position shows:
- Position number (1-4)
- Status: Available (Sage outline) / Booked (filled Stone) / Selected (filled Sage)
- Tap to select/deselect

```
┌─────────────────────────────┐
│         INSTRUCTOR          │
│         ─────────           │
│                             │
│  ┌───┐  ┌───┐  ┌───┐  ┌───┐│
│  │ 1 │  │ 2 │  │ 3 │  │ 4 ││
│  └───┘  └───┘  └───┘  └───┘│
│                             │
│          ENTRANCE →         │
└─────────────────────────────┘
```

**Calendar / Schedule View**

- Default view: **Week view** (Mon-Sun) with horizontal date picker at top
- Tap any date to see that day's classes listed vertically
- Month view available via toggle (shows dots on days with classes)
- 3-month forward booking window from today
- Past dates are greyed out and not tappable

**Class Card (in schedule list)**

Each class card displays:
- Time (e.g., "07:00 — 07:50")
- Class name (e.g., "Reformer Dynamic")
- Instructor name ("Katie")
- Duration (e.g., "50 min")
- Spots remaining (e.g., "2 of 4 spots left") — colour-coded: green (3-4), amber (1-2), red (full)
- Class type icon (reformer silhouette / mat silhouette)

Tapping a class card opens the **Class Detail Screen**.

**Class Detail Screen**

- Full class description (what to expect, what to bring, difficulty level)
- Instructor name and mini-bio
- Date, time, duration
- Spots remaining
- Reformer spot selection (if reformer class)
- "Book This Class" button (Sage, full-width)
- Price displayed (if single class purchase needed)
- Cancellation policy reminder text

**Cancellation Policy**

- Cancellations **12+ hours before** class: full refund / credit restored
- Cancellations **2-12 hours before** class: 50% credit (or no refund — Katie to decide)
- Cancellations **under 2 hours** / no-show: no refund
- Display cancellation policy clearly on booking confirmation and class detail screens
- **Note for Katie**: These times are configurable in admin. Start with 12-hour full / 2-hour no-refund and adjust based on experience.

**Waitlist**

- When a class is full, the "Book" button changes to "Join Waitlist"
- Waitlist is first-come, first-served
- When a spot opens (cancellation), the first person on the waitlist receives a push notification: *"A spot just opened in Reformer Dynamic at 07:00 on Monday! You have 30 minutes to confirm."*
- If not confirmed within 30 minutes, the spot moves to the next person on the waitlist
- Waitlist position is visible to the client (e.g., "You are #2 on the waitlist")

**Recurring Booking**

- After booking a class, offer: *"Book this class every week?"*
- If accepted, auto-book the same class for the next 4 weeks (configurable)
- Recurring bookings count against class packs / memberships as normal
- Client receives confirmation for each auto-booked session
- Client can cancel individual sessions or the entire recurring series

**Edge Cases**
- Client tries to book but has no payment method / pack / membership: redirect to payment screen
- Client tries to book but PAR-Q has a "Yes" answer and Katie hasn't reviewed: show message — *"Please speak with Katie before booking your first class. We'll be in touch shortly."*
- Two clients tap the same last spot simultaneously: first-come-first-served at the server level. Second client sees "This spot was just taken" and is offered the waitlist.
- Class is cancelled by admin: all booked clients receive push notification and automatic refund/credit
- Client tries to book two overlapping classes: block with message — *"You already have a booking at this time."*

**UI Notes**
- Schedule screen uses the Cream background
- Class cards are white with subtle shadow, rounded corners
- Sage accent for available spots and booking button
- Stone text for secondary information
- Smooth transition animation when opening class detail from card

---

### 4.3 Payments (Stripe Integration)

**Description**: All payments are processed through Stripe. The app qualifies for Apple and Google's physical goods/services exemption because ALIGN. is a brick-and-mortar studio selling in-person class attendance — not digital content. This means Stripe's 2-3% fees apply instead of the 30% app store commission.

**User Stories**

| # | As a... | I want to... | So that... |
|---|---------|-------------|------------|
| 1 | Client | Add my credit/debit card securely | I can pay for classes |
| 2 | Client | Buy a single class | I can try without commitment |
| 3 | Client | Buy a class pack (5 or 10 classes) | I get a better per-class rate |
| 4 | Client | Subscribe to a monthly membership | I have predictable access |
| 5 | Client | See my payment history and receipts | I can track my spending |
| 6 | Admin | See revenue by day/week/month | I understand my business performance |
| 7 | Admin | Issue a refund | I can handle cancellations fairly |

**Pricing Structure (MVP)**

| Product | Price | Notes |
|---------|-------|-------|
| Single Reformer Class | £20 | One-time purchase |
| Single Mat/S&C Class | £14 | One-time purchase |
| Drop-in Reformer | £22 | Walk-in, no advance booking |
| Intro Offer (3 Reformer Classes) | £45 | £15/class — new clients only, one-time |
| 5-Class Pack (Reformer) | £90 | £18/class — expires 2 months from purchase |
| 10-Class Pack (Reformer) | £180 | £18/class — expires 4 months from purchase |
| Monthly 8-Class Membership | £75/month | Auto-renewing via Stripe subscription |
| Monthly Unlimited Membership | £99/month | Auto-renewing via Stripe subscription |
| Private 1-to-1 Session | £55 | Booked separately (admin creates the slot) |

**Note for Katie**: These prices are from the vision document. Confirm before build. Founding member pricing (e.g., £79/month unlimited for first 20 members) is highly recommended — implement as a separate product in Stripe with limited quantity.

**Acceptance Criteria**

- Card details are entered via Stripe's prebuilt UI (Stripe Elements / Payment Sheet) — ALIGN. never sees or stores raw card numbers
- Saved cards are displayed as last 4 digits with card brand icon
- Clients can add multiple cards and set a default
- Class pack purchases deduct one credit per booking. Remaining credits shown in profile.
- Membership subscriptions are managed via Stripe Billing (auto-renewal, cancellation, pause)
- Receipts are generated automatically and viewable in-app (also emailed via Stripe)
- Admin can issue full or partial refunds from the admin panel
- Failed payments trigger a push notification and 3-day grace period before membership suspension

**Edge Cases**
- Card payment fails at booking time: show Stripe error message, suggest trying another card
- Class pack expires with unused credits: credits are forfeited (display expiry date prominently in profile)
- Client cancels membership mid-cycle: access continues until end of current billing period
- Stripe webhook fails: implement retry logic; log failed webhooks for manual review
- Refund on a class pack: refund one class credit value, not the pack price (unless full pack refund)

**Technical Notes**
- Use Stripe Payment Sheet (prebuilt UI) for card collection
- Use Stripe Customer objects to store payment methods per user
- Use Stripe Subscriptions for memberships
- Use Stripe Checkout or Payment Intents for one-time purchases
- Implement Stripe webhooks for: `payment_intent.succeeded`, `invoice.paid`, `invoice.payment_failed`, `customer.subscription.updated`, `customer.subscription.deleted`
- All Stripe API calls happen server-side. The app never directly calls Stripe APIs.

---

### 4.4 Client Profile

**Description**: The client's personal hub — their details, medical form, bookings, payments, and membership status in one place.

**Sections**

| Section | Contents |
|---------|----------|
| Personal Details | Name, email, phone, photo (optional), date of birth |
| Emergency Contact | Name, relationship, phone number |
| Medical Form (PAR-Q) | View responses, edit (triggers admin review if changed) |
| Fitness Info | Self-reported level (Beginner / Intermediate / Advanced), goals (free text) |
| Membership Status | Current plan, renewal date, remaining class pack credits, expiry dates |
| Payment Methods | Saved cards (add/remove/set default) |
| Payment History | List of transactions with date, amount, description, receipt link |
| Booking History | Past classes attended (date, class type, instructor) |
| Notification Preferences | Toggle: class reminders, new classes, community, marketing |
| Account | Change password, logout, delete account (GDPR), privacy policy |

**Acceptance Criteria**
- All personal data is editable
- PAR-Q edits trigger a flag for admin review
- Membership status is always current (synced with Stripe)
- "Delete Account" permanently removes all personal data within 30 days (GDPR requirement)
- Payment history shows last 12 months; older records downloadable

---

### 4.5 Push Notifications

**Description**: Timely, relevant notifications that enhance the experience without being intrusive. Every notification must pass the test: *"Would I be glad I received this?"*

**MVP Notification Types**

| Trigger | Timing | Message Example |
|---------|--------|-----------------|
| Booking confirmed | Immediate | "You're booked! Reformer Dynamic, Monday 07:00. See you there." |
| Class reminder | 24 hours before | "Your Reformer Dynamic class is tomorrow at 07:00. Don't forget your grip socks!" |
| Class reminder | 1 hour before | "Your class starts in 1 hour. See you soon." |
| Waitlist spot opened | Immediate | "A spot just opened in Reformer Dynamic at 07:00! Confirm within 30 minutes." |
| Payment confirmed | Immediate | "Payment received: £20.00 for Reformer Dynamic. Receipt in your profile." |
| Class cancelled by admin | Immediate | "Reformer Dynamic on Monday 07:00 has been cancelled. Your credit has been restored." |
| Booking cancelled by client | Immediate | "Your booking for Reformer Dynamic on Monday 07:00 has been cancelled." |
| Payment failed | Immediate | "Your payment couldn't be processed. Please update your card to keep your membership active." |

**Phase 2 Notification Types** (not MVP)
- New class type added
- Re-engagement ("We haven't seen you in 2 weeks — your reformer misses you!")
- Community event announcements
- New content published

**Acceptance Criteria**
- Notifications require explicit opt-in (iOS requires permission prompt; Android auto-enabled but respect preferences)
- All notification types are individually toggleable in profile settings
- Notifications link directly to the relevant screen (tap reminder → class detail)
- Badge count on app icon reflects unread notifications
- Silent hours: no notifications between 21:00 and 07:00 (configurable)

**Technical Notes**
- Use Expo Push Notifications (simplest with Expo) or Firebase Cloud Messaging
- Store push tokens per device per user
- Server-side notification scheduling (not local notifications) for reliability

---

### 4.6 Studio Info

**Description**: Everything a prospective or existing client needs to know about ALIGN. — location, contact, class descriptions, instructor bio, pricing, and FAQ. This is the "shop window" of the app.

**Screens**

**About ALIGN.**
- Studio story (Katie's journey, the vision)
- The ALIGN. philosophy ("Not just a studio — a community")
- Photo gallery (studio interior, Wye Valley, classes in action)

**Location**
- Embedded map (Apple Maps / Google Maps) with studio pin
- Address: [High Street address, Monmouth, NP25 ___]
- Directions / "Open in Maps" button
- Nearby landmark: "Next to Coffi Lab"
- Parking information

**Class Descriptions**
One card per class type, each containing:
- Class name and icon
- Duration
- Difficulty level (Beginner / All Levels / Intermediate / Advanced)
- Equipment used
- What to expect (2-3 sentences)
- What to bring (e.g., "Grip socks required for reformer classes. We sell them in studio if you forget!")
- Who it's for

| Class | Duration | Level | Description |
|-------|----------|-------|-------------|
| Reformer Dynamic | 50 min | Intermediate | Full-body reformer workout focusing on strength, control, and flow. Expect to sweat. |
| Reformer Core/Beginners | 50 min | Beginner | Gentle introduction to the reformer. Perfect if you've never tried Pilates before. |
| Mat Pilates | 50 min | All Levels | Classical mat Pilates. Build core strength, flexibility, and body awareness. |
| Strength & Conditioning | 45 min | All Levels | Bodyweight and resistance training. Complements your Pilates practice. |
| Reformer + Breathwork | 75 min | All Levels | Movement and guided breathwork combined. Leave feeling completely reset. |
| Candlelight Pilates | 50 min | All Levels | Evening reformer session in low light. Calm, restorative, beautiful. |
| Outdoor Pilates | 60 min | All Levels | Mat Pilates in the Wye Valley. Seasonal, weather permitting. |

**Instructor Bio**
- Katie's photo, qualifications (YMCA Level 3 Mat, Level 3 Reformer), background, personal philosophy
- Space for additional instructors (Phase 2)

**Pricing Page**
- Display all pricing options in a clean table/card layout
- "Best Value" badge on recommended option (Monthly Unlimited or 10-pack)
- Founding member pricing highlighted if active
- "Buy" buttons link directly to Stripe checkout

**FAQ**
Preloaded with common questions:
- "What should I wear?" — Comfortable clothing, grip socks for reformer (available for purchase in studio)
- "I've never done Pilates before — is that OK?" — Absolutely. Our Beginners classes are designed for you.
- "Can men come?" — Of course. ALIGN. is for everyone.
- "What's a reformer?" — Brief explanation with photo
- "What if I need to cancel?" — Cancellation policy summary
- "Is there parking?" — Details
- "I have a medical condition — can I still attend?" — We ask all clients to complete a health questionnaire. If you have concerns, speak with Katie before booking.

**Contact**
- Email, phone number
- Instagram link
- "Message us" button (links to messaging feature in Phase 2; links to Instagram DM for MVP)

---

### 4.7 Admin Panel (Katie's View) — MVP

**Description**: Katie's command centre. She needs to manage her business from her phone between classes. Speed and clarity are paramount — she has 5 minutes between sessions.

**4.7.1 Dashboard (Home)**

Displays at a glance:
- Today's classes with booking counts (e.g., "07:00 Reformer Dynamic — 3/4 booked")
- New signups since last check (with medical form flag if PAR-Q has "Yes" answers)
- Today's revenue
- Upcoming cancellations / waitlist activity

**4.7.2 Class Management**

| Action | Detail |
|--------|--------|
| Create class | Select type, date, time, duration, capacity (auto-set by type), description |
| Edit class | Change time, description, capacity |
| Cancel class | Confirm prompt → auto-notify all booked clients → auto-refund/credit |
| Recurring class | Create a weekly template (e.g., "Every Monday 07:00, Reformer Dynamic") |
| View roster | See who is booked in each spot (with reformer position for reformer classes) |

**4.7.3 Client Management**

- Searchable client list (by name or email)
- Client detail view: profile, medical form, booking history, payment history, admin notes
- Medical form review: see all PAR-Q responses. Flag indicator for "Yes" answers.
- Admin notes per client (visible only to admin): e.g., "Left knee injury — avoid deep squats"
- Manual client creation (for phone bookings or walk-ins processed by Katie)

**4.7.4 Manual Booking**

- Select a client from the list (or create new)
- Select a class from the schedule
- Confirm booking (payment can be marked as "in-studio cash/card" or processed via Stripe)

**4.7.5 Payments Overview**

- Transaction list with filters (date range, type)
- Daily/weekly/monthly revenue totals
- Refund button per transaction

**4.7.6 Push Notification Composer**

- Send a broadcast notification to all clients
- Send to specific class attendees (e.g., "Everyone booked into tomorrow's 07:00")
- Title + body text fields
- Schedule for later or send immediately

---

## 5. Feature Specification — Phase 2 (Month 2-6 Post-Launch)

> These features are important but NOT required for launch. Instagram DM and Instagram content fill the gaps for messaging and content respectively.

### 5.1 In-App Messaging

- **Studio → Client**: Broadcast messages (all clients or class-specific)
- **Client → Studio**: Direct message to ALIGN. (not client-to-client)
- **Pre-class notes**: Katie sends to class attendees — "Bring a towel today, we're doing something special"
- **Inbox UI**: Simple chat-style interface, timestamped messages
- **Push notification** for new messages

### 5.2 Content Feed

- Blog posts / articles (Katie writes in admin, published in-app)
- Free content cards: mindfulness audio descriptions, home workout guides
- Community event listings (Walk & Talk dates, Coffee mornings with Coffi Lab)
- Instagram-style visual posts from the studio
- Content is viewable without booking — it is a discovery and engagement tool

### 5.3 Client Progress Tracking (Katie's #1 Priority)

- **Attendance dashboard**: Total classes, classes this month, streak counter, attendance graph
- **Personal journal**: Client can add notes after each class ("Felt strong today", "Left shoulder tight")
- **Instructor notes**: Katie adds private notes per client per session (visible to admin only)
- **Self-assessment checkpoints**: Quarterly prompts — rate your flexibility, strength, balance, energy (1-10 scale). Visualised as a radar chart over time.
- **Progress photos**: Client-managed, stored locally or in secure cloud. Optional.
- **Monthly summary**: Auto-generated — "This month you attended 8 classes, up from 6 last month. Your flexibility self-score improved from 5 to 7."

### 5.4 Enhanced Community Features

- **Event RSVP**: Walk & Talk, Coffee mornings, workshops — book through the app
- **Referral programme**: Unique referral code per client. "Invite a friend — you both get a free class." Tracked in admin.
- **Member spotlight**: Katie features a client story in the content feed (with permission)

### 5.5 Admin Dashboard — Enhanced Analytics

- Revenue overview (daily, weekly, monthly, YTD) with graphs
- Class fill rate by time slot and type
- Client retention: weekly/monthly cohort analysis
- Most popular class times (heatmap)
- Waitlist demand per class (indicates where to add capacity)
- New client acquisition rate
- Instructor schedule management (when 2nd instructor joins)

---

## 6. Feature Specification — Phase 3 (Month 6-12)

### 6.1 Merchandise Shop

- Product catalogue with photos, descriptions, prices
- Categories: Grip Socks, Accessories, Branded Apparel, Wellness Products
- Shopping cart with quantity selection
- Stripe checkout (same payment methods as class booking)
- Fulfilment: "Collect in studio" (primary) / Shipping (future)
- Order history in client profile
- Admin: product management (add/edit/remove products, stock levels)

### 6.2 Wearable Integration

- **Apple Watch companion**: View upcoming class, receive reminders on wrist, tap to check in at studio
- **Oura Ring**: Display recovery score and sleep data on home screen — *"Your recovery is high today — perfect for Reformer Dynamic!"*
- **Apple Health / Google Fit**: Log ALIGN. classes as workouts automatically
- **Post-class summary**: Combine class data with health data — duration, estimated calories, heart rate (if available), recovery recommendation

### 6.3 On-Demand Content Library

- Video player with categories (class type, level, duration)
- Audio-only sessions (breathwork, mindfulness, guided relaxation)
- Favourites / saved list
- Continue watching / recently played
- Download for offline viewing (premium feature)
- Tied to digital membership tier (separate Stripe product)

---

## 7. User Journeys

### Journey 1: New Client Discovery to First Booking

```
1. Client walks past ALIGN. studio, sees QR code on the window
2. Scans QR code → App Store / Google Play listing
3. Downloads "ALIGN. Pilates" app
4. Opens app → Welcome screen → "Create Account"
5. Enters email, password, first name, last name → Next
6. PAR-Q medical form (7 questions + additional fields) → Next
7. Reads and accepts liability waiver → "I Agree"
8. Adds emergency contact, optional photo → "Complete Profile"
9. Welcome screen: "Welcome to ALIGN. Book your first class."
10. Taps "Book a Class" → Schedule view
11. Browses classes → Taps "Reformer Core/Beginners, Wednesday 10:00"
12. Class detail screen → Taps "Book This Class"
13. Sees reformer spot selection → Chooses Reformer #2
14. Prompted to add payment method (Stripe Payment Sheet)
15. Enters card details → Sees "Intro Offer: 3 Classes for £45"
16. Selects Intro Offer → Confirms payment
17. Booking confirmed! Push notification received.
18. Reminder notification 24 hours before class.
19. Arrives at studio → Katie has already reviewed their medical form.
```

**Time from QR scan to confirmed booking: under 5 minutes.**

### Journey 2: Regular Client Weekly Booking

```
1. Opens app (Sunday evening)
2. Home screen shows "No upcoming classes — book your next session"
3. Taps Schedule tab → Sees next week
4. Taps Monday 07:00 Reformer Dynamic
5. Reformer spot selection → Chooses usual spot (#3)
6. "Book This Class" → Deducted from 10-class pack (7 remaining)
7. "Book this class every week?" → Taps "Yes, for 4 weeks"
8. 4 bookings confirmed. Notifications set.
```

**Time: under 30 seconds.**

### Journey 3: Walk-In Client (iPad Flow)

```
1. Person enters studio, interested in trying a class
2. Katie directs them to the iPad on the reception counter
3. iPad shows ALIGN. app in kiosk/walk-in mode
4. "New here? Let's get you set up." → Quick signup form
5. Email, name, phone number → PAR-Q form → Waiver
6. Katie reviews the medical form on her phone while chatting
7. Katie manually books them into the next available class
8. Client pays via card reader in studio (Stripe Terminal) or in-app
9. After class, client receives email: "Download the ALIGN. app to book your next class"
```

### Journey 4: Katie's Morning Routine

```
1. Opens app at 06:30, switches to Admin view
2. Dashboard: "Today: 3 classes. 07:00 Reformer Dynamic — 4/4 (FULL). 10:00 Mat Pilates — 4/6. 18:00 Candlelight — 3/4."
3. Sees alert: "1 new signup — Helen Davies. PAR-Q flag: joint problem."
4. Taps Helen's profile → Reviews medical form → Adds admin note: "Discuss knee issue before class. Modify exercises as needed."
5. Taps 07:00 class → Views roster and reformer positions
6. Sends class notification: "Good morning! Today we're focusing on lower body. See you at 7!"
7. Closes app. Ready to teach.
```

**Time: under 2 minutes.**

### Journey 5: Client Cancellation & Waitlist

```
1. Sarah realises she can't make Monday 07:00 (13 hours before class)
2. Opens app → Bookings tab → Taps Monday 07:00
3. Taps "Cancel Booking" → Confirms → "Your credit has been restored."
4. Server detects open spot → Checks waitlist
5. Tom is #1 on waitlist → Receives push: "A spot opened in Reformer Dynamic at 07:00! Confirm within 30 minutes."
6. Tom taps notification → Opens class detail → "Confirm Booking"
7. Tom is booked. Katie sees updated roster.
```

---

## 8. Design Guidelines

### 8.1 Colour Palette

| Role | Colour | Hex | Usage |
|------|--------|-----|-------|
| Primary / Accent | Sage | `#8B9F82` | Buttons, active states, icons, links |
| Background | Cream | `#F5F0EB` | App background, screen base |
| Surface | White | `#FFFFFF` | Cards, modals, input fields |
| Text Primary | Charcoal | `#2C2C2C` | Headings, body text |
| Text Secondary | Stone | `#A69F95` | Captions, timestamps, secondary info |
| Light Beige | Sand | `#E8E0D8` | Dividers, subtle backgrounds, inactive tabs |
| Success | Soft Green | `#6B8F71` | Booking confirmed, payment success |
| Warning | Warm Amber | `#D4A574` | Low spots remaining, expiring packs |
| Error | Muted Rose | `#C47A7A` | Payment failed, validation errors |

### 8.2 Typography

| Element | Font | Weight | Size |
|---------|------|--------|------|
| App title / Logo | Serif (e.g., Playfair Display or similar) | Regular | 28-32px |
| Screen headings | Serif | SemiBold | 22-24px |
| Section headings | Sans-serif (e.g., Inter or SF Pro) | SemiBold | 18px |
| Body text | Sans-serif | Regular | 16px |
| Captions / metadata | Sans-serif | Regular | 13-14px |
| Buttons | Sans-serif | SemiBold | 16px |

The serif/sans-serif pairing reflects the ALIGN. brand: the serif brings elegance and distinction (brand DNA), the sans-serif ensures readability and modern clarity (functional).

### 8.3 Component Styling

- **Cards**: White background, 12px border radius, subtle shadow (`0 2px 8px rgba(0,0,0,0.06)`)
- **Buttons (Primary)**: Sage background, white text, 8px border radius, full-width on forms
- **Buttons (Secondary)**: White background, Sage border and text
- **Input fields**: White background, 1px Sand border, 8px radius. Sage border on focus.
- **Tab bar**: White background, Sage active icon, Stone inactive icon
- **Status bar**: Match Cream background (light content style)

### 8.4 Imagery & Iconography

- Photography: Natural light, warm tones, inclusive (mixed ages, genders, body types). Avoid stock fitness cliches.
- Icons: Line-style, 1.5px stroke, rounded caps. Sage colour when active, Stone when inactive.
- Empty states: Illustrated (not photographic) — e.g., a gentle reformer illustration with "No upcoming classes. Time to book one?"

### 8.5 Spacing & Layout

- Base unit: 8px grid
- Screen padding: 16-24px horizontal
- Card padding: 16px internal
- Generous whitespace between sections — the app should breathe
- Minimum touch target: 44x44px (Apple HIG / WCAG)

### 8.6 Accessibility

- WCAG AA contrast minimum for all text (4.5:1 body, 3:1 large text)
- All images have alt text
- Screen reader support (proper semantic labels on all interactive elements)
- Font scaling support (respect system font size settings)
- Minimum 44px touch targets throughout
- Colour is never the sole indicator of status (always paired with text or icon)

### 8.7 Animations

- Screen transitions: 250ms ease-out slide or fade
- Button press: subtle scale (0.97) with 100ms spring
- Card expand: smooth height animation
- Booking confirmed: gentle checkmark animation (Lottie)
- No aggressive or flashy animations. Everything calm and intentional.

---

## 9. Technical Architecture

### 9.1 System Overview

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  iOS App     │     │  Android App │     │  Admin Panel  │
│  (Expo/RN)   │     │  (Expo/RN)   │     │  (Same app,   │
│              │     │              │     │   admin role)  │
└──────┬───────┘     └──────┬───────┘     └──────┬────────┘
       │                    │                     │
       └────────────────────┼─────────────────────┘
                            │
                    ┌───────▼────────┐
                    │   API Server   │
                    │  (Node.js /    │
                    │   Express)     │
                    └───────┬────────┘
                            │
            ┌───────────────┼───────────────┐
            │               │               │
     ┌──────▼──────┐ ┌─────▼──────┐ ┌─────▼──────┐
     │  Database   │ │   Stripe   │ │   Push     │
     │ (Firestore  │ │   API      │ │  Service   │
     │  or Postgres)│ │            │ │ (Expo/FCM) │
     └─────────────┘ └────────────┘ └────────────┘
```

### 9.2 Technology Stack

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| Frontend | React Native (Expo SDK 52+) | Cross-platform, Eduardo's expertise |
| Navigation | React Navigation (bottom tabs + stack) | Industry standard for RN |
| State | Zustand or React Context | Lightweight, sufficient for app scope |
| Backend | Node.js + Express (or Firebase Functions) | Fast to build, Eduardo's discretion |
| Database | Firestore (recommended) or PostgreSQL | Firestore: zero config, real-time sync, scales automatically. Postgres: if Eduardo prefers relational. |
| Auth | Firebase Auth | Email/password + Apple Sign-In + Google. Battle-tested. |
| Payments | Stripe API (server-side) | Payment Sheet, Subscriptions, Webhooks |
| Push | Expo Push Notifications | Simplest integration with Expo apps |
| File Storage | Firebase Storage or Cloudinary | Profile photos, content images |
| Analytics | Mixpanel or Firebase Analytics | Event tracking, funnels, retention |
| Hosting | Firebase Hosting / Vercel / Railway | For API server. Eduardo's choice. |

### 9.3 Key Technical Decisions

**Stripe — Physical Goods Exemption**: ALIGN. sells in-person class attendance at a physical studio. This qualifies as a real-world service. Apple and Google explicitly exempt physical goods and real-world services from their in-app purchase requirement. Stripe can be used directly with standard 2.9% + 20p fees. No Apple/Google 30% commission.

**Franchise-Ready Architecture**: Even for MVP, structure the database with a `studio_id` field on all entities (classes, bookings, users). For now there is only one studio, but this prevents a painful migration later when ALIGN. expands.

**iPad Walk-In Mode**: Simplest approach — the same app running on an iPad in the studio, logged into a dedicated "walk-in" admin account. Katie taps "New Walk-In Client" and follows a streamlined signup flow. No separate web app needed for MVP.

---

## 10. Data Model

### 10.1 Entity Relationship Diagram (Simplified)

```
User ──< Booking >── Class
 │                      │
 │                      │
 ├── MedicalForm        ├── Instructor
 ├── Membership         │
 ├── ClassPack          └── Studio
 ├── PaymentMethod
 └── Payment
```

### 10.2 Core Entities

**User**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| studio_id | UUID | FK → Studio (franchise-ready) |
| email | String | Unique, required |
| password_hash | String | Firebase Auth managed |
| first_name | String | Required |
| last_name | String | Required |
| phone | String | Optional |
| date_of_birth | Date | Optional |
| photo_url | String | Optional |
| fitness_level | Enum | beginner / intermediate / advanced |
| goals | String | Free text |
| emergency_contact_name | String | Required |
| emergency_contact_phone | String | Required |
| emergency_contact_relation | String | Required |
| role | Enum | client / admin / instructor |
| stripe_customer_id | String | Stripe Customer object ID |
| push_token | String | Expo push token |
| notification_prefs | JSON | Per-type toggle settings |
| created_at | Timestamp | |
| updated_at | Timestamp | |

**MedicalForm**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| user_id | UUID | FK → User |
| parq_heart_condition | Boolean | Question 1 |
| parq_chest_pain_activity | Boolean | Question 2 |
| parq_chest_pain_rest | Boolean | Question 3 |
| parq_dizziness | Boolean | Question 4 |
| parq_bone_joint | Boolean | Question 5 |
| parq_medication | Boolean | Question 6 |
| parq_other_reason | Boolean | Question 7 |
| has_flags | Boolean | Computed: true if any answer is Yes |
| injuries_conditions | String | Free text |
| medications | String | Free text |
| pregnancy_status | Enum | no / yes / prefer_not_to_say |
| gp_name | String | Optional |
| gp_surgery | String | Optional |
| admin_reviewed | Boolean | Default false |
| admin_notes | String | Katie's notes |
| completed_at | Timestamp | |
| updated_at | Timestamp | |

**Class**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| studio_id | UUID | FK → Studio |
| instructor_id | UUID | FK → User (instructor role) |
| class_type | Enum | reformer_dynamic / reformer_beginners / mat / strength / reformer_breathwork / candlelight / outdoor |
| title | String | Display name |
| description | String | Full description |
| date | Date | |
| start_time | Time | |
| duration_minutes | Int | |
| capacity | Int | 4 (reformer) / 6 (mat) / 8-10 (outdoor) |
| has_spot_selection | Boolean | true for reformer classes |
| is_cancelled | Boolean | Default false |
| recurring_id | UUID | Links recurring class instances |
| created_at | Timestamp | |

**Booking**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| user_id | UUID | FK → User |
| class_id | UUID | FK → Class |
| spot_number | Int | Nullable (only for reformer classes) |
| status | Enum | confirmed / cancelled / waitlisted / no_show |
| payment_type | Enum | single / class_pack / membership / in_studio / comp |
| payment_id | UUID | FK → Payment (nullable for membership/pack) |
| class_pack_id | UUID | FK → ClassPack (nullable) |
| cancelled_at | Timestamp | Nullable |
| waitlist_position | Int | Nullable, only when status = waitlisted |
| waitlist_expires_at | Timestamp | 30 min after notification sent |
| created_at | Timestamp | |

**Payment**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| user_id | UUID | FK → User |
| stripe_payment_intent_id | String | Stripe reference |
| amount_pence | Int | Amount in pence (e.g., 2000 = £20.00) |
| currency | String | "gbp" |
| product_type | Enum | single_class / class_pack / membership / intro_offer / private_session |
| description | String | Human-readable |
| status | Enum | succeeded / failed / refunded / partially_refunded |
| refunded_amount_pence | Int | Default 0 |
| created_at | Timestamp | |

**Membership**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| user_id | UUID | FK → User |
| stripe_subscription_id | String | Stripe Subscription reference |
| plan | Enum | monthly_8 / monthly_unlimited |
| status | Enum | active / cancelled / past_due / paused |
| current_period_start | Timestamp | |
| current_period_end | Timestamp | |
| classes_used_this_period | Int | For monthly_8 plan |
| created_at | Timestamp | |

**ClassPack**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| user_id | UUID | FK → User |
| payment_id | UUID | FK → Payment |
| pack_type | Enum | intro_3 / pack_5 / pack_10 |
| total_credits | Int | 3, 5, or 10 |
| remaining_credits | Int | |
| expires_at | Timestamp | |
| created_at | Timestamp | |

**Studio**
| Field | Type | Notes |
|-------|------|-------|
| id | UUID | Primary key |
| name | String | "ALIGN. Monmouth" |
| address | String | |
| lat | Float | For map |
| lng | Float | For map |
| phone | String | |
| email | String | |
| instagram_url | String | |
| cancellation_hours_full | Int | Default 12 |
| cancellation_hours_partial | Int | Default 2 |
| created_at | Timestamp | |

---

## 11. Non-Functional Requirements

| Requirement | Target | Notes |
|-------------|--------|-------|
| App cold start | < 2 seconds | On 4G connection, mid-range device |
| Booking confirmation | < 1 second | Server response time |
| Uptime | 99.5% | Monthly SLA target |
| GDPR compliance | Full | Right to deletion, data export, consent tracking, encrypted medical data |
| PCI DSS | Via Stripe | ALIGN. never handles raw card data |
| Medical data encryption | At rest and in transit | PAR-Q data stored encrypted. TLS for all API calls. |
| Offline support | Basic | Cached schedule viewable offline. Bookings require connectivity. |
| iOS support | iOS 15+ | Covers ~95% of active iPhones |
| Android support | Android 10+ | Covers ~90% of active Android devices |
| Scalability | Multi-studio ready | studio_id on all entities from day one |
| Data backup | Daily | Automated database backups |
| App size | < 50MB | Reasonable initial download size |

---

## 12. MVP Scope — What Eduardo Builds in 2 Weeks

### Included in MVP (Launch-Critical)

| Feature | Priority | Notes |
|---------|----------|-------|
| Auth (email + password) | P0 | Apple Sign-In highly recommended for iOS |
| Onboarding wizard (PAR-Q + waiver + profile) | P0 | Non-negotiable — medical/legal requirement |
| Class schedule (week view + class detail) | P0 | Core functionality |
| Reformer spot selection | P0 | Key differentiator |
| Booking + cancellation + waitlist | P0 | Core functionality |
| Stripe payments (single class + packs + memberships) | P0 | Revenue enablement |
| Client profile (details + medical form + booking history) | P0 | |
| Push notifications (booking confirm + reminders) | P0 | Critical for attendance |
| Studio info (location, classes, FAQ, instructor) | P0 | "Shop window" |
| Admin: class management (CRUD + recurring) | P0 | Katie must be able to manage classes |
| Admin: booking view + roster | P0 | Katie must see who's coming |
| Admin: client list + medical form review | P0 | Legal/safety requirement |
| Admin: manual booking (walk-in/phone) | P0 | |
| Admin: push notification composer (basic) | P1 | Broadcast to all or class-specific |

### Deferred to Phase 2 (Month 2-6)

| Feature | Fallback |
|---------|----------|
| In-app messaging | Use Instagram DM. "Message us on Instagram" link in app. |
| Content feed / blog | Use Instagram for content. Link to Instagram from the app. |
| Progress tracking | Manual — Katie tracks in a notebook or spreadsheet initially |
| Enhanced analytics | Stripe Dashboard provides basic revenue data |
| Referral programme | Word of mouth + manual tracking |
| Event RSVP | Instagram posts for event promotion |

### Deferred to Phase 3 (Month 6-12)

| Feature | Fallback |
|---------|----------|
| Merchandise shop | Sell in studio, promote on Instagram |
| Wearable integration | Not needed for launch |
| On-demand video content | Not needed until Katie starts filming |
| Dark mode | Future enhancement |

### Eduardo's 2-Week Build Breakdown (Suggested)

| Days | Focus |
|------|-------|
| Day 1-2 | Project setup, navigation, auth flow, Firebase/backend setup |
| Day 3-4 | Onboarding wizard (PAR-Q, waiver, profile creation) |
| Day 5-6 | Class schedule, class detail, reformer spot selection |
| Day 7-8 | Booking flow, cancellation, waitlist logic |
| Day 9-10 | Stripe integration (payments, subscriptions, packs) |
| Day 11 | Push notifications, client profile |
| Day 12 | Admin panel (class management, client list, roster) |
| Day 13 | Studio info screens, polish, edge cases |
| Day 14 | Testing, bug fixes, App Store submission prep |

---

## 13. Analytics & Success Metrics

### Key Performance Indicators

| Metric | Target (Month 1) | Target (Month 6) | How Measured |
|--------|-------------------|-------------------|-------------|
| App downloads | 100 | 500 | App Store Connect / Google Play Console |
| Registered users | 80 | 400 | Database count |
| Medical form completion rate | 95%+ | 95%+ | Registrations with completed PAR-Q / total registrations |
| Booking conversion rate | 60% | 70% | Users who book / registered users |
| Class fill rate | 50% | 80% | Booked spots / total spots across all classes |
| Weekly active users | 30 | 150 | Users who open the app in a given week |
| Retention (week 4) | 50% | 65% | Users who book in week 4 / users who booked in week 1 |
| Revenue per user per month | £40 | £60 | Total revenue / active users |
| Push notification opt-in rate | 80% | 80% | Users with push enabled / total users |
| Average time to book | < 60 seconds | < 30 seconds | Analytics event tracking |

### Events to Track

| Event | Properties |
|-------|-----------|
| `app_opened` | source (push notification, organic, deep link) |
| `signup_started` | |
| `signup_completed` | method (email, apple, google) |
| `parq_completed` | has_flags (boolean) |
| `schedule_viewed` | date, filter_applied |
| `class_detail_viewed` | class_type, class_id |
| `spot_selected` | spot_number, class_type |
| `booking_completed` | class_type, payment_type, time_to_book_seconds |
| `booking_cancelled` | class_type, hours_before_class |
| `waitlist_joined` | class_type |
| `waitlist_converted` | class_type, wait_time_minutes |
| `payment_completed` | product_type, amount |
| `payment_failed` | product_type, error_type |
| `push_notification_received` | notification_type |
| `push_notification_tapped` | notification_type |
| `studio_info_viewed` | section (about, location, classes, faq) |
| `profile_updated` | fields_changed |

---

## 14. App Store Preparation

### 14.1 Submission Details

| Field | Value |
|-------|-------|
| App Name | ALIGN. Pilates |
| Subtitle | Book Classes. Build Community. |
| Category | Primary: Health & Fitness. Secondary: Lifestyle. |
| Age Rating | 4+ |
| Price | Free (revenue via in-app Stripe payments) |
| Availability | United Kingdom (initially). Expand later. |

### 14.2 App Store Description

> ALIGN. Pilates — your studio in your pocket.
>
> Book reformer and mat Pilates classes at ALIGN. Studio in Monmouth. Choose your reformer spot, manage your membership, and stay connected with the ALIGN. community.
>
> FEATURES:
> - Browse the class schedule and book in seconds
> - Choose your preferred reformer position
> - Manage your membership or class packs
> - Receive reminders so you never miss a session
> - Learn about each class type and what to expect
> - Complete your health questionnaire securely in-app
>
> ALIGN. is more than a studio. It's a community committed to your wellbeing — knowledgeable guidance from beyond the studio walls.
>
> Available at ALIGN. Studio, Monmouth, South Wales.

### 14.3 Keywords

`pilates, reformer, booking, monmouth, wales, fitness, wellness, studio, mat pilates, class booking, pilates studio`

### 14.4 Screenshots Required

| Screen | Content |
|--------|---------|
| 1 | Home screen with welcome and upcoming class |
| 2 | Schedule view with class cards |
| 3 | Reformer spot selection |
| 4 | Booking confirmation |
| 5 | Profile with membership status |
| 6 (optional) | Studio info / class descriptions |

**Sizes needed**: iPhone 6.7" (required), iPhone 6.1", iPad (optional). Android: phone (required).

### 14.5 Pre-Submission Checklist

| Task | Owner | Timeline |
|------|-------|----------|
| Apple Developer Account (£79/year) | Katie / Eduardo | ASAP — can take 2-5 days to approve |
| Google Play Developer Account ($25 one-time) | Katie / Eduardo | ASAP — usually approved within 48 hours |
| Privacy Policy URL (hosted on web) | Eduardo | Before submission |
| Terms of Service URL | Katie / Eduardo | Before submission |
| App icons (1024x1024 PNG) | Brand designer / Eduardo | Before submission |
| Screenshots (real device or simulator) | Eduardo | After build complete |
| Submit to Apple | Eduardo | 3-4 weeks before launch (review takes 2-5 days, allow buffer for rejections) |
| Submit to Google | Eduardo | 2-3 weeks before launch (review typically faster) |

### 14.6 Apple Review — Key Compliance Points

- **Stripe payments**: Permissible because ALIGN. sells physical services (in-person classes). Include a note in the review submission explaining the brick-and-mortar exemption.
- **Health data (PAR-Q)**: Declare health data collection in App Privacy. Encrypt at rest.
- **Push notifications**: Must have user consent. Do not send marketing without opt-in.
- **Account deletion**: Must offer account deletion (GDPR + Apple requirement). Include in Settings.
- **Sign in with Apple**: Required if any third-party social login is offered.

---

## 15. Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| Apple rejects app due to Stripe payments | Low | High | Include clear explanation of physical service exemption in review notes. Screenshot of studio address. |
| 2-week build timeline slips | Medium | High | Strict MVP scope. Defer messaging and content feed without hesitation. |
| Low app adoption at launch | Medium | Medium | QR codes everywhere. Social media push. Offer founding member pricing as incentive. |
| Stripe webhook reliability | Low | Medium | Implement retry logic. Manual payment reconciliation as fallback. |
| Medical data breach | Very Low | Very High | Encrypt PAR-Q data at rest. Use Firebase security rules. Regular security review. |
| Walk-in iPad flow too complex | Medium | Low | Keep it simple: same app, admin mode. Katie assists in person. |

---

## Appendix A: Cancellation Policy Recommendation

Based on industry norms for small-capacity Pilates studios (4-6 spots per class):

| Window | Policy | Rationale |
|--------|--------|-----------|
| 12+ hours before | Full refund / credit restored | Standard grace period |
| 2-12 hours before | No refund, but credit held (late cancel credit — usable for future class) | Encourages advance cancellation while not penalising too harshly |
| Under 2 hours / no-show | No refund, credit forfeited | Protects revenue — with only 4 spots, a no-show is 25% of capacity lost |

**Implementation note**: Store the cancellation policy hours in the Studio entity so Katie can adjust them without a code change.

---

## Appendix B: Founding Member Programme

Recommended launch strategy to drive early adoption:

| Offer | Detail |
|-------|--------|
| Name | "Founding Member" |
| Price | £79/month unlimited (vs standard £99) |
| Limit | First 20 members |
| Lock-in | Price guaranteed for 12 months |
| Benefit | Priority booking (12 hours before general release) |
| Marketing | "Be one of our first 20 Founding Members — limited spots available" |

Implement as a separate Stripe product with quantity cap. When 20 subscriptions are sold, mark as unavailable.

---

## Appendix C: QR Code Strategy

| Location | QR Code Links To |
|----------|-----------------|
| Studio front window | App Store / Google Play (smart link that detects OS) |
| Inside studio (wall poster) | Direct to booking screen (deep link) |
| Coffi Lab partnership card | App download + intro offer landing page |
| Instagram bio | App download link |
| Business cards / flyers | App download link |
| Event materials (Walk & Talk) | App download + event RSVP |

**Technical**: Use a smart link service (e.g., Firebase Dynamic Links or onelink.to) that routes iOS users to the App Store and Android users to Google Play from a single QR code.

---

*This document is the specification for Eduardo's build. Katie's vision is the north star. Every screen, every flow, every detail exists to serve one purpose: making ALIGN. feel like more than a studio — it's a community, a brand, and a commitment to your wellbeing.*

---

**Document version**: 1.0
**Last updated**: 26 March 2026
**Next review**: After Eduardo's mockup delivery (estimated 29-31 March 2026)
