# 🏋️ Octane Wellness Club — Website PRD
> **Product Requirements Document** for vibe coding tools (Cursor / Bolt / Lovable / v0)
> Reference UI: Bartos Gym design system (dark premium aesthetic, lime-green CTA)

---

## 1. Project Overview

| Field | Detail |
|-------|--------|
| **Client** | Octane Wellness Club |
| **Location** | SCO 73-79, Shopping Plaza, Sector 17D, Chandigarh – 160017 |
| **Phone** | +91 72680 90909 |
| **WhatsApp** | +91 72680 90909 |
| **Rating** | ⭐ 4.6 / 5 (734+ Google Reviews) |
| **Hours** | Mon–Sat: 6:00 AM – 10:30 PM · Sun: 5:00 AM – 9:00 PM |
| **Stack** | HTML5 · CSS3 · Vanilla JS (no framework) · Single HTML file |

---

## 2. Design System

### 2.1 Color Palette

```css
--color-bg:         #0A0A0A;   /* near-black page background */
--color-surface:    #111111;   /* card / section backgrounds */
--color-surface-2:  #1A1A1A;   /* elevated cards */
--color-accent:     #C8FF00;   /* lime-green — primary CTA, highlights */
--color-accent-dark:#9ECC00;   /* hover state of accent */
--color-text:       #FFFFFF;   /* primary text */
--color-text-muted: #888888;   /* secondary / caption text */
--color-border:     #2A2A2A;   /* subtle borders */
```

### 2.2 Typography

```css
/* Import in <head> */
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@300;400;500;600&display=swap');

--font-display: 'Bebas Neue', sans-serif;   /* hero headings, section titles */
--font-body:    'Inter', sans-serif;         /* body, nav, buttons, labels */

/* Scale */
--text-hero:  clamp(52px, 8vw, 100px);   /* Bebas Neue, font-weight 400 */
--text-h2:    clamp(32px, 5vw, 56px);    /* Bebas Neue, font-weight 400 */
--text-h3:    20px;                       /* Inter, font-weight 600 */
--text-body:  16px;                       /* Inter, font-weight 400, line-height 1.7 */
--text-label: 12px;                       /* Inter, font-weight 500, letter-spacing 2px, UPPERCASE */
```

### 2.3 Layout Rules

- Max content width: **1200px**, centered with `margin: 0 auto`
- Section padding: `100px 48px` desktop · `60px 20px` mobile
- Border-radius: **0px** for sections · **8px** for cards · **999px** for pill buttons
- No gradients, no drop shadows — flat, bold, minimal
- Grid: CSS Grid + Flexbox only

### 2.4 Signature Element

> **The accent bar** — a `2px solid #C8FF00` underline appears on active nav items, section eyebrows, and hover states. This single element ties the whole design together.

---

## 3. Site Architecture (Sections in Order)

```
[1]  NAVBAR
[2]  HERO
[3]  ABOUT STRIP
[4]  PHOTO GALLERY
[5]  SERVICES / FEATURES
[6]  VIDEO REEL SECTION
[7]  STATS BAR
[8]  TESTIMONIALS
[9]  LOCATION + MAP
[10] FAQ
[11] CTA BANNER
[12] FOOTER
[🔘] WHATSAPP FLOATING BUTTON (position: fixed)
```

---

## 4. Section-by-Section Specifications

---

### [1] NAVBAR

**Layout:** Fixed top · full-width · `background: rgba(10,10,10,0.95)` · `backdrop-filter: blur(12px)` · `border-bottom: 1px solid #2A2A2A`

**Left:** Logo text `OCTANE` in Bebas Neue 28px lime-green `#C8FF00` + `WELLNESS CLUB` in Inter 11px muted below

**Center links (desktop):** About · Gallery · Services · Videos · Location · FAQ

**Right CTA:**
```html
<a href="https://wa.me/917268090909" class="btn-cta">Join Now ↗</a>
```
Style: `background: #C8FF00; color: #000; border-radius: 999px; padding: 10px 24px; font-weight: 600; font-size: 14px`

**Mobile:** Hamburger menu → full-screen overlay nav with lime-green active link

---

### [2] HERO SECTION

**Layout:** Full viewport height `100vh` · background image with dark overlay

**Background image:**
```
https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=1600&q=80
```
`background-size: cover; background-position: center;`

**Overlay:** `background: linear-gradient(to right, rgba(0,0,0,0.85) 50%, rgba(0,0,0,0.3) 100%)`

