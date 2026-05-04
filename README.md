# Alīgn Studio — Vision

Strategic design vision, brand thinking, and interactive mockups for **Alīgn Studio** — a UK Pilates studio led by Katie. Produced by [CapitalTrend Group](https://capitaltrend.group).

## Live Mockup

**[Alīgn Studio · App Mockup →](https://capitaltrendgroup.github.io/align-studio-vision/app-mockup/)**

A full-fidelity interactive PWA mockup of the member-facing app. Built as a single-file HTML for ease of review on any device.

> Best viewed on iPhone Safari → Share → **Add to Home Screen** for the fullscreen experience.

### What's inside the mockup

The current build is the **rebrand v1**, brought onto Katie's finalized brandbook:

- **Wordmark** — Alīgn Studio with macron over the *i*
- **Palette** — Deep Brown `#5A3029` + Sage `#A4B49B` + Cream `#F5F1E8`
- **Typography** — Proza Libre (display) + Inter (body)
- **Line + Points motif** — a single visual language carried functionally across reformer spot picker, tab bar, schedule capacity, onboarding progress, streak/progress in Profile, and the new Your Line screen
- **Editorial photography** — 7 commissioned-style images via Nano Banana, in the spirit of Bottega Veneta / The Row campaigns: cream + sage + brown, no AI clichés, no overt happiness
- **Three GSAP signature moments**
  1. Splash — 12 dots scatter, converge, collapse to form the macron
  2. Tab transitions — dot expands to dash with subtle overshoot
  3. Booking confirmation — chosen dot flies along the line and settles
- **New "Your Line" screen** — accessible from the Home week-strip and the Profile streak line. Hero number, line of attended-class dots, patterns, and the next point.
- **Cinema Sussurrado motion** — quiet, restrained animation. `prefers-reduced-motion` and GSAP-CDN-failure fallbacks throughout.

### Screens

Splash · Onboarding (4 steps + PAR-Q) · Home · Schedule · Class Detail · Booking Confirmation · My Bookings · Content · Profile · Admin Dashboard · **Your Line**

## Repository Structure

| Path | What |
|---|---|
| `app-mockup/index.html` | The single-file PWA mockup (rebrand v1) |
| `app-mockup/img/` | 7 editorial WebPs (~770KB total) |
| `app-mockup/intro/` | Earlier intro screen iteration |
| `docs/` | Strategy, planning, and vision documents |
| `index.html` | Landing page |

## Status

**Rebrand v1 — ready for Katie's review.** Smoke-tested on Chrome desktop. iOS Safari hands-on test pending. Open follow-ups: lock final sage hex (3 candidates available via `?sage=a|b|c` query param), date-proportional dot positioning on Your Line, real audio playback, backend integration.

---

© CapitalTrend Group · Designed for Katie / Alīgn Studio
