# WD Red NAS — Landing Page: Flow & Code Documentation

**File:** `wd-red-nas-landing-page.html`
**Location:** `WD Red NAS/New folder/`
**Version:** 1.0 · August 2026
**Theme:** WD.com White — Inter font · #c8102e red · #2266ff blue · #00e5d1 teal

---

## Table of Contents

1. [Page Flow Overview](#page-flow-overview)
2. [Assets Used](#assets-used)
3. [Design Tokens](#design-tokens)
4. [Section-by-Section Breakdown](#section-by-section-breakdown)
5. [CSS Architecture](#css-architecture)
6. [JavaScript Behaviour](#javascript-behaviour)
7. [Responsive Breakpoints](#responsive-breakpoints)

---

## Page Flow Overview

```
┌─────────────────────────────────────────────────────────────┐
│  STICKY NAVIGATION (70px, glassmorphism blur)              │
│  [WD Logo] | RED NAS     What is NAS · How it Works ·     │
│  Benefits · Setup · WD Red Drives     [Get NAS Advice]     │
├─────────────────────────────────────────────────────────────┤
│  HERO  (white bg, 50/50 CSS grid)                         │
│  LEFT:                    RIGHT:                           │
│  Eyebrow (red)            ┌──────────────────────┐        │
│  H1 — "one safe home"     │  [24/7 badge]        │        │
│         (em in red)       │                      │        │
│  Lede text (17px)         │  EX4100 device image │        │
│  [Get NAS Advice] CTA     │   (floating anim)    │        │
│  [Learn NAS Basics]       │          [WD Red Pro]│        │
│  Trust badges × 3         └──────────────────────┘        │
├─────────────────────────────────────────────────────────────┤
│  FULL-WIDTH FEATURE BANNER (min-height 460px)              │
│  BG: Office/team photo · Dark gradient overlay left→right  │
│  Teal eyebrow · White H2 · White body · Outline-white CTA  │
├─────────────────────────────────────────────────────────────┤
│  WHAT IS NAS  (off-white #f7f7f5, 1.1fr/0.9fr grid)       │
│  LEFT: Eyebrow · H2 · 2× paragraphs · Definition callout  │
│  RIGHT: QNAP + WD Red drives image                        │
├─────────────────────────────────────────────────────────────┤
│  HOW IT WORKS  (white, centre-head + 4-col card grid)      │
│  [01 Connect] [02 Install] [03 Set up] [04 Backup]        │
│  Each: step# · icon (red on red-tint) · H3 · body         │
│  Hover: lift + red border                                  │
├─────────────────────────────────────────────────────────────┤
│  BENEFITS  (off-white, centre-head + 3-col card grid)      │
│  [Backup]  [Share]  [Grow]                                │
│  [Private] [Always-on] [Cost]                             │
│  + Audience chips row (pill tags, hover red)               │
│  🏠 Home  📷 Photo  🎬 Video  🏢 SMB  📹 CCTV  🖥️ IT   │
├─────────────────────────────────────────────────────────────┤
│  ECOSYSTEM / SETUP  (white, 50/50 grid)                    │
│  LEFT: QNAP+WD Red image                                  │
│  RIGHT: Eyebrow · H2 · Body                               │
│    ① Choose NAS enclosure                                 │
│    ② Insert WD Red drives                                 │
│    ③ Connect, configure & go                              │
│    [Talk to a Specialist] CTA                             │
├─────────────────────────────────────────────────────────────┤
│  WHY WD RED  (off-white, centre-head)                      │
│  4 spec cards (red 32×4px bar accent):                     │
│  [NAS 24/7] [NASware™] [RAID] [3yr Warranty]              │
│                                                            │
│  2 product cards (side-by-side):                           │
│  [WD Red Plus — white card]  [WD Red Pro — dark/ink]      │
│   12TB image, specs list      16TB image, specs list       │
├─────────────────────────────────────────────────────────────┤
│  QUOTE BAND  (WD red #c8102e, full-width)                  │
│  "Here is the simplest NAS setup for your use case..."    │
│  WD AUTHORISED CHANNEL PARTNERS — INDIA                   │
├─────────────────────────────────────────────────────────────┤
│  LEAD FORM  (ink/dark #111111)                             │
│  LEFT: Teal eyebrow · White H2 · Lede                     │
│  Routing list (teal labels, white text):                   │
│   FAMILY / HOME  → nearest IT retailer                    │
│   CREATOR / STUDIO → NAS creative partner                 │
│   OFFICE / SMB → system integrator                        │
│   CCTV / SURVEILLANCE → surveillance partner              │
│                                                            │
│  RIGHT: White form card                                   │
│  [Full Name]      [Mobile/Email]                          │
│  [City]           [Use Case ▼]                            │
│  [Storage Need ▼] [Buying Timeline ▼]                     │
│  [Request a Callback] full-width red btn                  │
│  → Success state: checkmark icon + message                │
├─────────────────────────────────────────────────────────────┤
│  FOOTER (white, border-top)                               │
│  [WD Logo] | Red NAS          WD CONFIDENTIAL © 2026      │
└─────────────────────────────────────────────────────────────┘
```

---

## Assets Used

| File (relative from HTML) | Section | Role |
|---|---|---|
| `../header-main-logo.svg` | Nav, Footer | WD wordmark SVG (multi-colour, 83×48px viewBox) |
| `../my-cloud-ex4100-Hero.png.thumb.1280.1280.png` | Hero | WD My Cloud EX4100 (4-bay NAS device) |
| `../WD-Red-Pro-feature1.jpg.wdthumb.1280.1280.png` | Feature Banner | Team/office background image |
| `../nas-product-qnap-red.png.thumb.1280.1280.png` | What is NAS, Ecosystem | QNAP NAS + WD Red Pro & Plus drives |
| `../wd-red-plus-sata-3-5-hdd-12tb.png.wdthumb.1280.1280.png` | Why WD Red | WD Red Plus 12TB drive |
| `../WD-Red-Pro-3-5-HDD-left-16TB.png.wdthumb.1280.1280.png` | Why WD Red | WD Red Pro 16TB drive |

> All paths use `../` because the HTML is one level deep in `New folder/`.

---

## Design Tokens

```css
:root {
  /* Brand colours */
  --wd-red:       #c8102e;   /* Primary: CTAs, accents, eyebrows */
  --wd-red-dark:  #a30d25;   /* Hover state for red buttons */
  --wd-red-light: #f9e5e8;   /* Icon backgrounds, tints */
  --wd-blue:      #2266ff;   /* Focus rings (matches logo) */
  --wd-teal:      #00e5d1;   /* Eyebrows on dark sections (matches logo) */

  /* Ink (text) scale */
  --ink:          #111111;   /* Headings, dark section background */
  --ink-mid:      #3d3d3d;   /* Secondary text, form labels */
  --ink-soft:     #6b7280;   /* Body copy, card text */
  --ink-muted:    #9ca3af;   /* Placeholders, legal text */

  /* Surface scale */
  --white:        #ffffff;
  --off-white:    #f7f7f5;   /* Alternating section backgrounds */
  --surface:      #f2f2ef;   /* Nav link hover background */
  --line:         #e5e5e2;   /* All borders and dividers */
  --line-mid:     #d1d1ce;   /* Stronger separators */

  /* Border radii */
  --radius-sm:    4px;       /* Buttons, inputs */
  --radius:       8px;       /* Icon containers, small cards */
  --radius-lg:    16px;      /* Main cards, form wrapper */

  /* Layout */
  --maxw:         1200px;    /* Content container max-width */
  --nav-h:        70px;      /* Sticky header height */

  /* Typography */
  --font: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
}
```

---

## Section-by-Section Breakdown

### 4.1 Navigation — `.site-header`

- **Sticky:** `position: sticky; top: 0; z-index: 100`
- **Glassmorphism:** `background: rgba(255,255,255,0.97); backdrop-filter: blur(10px)`
- **Height:** 70px (`--nav-h`)
- **Nav links hide at ≤900px**
- **Anchor targets:** `#what-is-nas` · `#how-it-works` · `#benefits` · `#ecosystem` · `#why-wd-red` · `#get-advice`

| Class | Element |
|---|---|
| `.site-header` | `<header>` wrapper |
| `.nav-inner` | Flexbox row: brand · links · CTA |
| `.nav-brand` | Logo img + separator + "RED NAS" label |
| `.nav-links` | `<ul>` of 5 anchor links |
| `.nav-cta` | "Get NAS Advice" button |

---

### 4.2 Hero — `.hero`

- **Layout:** `display: grid; grid-template-columns: 1fr 1fr` → stacks at ≤860px
- **Padding:** `80px 0 0` (no bottom — flows into next section)

| Element | Class | Detail |
|---|---|---|
| Eyebrow | `.eyebrow` | "WD Red NAS Storage" — red, 11px, uppercase |
| H1 | `.hero-copy h1` | `clamp(34px,4.5vw,54px)`, fw 800, `em` = red |
| Lede | `.lede` | 17px, `--ink-soft`, max 48ch |
| CTA row | `.hero-cta-row` | flex-wrap, gap 12px |
| Trust strip | `.hero-trust` | 3 icon+text items, 13px |
| Device image | `.hero-device-img` | `heroFloat` animation (6s, ±10px Y) |
| White badge | `.hero-badge` | "24/7" — white card, top-left, `badgePulse` |
| Red badge | `.hero-badge-2` | "WD Red® Pro" — red card, bottom-right |

**Keyframes:**
```css
@keyframes heroFloat { 0%,100%{transform:translateY(0)} 50%{transform:translateY(-10px)} }
@keyframes badgePulse { 0%,100%{transform:scale(1)} 50%{transform:scale(1.02)} }
```

---

### 4.3 Feature Banner — `.feature-banner`

- Full-width `<div>`, `min-height: 460px`, `position: relative`
- Background `<img>` at `position: absolute; inset: 0; object-fit: cover`
- Gradient overlay: `linear-gradient(90deg, rgba(10,10,10,0.80), rgba(10,10,10,0.55), transparent)`
- Content z-index 2 above overlay
- Eyebrow colour: `--wd-teal` (not red)

---

### 4.4 What is NAS — `.section-what-is-nas`

- Background: `--off-white`
- Grid: `1.1fr 0.9fr` → 1-col at ≤860px
- Contains `.nas-definition` callout card: white bg, red icon, "In plain terms:" bold intro
- Image: `nas-product-qnap-red.png`, `max-width: 400px`, `drop-shadow`

---

### 4.5 How It Works — `.section-how`

- Background: `--white`
- 4-column grid → 2-col at ≤1000px → 1-col at ≤560px
- Each `.how-card`: step number (red) · icon (red on `--wd-red-light` bg) · H3 · body
- **Hover:** `translateY(-6px)` + box-shadow + `border-color: var(--wd-red)`

| Step | Title | Icon |
|---|---|---|
| 01 | Connect to network | Monitor/screen |
| 02 | Install WD Red drives | Server stack |
| 03 | Set up users & folders | People group |
| 04 | Start backup & access | Shield check |

---

### 4.6 Benefits — `.section-benefits`

- Background: `--off-white`
- 3-column grid → 2-col at ≤900px → 1-col at ≤560px
- Each `.benefit-card`: 50×50 icon (red on red-tint) · H3 · body
- **Hover:** `translateY(-5px)` + shadow
- Audience chips (`.audience-chip`): `border-radius: 100px`, hover = red border + text

| Card | Icon |
|---|---|
| Backup without confusion | Shield |
| Share without resending | Share/nodes |
| Grow without starting over | Trending up arrow |
| Private by design | Lock/padlock |
| Always-on access | Clock |
| Reduce cloud costs | Dollar/currency |

---

### 4.7 Ecosystem / Setup — `.section-ecosystem`

- Background: `--white`
- 50/50 grid → 1-col at ≤860px
- Steps list (`.steps-list`): `<ol>`, each `.step-item` = red circle number + `.step-body` (H3 + p)
- Step dividers: `border-bottom: 1px solid var(--line)` (last has `none`)

---

### 4.8 Why WD Red — `.section-why-wd-red`

- Background: `--off-white`
- **Spec cards** (`.spec-card`): 4-col grid, red 32×4px bar accent at top
- **Product cards** (`.product-card`): 2-col, flex row (image + info)
  - Standard card: white bg, `--wd-red` tag
  - Featured card (`.featured`): `--ink` dark bg, `#ff8e9c` pink tag

| Product | Image | Specs |
|---|---|---|
| WD Red® Plus | `wd-red-plus-sata-3-5-hdd-12tb.png` | 14TB · 8-bay · 5400RPM · 180TB/yr |
| WD Red® Pro | `WD-Red-Pro-3-5-HDD-left-16TB.png` | 28TB · 24-bay · 7200RPM · 300TB/yr |

---

### 4.9 Quote Band — `.quote-band`

- Background: `var(--wd-red)` full-width
- `font-style: italic` blockquote, `clamp(18px,2.5vw,26px)`
- `<cite>` in `rgba(255,255,255,0.72)`, uppercase, spaced

---

### 4.10 Lead Form — `.section-lead`

- Background: `var(--ink)` (#111111)
- Grid: `1fr 1.1fr` → 1-col at ≤920px
- Left: teal eyebrow · white H2 · lede · routing list (`.routing-list`)
- Right: white card (`.lead-form-wrap`), 6 input fields in 3 × 2-col rows

**Form fields:**
| Row | Field 1 | Field 2 |
|---|---|---|
| 1 | Full Name (text) | Mobile/Email (text) |
| 2 | City (text) | Use Case (select) |
| 3 | Storage Need (select) | Buying Timeline (select) |

**Validation:** `[required]` → red border on empty submit
**Success state:** `#formFields` hidden → `#successMsg.show` displayed

---

### 4.11 Footer — `footer`

- `padding: 40px 0`, `border-top: 1px solid var(--line)`, white background
- Flexbox: logo+label left, legal text right, wraps on small screens

---

## CSS Architecture

Single `<style>` block in `<head>`. 18 named sections:

```
01  :root — design tokens
02  Global reset (box-sizing, margin, padding)
03  Base styles (body, img, a, h1-h4)
04  .wrap — max-width container
05  .eyebrow — uppercase label component
06  .btn variants (primary, outline, outline-white)
07  Focus styles (a11y — blue outline)
08  Navigation (.site-header through .nav-cta)
09  Hero (.hero through .hero-badge-2, @keyframes)
10  Feature banner (.feature-banner through content)
11  What is NAS (.section-what-is-nas, .nas-definition)
12  How it works (.section-how, .how-card)
13  Benefits (.section-benefits, .benefit-card, .audience-chip)
14  Ecosystem (.section-ecosystem, .steps-list, .step-item)
15  Why WD Red (.section-why-wd-red, .spec-card, .product-card)
16  Quote band (.quote-band)
17  Lead form (.section-lead through .form-success)
18  Footer (footer, .footer-inner, .footer-brand)
19  Scroll reveal (.reveal, .reveal-delay-1 to 4)
```

**CSS Animations:**
- `heroFloat` — 6s ease-in-out infinite, Y-axis ±10px
- `badgePulse` — 4s ease-in-out infinite, scale 1.02 (2s delay variant on `.hero-badge-2`)

---

## JavaScript Behaviour

Single self-invoking IIFE at bottom of `<body>`. No frameworks, no dependencies.

### Scroll Reveal (IntersectionObserver)

```js
(function () {
  'use strict';

  const revealEls = document.querySelectorAll('.reveal');

  // Primary: IntersectionObserver API
  if ('IntersectionObserver' in window) {
    const io = new IntersectionObserver(function (entries) {
      entries.forEach(function (e) {
        if (e.isIntersecting) {
          e.target.classList.add('in');  // triggers CSS transition
          io.unobserve(e.target);        // stop watching after reveal
        }
      });
    }, { threshold: 0.10 });             // fires at 10% visibility
    revealEls.forEach(function (el) { io.observe(el); });
  } else {
    // Fallback for older browsers
    revealEls.forEach(function (el) { el.classList.add('in'); });
  }

  // Safety net: force-reveal all after 1600ms
  setTimeout(function () {
    revealEls.forEach(function (el) { el.classList.add('in'); });
  }, 1600);
```

**CSS triggered by `.in`:**
```css
.reveal { opacity: 0; transform: translateY(20px);
  transition: opacity 0.65s cubic-bezier(0.22,1,0.36,1),
              transform 0.65s cubic-bezier(0.22,1,0.36,1); }
.reveal.in { opacity: 1; transform: translateY(0); }
.reveal-delay-1 { transition-delay: 0.10s; }
.reveal-delay-2 { transition-delay: 0.20s; }
.reveal-delay-3 { transition-delay: 0.30s; }
.reveal-delay-4 { transition-delay: 0.40s; }
```

### Lead Form

```js
  var form = document.getElementById('leadForm');
  form.addEventListener('submit', function (e) {
    e.preventDefault();
    var valid = true;

    // Validate all [required] fields
    form.querySelectorAll('[required]').forEach(function (input) {
      if (!input.value.trim()) {
        valid = false;
        input.style.borderColor = '#c8102e'; // red highlight
      } else {
        input.style.borderColor = '';
      }
    });

    if (!valid) return; // stop if any field empty

    // Show success state
    document.getElementById('formFields').style.display = 'none';
    document.getElementById('successMsg').classList.add('show');
  });
})();
```

---

## Responsive Breakpoints

| Max-width | What changes |
|---|---|
| `1000px` | `.how-grid` 4-col → 2-col; `.specs-row` 4-col → 2-col |
| `920px` | `.lead-grid` 2-col → 1-col |
| `900px` | `.benefits-grid` 3-col → 2-col; `.nav-links` hidden |
| `860px` | `.hero-grid`, `.what-is-nas-grid`, `.ecosystem-grid` → 1-col; hero-badges hidden |
| `768px` | `.wrap` padding 40px → 20px; feature-banner full-width; overlay darkened |
| `760px` | `.product-cards` 2-col → 1-col |
| `560px` | `.how-grid`, `.specs-row`, `.benefits-grid` → 1-col; device img max 300px |
| `500px` | `.product-card` flex → column; `.lead-form-wrap` padding reduced |
| `480px` | `.form-row` 2-col → 1-col |

---

*WD Red NAS Project — Documentation generated August 2026*