**Content (left-aligned, vertically centered):**
```
[eyebrow]  SECTOR 17 · CHANDIGARH   ← 12px Inter, #C8FF00, letter-spacing 3px
[h1]       YOUR GYM.
           YOUR SPACE.
           YOUR GOALS.              ← Bebas Neue, clamp(52px,8vw,100px), white
[body]     Chandigarh's most advanced wellness club.
           State-of-the-art equipment, expert trainers,
           and a community that drives results.
[buttons]
  <a href="https://wa.me/917268090909">Join Now ↗</a>   ← lime pill button
  <a href="#gallery">View Gallery</a>                     ← ghost pill (white border)
```

**Bottom-left badge:**
```
⭐ 4.6 Rating · 734+ Members Love Us
```
Style: `background: rgba(255,255,255,0.08); backdrop-filter: blur(8px); border-radius: 8px; padding: 12px 20px`

---

### [3] ABOUT STRIP

**Layout:** Full-width · `background: #111111` · 2-column row

**Left column:** `OUR STUDIO` in 12px uppercase lime-green

**Right column:** 
```
Discover what makes Octane Wellness Club special. Experience
state-of-the-art facilities designed for every fitness level —
from heavy strength zones to cardio suites and personal training areas.
```
Font: 18px Inter, color: #888

**Divider top/bottom:** `border: 1px solid #2A2A2A`

---

### [4] PHOTO GALLERY

**Section eyebrow:** `OUR SPACE`
**Section heading:** `TRAIN IN A WORLD-CLASS FACILITY`

**12 photo cards — use these Unsplash URLs:**

```js
const gymPhotos = [
  { url: "https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=800&q=80", label: "Main Gym Floor" },
  { url: "https://images.unsplash.com/photo-1571902943202-507ec2618e8f?w=800&q=80", label: "Strength Zone" },
  { url: "https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=800&q=80", label: "Cardio Suite" },
  { url: "https://images.unsplash.com/photo-1517836357463-d25dfeac3438?w=800&q=80", label: "Free Weights" },
  { url: "https://images.unsplash.com/photo-1540497077202-7c8a3999166f?w=800&q=80", label: "Olympic Platform" },
  { url: "https://images.unsplash.com/photo-1576678927484-cc907957088c?w=800&q=80", label: "Functional Training" },
  { url: "https://images.unsplash.com/photo-1549060279-7e168fcee0c2?w=800&q=80", label: "Personal Training" },
  { url: "https://images.unsplash.com/photo-1623874514711-0f321325f318?w=800&q=80", label: "Locker Room" },
  { url: "https://images.unsplash.com/photo-1583454110551-21f2fa2afe61?w=800&q=80", label: "Yoga & Stretch" },
  { url: "https://images.unsplash.com/photo-1526506118085-60ce8714f8c5?w=800&q=80", label: "Boxing Zone" },
  { url: "https://images.unsplash.com/photo-1593079831268-3381b0db4a77?w=800&q=80", label: "Cycling Studio" },
  { url: "https://images.unsplash.com/photo-1460925895917-afdab827c52f?w=800&q=80", label: "Reception" }
];
```

**Grid:**
```css
display: grid;
grid-template-columns: repeat(4, 1fr); /* desktop */
grid-template-columns: repeat(2, 1fr); /* tablet ≤1023px */
grid-template-columns: 1fr;            /* mobile ≤639px */
gap: 8px;
```

**Card hover:** label slides up from bottom as `background: rgba(200,255,0,0.9); color: #000; font-weight: 600`
Image: `transform: scale(1.05)` on hover · `overflow: hidden` · `aspect-ratio: 4/3`

---

### [5] SERVICES / FEATURES

**Section eyebrow:** `WHY OCTANE`
**Section heading:**
```
WE'RE MORE THAN JUST A GYM —
WE'RE YOUR PARTNER IN ACHIEVING GREATNESS
```

**6-card icon grid (3 columns desktop, 2 tablet, 1 mobile):**

| SVG Icon (inline) | Title | Description |
|---|---|---|
| dumbbell | Expert Trainers | Certified coaches with 5+ years experience guiding every rep |
| lightning | Modern Equipment | 200+ machines from premium brands — always maintained |
| lotus | Holistic Wellness | From strength training to yoga, complete health coverage |
| chart | Progress Tracking | Monthly assessments and customised plans for real results |
| shower | Premium Amenities | Clean changing rooms, showers, and locker facilities |
| clock | Flexible Hours | Open 6 AM–10:30 PM Mon–Sat · 5 AM–9 PM on Sundays |

**Card style:**
```css
background: #111;
border: 1px solid #2A2A2A;
border-radius: 8px;
padding: 32px 24px;
transition: border-color 0.2s;
```
Hover: `border-color: #C8FF00`
Icon: 32px, color `#C8FF00`

---

### [6] VIDEO REEL SECTION

**Section eyebrow:** `FEEL THE ENERGY`
**Section heading:** `WATCH OUR REELS`
**Subtitle:** Follow us on Instagram for daily fitness content

**3 video cards (3 cols desktop, 1 col mobile):**

```js
const videoReels = [
  {
    embedUrl: "https://www.youtube.com/embed/UItWltVZZmE",
    thumb: "https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=600&q=80",
    title: "Morning Strength Session",
    tag: "STRENGTH"
  },
  {
    embedUrl: "https://www.youtube.com/embed/cbKkB3POqaY",
    thumb: "https://images.unsplash.com/photo-1571902943202-507ec2618e8f?w=600&q=80",
    title: "Full Body HIIT Workout",
    tag: "HIIT"
  },
  {
    embedUrl: "https://www.youtube.com/embed/oAPCPjnU1wA",
    thumb: "https://images.unsplash.com/photo-1540497077202-7c8a3999166f?w=600&q=80",
    title: "Club Tour & Facilities",
    tag: "TOUR"
  }
];
```

**Behaviour:** Show thumbnail + lime play button overlay by default.
On click → replace with `<iframe src="embedUrl?autoplay=1" allowfullscreen>`
Tag badge: `background: #C8FF00; color: #000; font-size: 11px; padding: 4px 10px; border-radius: 4px`

**Below videos:**
```html
<a href="https://www.instagram.com/octanewellnessclub" target="_blank" class="btn-ghost">
  View All Reels on Instagram ↗
</a>
```

---

### [7] STATS BAR

**Full-width strip · `background: #111` · 4 stats in a row:**

```
734+           200+          5+            6 AM
Members        Machines      Trainers      Opens Daily
```

Bebas Neue 64px `#C8FF00` number · Inter 14px `#888` label below
Vertical dividers: `1px solid #2A2A2A` between each stat

---

### [8] TESTIMONIALS

**Section heading:** `WHAT OUR MEMBERS SAY`

**3 review cards (real Google reviews):**

```js
const reviews = [
  {
    name: "Verified Member",
    stars: 5,
    text: "Really nice gym, very spacious with good equipment. Extremely hygienic and the staff is highly professional. Trainer Ravi made me lose 4 kgs in just a week — a great motivator!"
  },
  {
    name: "Verified Member",
    stars: 5,
    text: "I recently joined Octane and my experience has been very good. The gym is well maintained and clean. Equipment is modern — everything required for strength training and cardio is available."
  },
  {
    name: "Long-Term Member",
    stars: 5,
    text: "With Octane for 2 years. Experienced and well-trained staff, contributing to the best gym environment. Training with Trainer Ravi for 6 months has helped me achieve my 2025 goals. Totally recommend!"
  }
];
```

**Card style:** `background: #111; border: 1px solid #2A2A2A; border-radius: 8px; padding: 28px`
Stars in `#C8FF00` · quote text in `#888` · name in white bold

---

### [9] LOCATION + MAP

**2-column layout (50/50 desktop · stacked mobile):**

**Left — contact details:**
```
[label]  FIND US

📍 Address
SCO 73-79, Shopping Plaza,
Sector 17D, Chandigarh – 160017

🕐 Opening Hours
Mon – Sat : 6:00 AM – 10:30 PM
Sunday    : 5:00 AM – 9:00 PM

📞 Phone
+91 72680 90909

💬 WhatsApp
https://wa.me/917268090909
```

**Right — Google Maps embed:**
```html
<iframe
  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3430.23!2d76.7820211!3d30.7410961!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x390fed0bcb322b6b%3A0x505fbea18b1e1df0!2sOctane%20Wellness%20Club!5e0!3m2!1sen!2sin"
  width="100%"
  height="420"
  style="border:0; filter: grayscale(100%) invert(92%) contrast(83%); border-radius: 8px;"
  allowfullscreen=""
  loading="lazy">
</iframe>
```

> Map CSS filter gives it the dark Bartos-style look matching the reference image.

**Get Directions button:**
```html
<a href="https://maps.google.com/?q=Octane+Wellness+Club+Sector+17+Chandigarh" target="_blank" class="btn-ghost">
  Get Directions ↗
</a>
```

---

### [10] FAQ

**2-column layout:**

**Left (large type):**
```
FAQ

ALL YOUR
QUERIES
ANSWERED.
```
Bebas Neue, clamp(40px, 5vw, 64px)

**Right — JS accordion:**

```js
const faqs = [
  {
    q: "What are your membership plans?",
    a: "We offer monthly, quarterly, and annual plans. Contact us on WhatsApp at +91 72680 90909 for current pricing and offers."
  },
  {
    q: "Is personal training available?",
    a: "Yes! We have certified personal trainers for one-on-one sessions. Trainer Ravi has helped hundreds of members achieve their fitness goals."
  },
  {
    q: "Can I try before joining?",
    a: "Yes, we offer a free trial session. Walk in to our Sector 17D facility or WhatsApp us to schedule your visit."
  },
  {
    q: "What facilities are included?",
    a: "State-of-the-art gym floor, 200+ machines, cardio suite, strength zone, functional training area, changing rooms, showers, and lockers."
  },
  {
    q: "Do you offer group classes?",
    a: "Yes, we run group fitness classes including HIIT, yoga, and functional training. Schedule is updated monthly."
  },
  {
    q: "Is there parking available?",
    a: "Yes, ample parking is available at the SCO Shopping Plaza, Sector 17D, Chandigarh."
  }
];
```

**Accordion behaviour:**
- Default closed: `border-bottom: 1px solid #2A2A2A` · question in white 16px · `+` right-aligned
- Open: answer animates down via `max-height` transition · `+` becomes `−` · `border-bottom: 1px solid #C8FF00`

---

### [11] CTA BANNER

**Full-width · background image + dark overlay:**
```
https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?w=1600&q=80
```
Overlay: `background: rgba(0,0,0,0.75)`

**Centered content:**
```
READY TO START YOUR
FITNESS JOURNEY?

Join a community that motivates you, trains with the
best tech, and supports every goal — big or small.

[Join Now on WhatsApp ↗]    [Call Us: +91 72680 90909]
```

---

### [12] FOOTER

**4-column grid (desktop) · 2-col tablet · 1-col mobile:**

| Col 1 — Brand | Col 2 — Quick Links | Col 3 — Hours | Col 4 — Contact |
|---|---|---|---|
| OCTANE WELLNESS CLUB | About Us | Mon–Sat: 6:00 AM–10:30 PM | +91 72680 90909 |
| Sector 17D, Chandigarh | Gallery | Sunday: 5:00 AM–9:00 PM | hello@octanewellness.com |
| +91 72680 90909 | Services | | SCO 73-79, Sector 17D |
| [IG] [WA] [Maps] icons | Membership | | Chandigarh – 160017 |
| | Contact | | |

**Bottom bar:**
```
© 2025 Octane Wellness Club · All rights reserved.
```
`border-top: 1px solid #2A2A2A` · centered · 14px muted

---

## 5. WhatsApp Floating Button (Fixed)

```html
<a href="https://wa.me/917268090909?text=Hi%2C%20I%27m%20interested%20in%20joining%20Octane%20Wellness%20Club"
   class="whatsapp-fab"
   target="_blank"
   aria-label="Chat on WhatsApp">
  <!-- WhatsApp SVG icon, white, 28px -->
</a>
```

```css
.whatsapp-fab {
  position: fixed;
  bottom: 28px;
  right: 28px;
  z-index: 9999;
  width: 60px;
  height: 60px;
  background: #25D366;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 20px rgba(37,211,102,0.4);
  transition: transform 0.2s, box-shadow 0.2s;
}
.whatsapp-fab:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 28px rgba(37,211,102,0.6);
}
```

---

## 6. JavaScript Behaviours

| Feature | Implementation |
|---------|---------------|
| Smooth scroll | `scroll-behavior: smooth` on `html` element |
| Active nav link | `IntersectionObserver` on each section — add `.active` class to matching nav link |
| FAQ accordion | Toggle `.open` class → `max-height: 0` to `max-height: 500px` with `transition: 0.3s ease` |
| Gallery hover | CSS `:hover` + `transform: scale(1.05)` with `overflow: hidden` |
| Video click-to-play | Replace `<img>` thumbnail with `<iframe autoplay=1>` on click |
| Navbar scroll state | Add `.scrolled` class at `scrollY > 50` → stronger backdrop blur |
| Mobile hamburger | Toggle `.nav-open` class → full-screen overlay nav |
| Scroll reveal | `IntersectionObserver` → add `.visible` → `opacity: 0; transform: translateY(24px)` to `opacity:1; transform:none` |

---

## 7. Responsive Breakpoints

```css
/* Desktop  */ @media (min-width: 1024px)
/* Tablet   */ @media (max-width: 1023px) and (min-width: 640px)
/* Mobile   */ @media (max-width: 639px)
```

| Section | Desktop | Tablet | Mobile |
|---------|---------|--------|--------|
| Gallery | 4 cols | 2 cols | 1 col |
| Services | 3 cols | 2 cols | 1 col |
| Videos | 3 cols | 2 cols | 1 col |
| Testimonials | 3 cols | 2 cols | 1 col |
| Location | 2 cols | stacked | stacked |
| FAQ | 2 cols | stacked | stacked |
| Footer | 4 cols | 2 cols | 1 col |
| Stats | 4-in-row | 2×2 | 2×2 |

---

## 8. SEO & Meta Tags

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Octane Wellness Club | Best Gym in Sector 17, Chandigarh</title>
<meta name="description" content="Octane Wellness Club — Chandigarh's premier fitness destination at Sector 17D. State-of-the-art equipment, expert trainers, open 6 AM daily. Join today!">
<meta name="keywords" content="gym chandigarh, fitness club sector 17, best gym chandigarh, octane wellness, personal trainer chandigarh">
<meta property="og:title" content="Octane Wellness Club | Sector 17, Chandigarh">
<meta property="og:description" content="Chandigarh's most advanced wellness club. 200+ machines, expert trainers, open 6 AM daily.">
<meta property="og:image" content="https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=1200&q=80">
<link rel="canonical" href="https://octanewellness.com">
```

---

## 9. File Structure

```
octane-wellness/
├── index.html      ← single file (HTML + CSS + JS all inline)
└── assets/         ← replace Unsplash URLs with real photos here
    ├── gym-1.jpg
    ├── gym-2.jpg
    └── logo.png
```

> All images use live Unsplash URLs — no local assets needed to run immediately.
> Replace with real client photos when provided.

---

## 10. All Key External Links

| Purpose | URL |
|---------|-----|
| WhatsApp Chat | `https://wa.me/917268090909` |
| WhatsApp with message | `https://wa.me/917268090909?text=Hi%2C%20I%27m%20interested%20in%20joining%20Octane%20Wellness%20Club` |
| Google Maps directions | `https://maps.google.com/?q=Octane+Wellness+Club+Sector+17+Chandigarh` |
| Google Maps embed | `https://www.google.com/maps/embed?pb=...ChIJazILzUftDzkR8B0uh4G-XFA` |
| Instagram | `https://www.instagram.com/octanewellnessclub` |
| Hero image (Unsplash) | `https://images.unsplash.com/photo-1534438327276-14e5300c3a48?w=1600&q=80` |
| CTA banner image | `https://images.unsplash.com/photo-1581009146145-b5ef050c2e1e?w=1600&q=80` |

---

## 11. Prompt to Paste into Your Vibe Coding Tool

> Copy this entire block + attach the reference image (Bartos Gym screenshot) + attach this PRD file:

```
Build a single-file HTML/CSS/JS website for "Octane Wellness Club" using
the attached PRD and the reference image (Bartos Gym dark UI).

DESIGN RULES (match reference image exactly):
- Background: #0A0A0A (near-black)
- Accent: #C8FF00 (lime-green) for all CTAs, highlights, hover borders
- Display font: Bebas Neue (Google Fonts) for all headings
- Body font: Inter (Google Fonts) for all text
- No gradients · No drop shadows · Flat and bold
- Pill buttons with border-radius: 999px
- 2px lime-green border accent on hover cards and active nav

SECTIONS (build all 12 in this order):
1. Fixed navbar with logo, nav links, lime CTA button
2. Full-viewport hero with gym background image + dark overlay
3. About strip (2-column, muted description)
4. 12-photo gallery grid (4 cols desktop, hover label reveal)
5. 6 service/feature cards (icon + title + description)
6. 3 video reels (thumbnail + play button → iframe on click)
7. Stats bar (734+ Members · 200+ Machines · 5+ Trainers · 6 AM Opens)
8. 3 testimonial cards (real member reviews)
9. Location section (contact details + dark-filtered Google Maps embed)
10. FAQ accordion (JS toggle, lime bottom border on open)
11. CTA banner (full-width bg image + 2 buttons)
12. Footer (4-column grid + social icons)

FIXED ELEMENT: WhatsApp floating button (bottom-right, #25D366 green circle)

Use all image URLs, embed URLs, contact info, and copy from the PRD exactly.
Output: single index.html file with all CSS and JS inline. No external files.
```

---

*PRD Version 1.0 · Octane Wellness Club · Sector 17D, Chandigarh · June 2025*
