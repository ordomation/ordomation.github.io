# GEMINI TASK: Elite Ordomation Landing Page Transformation

## Mission

Transform the current Ordomation landing page into an **elite conversion machine** that sells the vision instantly. The site has solid foundations (Astro + GSAP) but needs strategic improvements in storytelling, specificity, and conversion architecture.

**Target Quality:** Stripe.com / Linear.app level premium feel.

---

## CRITICAL: Business Context (READ THIS FIRST)

**Ordomation** is the product being built. It is an AI-powered document automation service for Danish small businesses.

**The Founders:**
- **Thue Tonnesen** - Co-Founder, Infrastructure
  - LinkedIn: https://www.linkedin.com/in/thue-tonnesen-414475245/
  - GitHub: https://github.com/Thue-T
  - Bio: "Server architect who built infrastructure processing 14,000+ emails."

- **Joachim Gensmann** - Co-Founder, Strategy
  - LinkedIn: https://www.linkedin.com/in/joachim-gensmann/
  - Bio: "Product thinker who ensures Ordomation solves real problems."

**Client Businesses (NOT founded by the Ordomation team):**
- **TST Maskiner** - Machine/equipment business
- **Baskas** - Food/takeaway business
- **GreenGuard** - Environmental/garden business
- **Glare** - Fashion/retail business

These are **clients** that Ordomation helps automate. The founders did NOT build these businesses. They built Ordomation to help businesses like these.

**DO NOT make these mistakes:**
- Never say "We built GreenGuard" or "our company GreenGuard"
- Never write "Joachim Ovesen" - the correct name is "Joachim Gensmann"
- Never confuse client businesses with Ordomation itself

---

## CRITICAL: Instant Feedback Workflow

**You MUST use visual feedback for this task:**

1. After EVERY component change, run `npm run dev`
2. Open browser to http://localhost:4321
3. **Take a screenshot** of the result
4. Analyze: Does it look premium? Does it match Stripe/Linear quality?
5. If not perfect, **iterate and fix**
6. Continue until the visual is **exactly right**
7. Test mobile view (375px) after each major section

**The goal is pixel-perfect execution.** Don't settle for "good enough" - keep iterating until each section looks as polished as the reference sites.

### Test Checklist After Each Section:
- [ ] Does it look premium on desktop?
- [ ] Does it look premium on mobile (375px)?
- [ ] Are animations smooth (60fps)?
- [ ] Is text readable and hierarchy clear?
- [ ] Do hover states feel responsive?

---

## Design References

Study these before building:
- https://stripe.com - Bento grids, progressive disclosure, ambient motion
- https://linear.app - Precision minimalism, purposeful motion, dark theme
- https://vercel.com - Bold simplicity, technical authenticity
- https://raycast.com - Emotional positioning, glassmorphism, 3D elements
- https://arc.net - Vibrant accent colors, generous whitespace

---

## Technical Stack

- **Framework:** Astro 4.x
- **Animations:** GSAP + ScrollTrigger (already installed)
- **Styling:** Vanilla CSS (dark theme)
- **Forms:** n8n webhook submission
- **Hosting:** GitHub Pages

---

## Color Palette (DARK THEME ONLY)

```css
:root {
  /* Existing */
  --bg-primary: #0a0a0a;
  --bg-secondary: #141414;
  --bg-card: #1a1a1a;
  --text-primary: #fafafa;
  --text-muted: #737373;
  --accent: #3b82f6;
  --accent-glow: rgba(59, 130, 246, 0.5);
  --gradient-1: #6366f1;
  --gradient-2: #8b5cf6;
  --gradient-3: #ec4899;

  /* New Additions */
  --accent-hover: #2563eb;
  --success: #22c55e;
  --glass-bg: rgba(26, 26, 26, 0.6);
  --glass-border: rgba(255, 255, 255, 0.05);
  --glass-blur: 16px;
}
```

---

## NEW SITE ARCHITECTURE (12 Sections)

Build in this order:

```
1.  NAVIGATION          - Sticky, minimal, smart scroll
2.  HERO                - New copy + product visual + 2 CTAs
3.  SOCIAL PROOF BAR    - Metrics + business logos
4.  PROBLEM             - Emotional pain statement
5.  LIVE DEMO           - Product visualization (replaces Vision)
6.  HOW IT WORKS        - 3 concrete steps (replaces Journey)
7.  FEATURES            - Bento box grid (NEW)
8.  BENEFITS            - Enhanced with metrics
9.  TESTIMONIALS        - Quote carousel (NEW)
10. FOUNDERS            - Real photos + bios
11. CTA/WAITLIST        - Email capture (NEW)
12. FOOTER              - Multi-column layout
```

---

## SECTION 1: NAVIGATION (New Component)

**File:** `src/components/Nav.astro`

### Visual:
```
+------------------------------------------------------------------+
|  [O] ORDOMATION          Features  How It Works  Team  [Contact] |
+------------------------------------------------------------------+
```

### Specifications:
- **Position:** Fixed top, starts transparent
- **Scroll behavior:** Gains `backdrop-filter: blur(16px)` and `background: rgba(10,10,10,0.9)` after 50px scroll
- **Height:** 64px desktop, 56px mobile
- **Logo:** "ORDOMATION" in Inter 700, 20px
  - The "O" should have animated gradient fill (uses --gradient-1/2/3)
- **Links:** Smooth scroll to section IDs, 16px Inter 500
  - Default: `opacity: 0.7`
  - Hover: `opacity: 1`
- **Contact CTA:** Pill button with `background: var(--accent)`, `border-radius: 9999px`
- **Mobile (< 768px):** Hamburger menu, slide-in from right, full-height overlay

### GSAP Animation:
```javascript
gsap.to(".nav", {
  backgroundColor: "rgba(10,10,10,0.95)",
  backdropFilter: "blur(16px)",
  scrollTrigger: {
    trigger: "body",
    start: "50px top",
    toggleActions: "play none none reverse"
  }
});
```

---

## SECTION 2: HERO (Complete Redesign)

**File:** `src/components/Hero.astro`

### Visual:
```
+------------------------------------------------------------------+
|                    [Animated gradient mesh - subtle]              |
|                                                                   |
|           Every invoice. Every receipt.                           |
|           Organized before you blink.                             |
|                                                                   |
|     AI-powered document automation for Danish small businesses.   |
|     From inbox chaos to SKAT-ready books, automatically.          |
|                                                                   |
|     [Join the Waitlist]        [Watch Demo]                       |
|                                                                   |
|                    [Product Mockup/Animation]                     |
|                                                                   |
+------------------------------------------------------------------+
```

### New Copy:
**Headline:**
> "Every invoice. Every receipt. Organized before you blink."

**Subheadline:**
> AI-powered document automation for Danish small businesses. From inbox chaos to SKAT-ready books, automatically.

### Two CTAs:
1. **Primary:** "Join the Waitlist"
   - Opens modal with email input form
   - Glow effect on hover
   - `background: var(--accent)`

2. **Secondary:** "Watch Demo"
   - Scrolls to #live-demo section
   - Ghost button style: `border: 1px solid rgba(255,255,255,0.2)`
   - Arrow icon

### Product Visual:
Create an animated email-to-folder flow visualization:
- Left: Email inbox icon with "3 new invoices" badge
- Center: AI processing orb with sparkle animation
- Right: Folder tree building itself (Q1/2026/Baskas/001_invoice.pdf)

**OR** create a floating browser mockup showing a dashboard (use CSS perspective transform for 3D effect).

### Visual Enhancements:
- Keep animated gradient but reduce opacity to 0.4 (too distracting currently)
- Add noise texture overlay: `background-image: url(/noise.svg); opacity: 0.03;`
- Add subtle grid pattern: `background: linear-gradient(rgba(59, 130, 246, 0.03) 1px, transparent 1px)`
- Product visual should have subtle parallax on scroll

---

## SECTION 3: SOCIAL PROOF BAR (New Component)

**File:** `src/components/SocialProof.astro`

### Visual:
```
+------------------------------------------------------------------+
|  Currently automating for:                                        |
|                                                                   |
|  [TST Maskiner]  [Baskas]  [GreenGuard]  [Glare]                 |
|                                                                   |
|  "14,000+ emails processed"  |  "4 businesses automated"         |
+------------------------------------------------------------------+
```

### Specifications:
- **Background:** `var(--bg-secondary)` with subtle gradient fade at top
- **Logos:** Create simple text-based logo placeholders
  - Text in Inter 600, styled to look like minimal wordmarks
  - Grayscale at 0.5 opacity, full opacity + accent color on hover
- **Metrics:** Counter animation on scroll-into-view (counts up from 0)
- **Layout:** Centered, generous padding (80px vertical)

### Logo Creation (Simple Text Style):
```css
.logo-text {
  font-size: 18px;
  font-weight: 600;
  letter-spacing: 0.05em;
  color: var(--text-muted);
  transition: color 0.3s ease;
}
.logo-text:hover {
  color: var(--accent);
}
```

---

## SECTION 4: PROBLEM (Replaces PainPoints)

**File:** `src/components/Problem.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|       "Every morning, 47 new emails.                              |
|        Buried somewhere: the invoice you need for VAT."           |
|                                                                   |
|       ----                                                        |
|                                                                   |
|       Sound familiar?                                             |
|                                                                   |
|       You're not bad at bookkeeping.                              |
|       The tools just weren't built for small businesses.          |
|                                                                   |
+------------------------------------------------------------------+
```

### Specifications:
- **Layout:** Full-width, centered text
- **Padding:** 200px vertical (generous whitespace)
- **Background:** Subtle radial gradient from center (dark purple at 2% opacity)
- **Typography:**
  - Main quote: 36px, line-height 1.3
  - Horizontal rule: thin line, 60px wide, centered
  - "Sound familiar?": 24px, var(--accent)
  - Explanation: 20px, var(--text-muted)
- **Animation:** Text fades up with 0.3s stagger between lines

---

## SECTION 5: LIVE DEMO (Replaces Vision)

**File:** `src/components/LiveDemo.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|       Watch it work.                                              |
|                                                                   |
|   +-------------------+         +-------------------+             |
|   |                   |   -->   |                   |             |
|   |   [Email Inbox]   |   AI    |  [Organized Folder]|            |
|   |   3 new invoices  |  Magic  |  Q1/2026/Baskas   |             |
|   |                   |         |  ├── 001_invoice  |             |
|   +-------------------+         |  ├── 002_receipt  |             |
|                                 |  └── 003_credit   |             |
|                                 +-------------------+             |
|                                                                   |
+------------------------------------------------------------------+
```

### Headline:
> "Watch it work."

### Concept:
Replace the abstract particle convergence with a **concrete product demonstration**.

### Animation Sequence (scroll-triggered):
1. Email inbox panel appears (left side)
2. 3 email items slide in
3. Arrow/connection animates toward center
4. AI processing orb pulses with glow
5. Folder structure builds itself on right
6. Files animate into folders

### Technical Approach:
- Use GSAP ScrollTrigger timeline
- SVG icons for email and folder
- CSS animations for the particles/processing
- Staggered reveal for folder contents

---

## SECTION 6: HOW IT WORKS (Replaces Journey)

**File:** `src/components/HowItWorks.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|       How Ordomation works                                        |
|                                                                   |
|   +--------+          +--------+          +--------+              |
|   |   01   |   ───>   |   02   |   ───>   |   03   |              |
|   | CONNECT|          |  SCAN  |          | ORGANIZE|             |
|   +--------+          +--------+          +--------+              |
|                                                                   |
|    Connect your       AI monitors         Files renamed,          |
|    Gmail accounts     every email,        dated, sorted.          |
|    in 2 minutes.      extracts data.      Ready for e-conomic.    |
|                                                                   |
+------------------------------------------------------------------+
```

### Three Steps:

| Step | Number | Title | Description | Icon |
|------|--------|-------|-------------|------|
| 1 | 01 | CONNECT | Connect your Gmail accounts in under 2 minutes. Multiple businesses, one dashboard. | Link/chain icon |
| 2 | 02 | SCAN | AI reads every incoming email. Invoices, receipts, and credit notes extracted automatically. | Scanner/eye icon |
| 3 | 03 | ORGANIZE | Files renamed, dated, and sorted by quarter. Ready for e-conomic, Dinero, or your accountant. | Folder icon |

### Specifications:
- **Layout:** Horizontal on desktop, vertical stack on mobile
- **Numbers:** Large, bold, with gradient fill
- **Connecting lines:** Draw on scroll (SVG path animation)
- **Colors:** Gradient from purple (01) to blue (02) to green (03)
- **Animation:** Steps fade in sequentially, 0.2s stagger

---

## SECTION 7: FEATURES BENTO BOX (New Component)

**File:** `src/components/Features.astro`

### Visual (Stripe-style bento grid):
```
+---------------------------+  +------------+  +------------+
|   Multi-Account           |  |    AI      |  |   SKAT     |
|   Monitoring              |  |  Extract   |  | Compliant  |
|   [Large card]            |  |            |  |            |
+---------------------------+  +------------+  +------------+
+------------+  +------------+  +---------------------------+
|   Auto-    |  |   Smart    |  |      e-conomic Ready      |
|   Rename   |  |  Folders   |  |      [Large card]         |
+------------+  +------------+  +---------------------------+
```

### 6 Feature Cards:

| Feature | Title | Description | Visual |
|---------|-------|-------------|--------|
| 1 (Large) | Multi-Account Monitoring | Monitor Gmail for TST, Baskas, GreenGuard, Glare - all in one place | Email icons flowing to hub |
| 2 | AI Extraction | Amount, date, supplier, CVR number - pulled from PDFs automatically | Text appearing on doc |
| 3 | SKAT Compliance | 5-year retention, quarterly organization, audit-ready folders | Checkmark + DK flag |
| 4 | Smart Naming | Files renamed consistently: `001_invoice_supplier_date.pdf` | Before/after file icons |
| 5 | Auto-Sorting | Q1/2026/Business/ structure created automatically | Folder tree animation |
| 6 (Large) | e-conomic Ready | Export directly or download organized archives | e-conomic text + export arrow |

### CSS Grid:
```css
.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: var(--space-md);
}

.feature-card.large {
  grid-column: span 2;
}

.feature-card {
  background: var(--glass-bg);
  backdrop-filter: blur(var(--glass-blur));
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: var(--space-xl);
}
```

---

## SECTION 8: BENEFITS (Enhanced Copy)

**File:** `src/components/Benefits.astro`

### Keep existing structure but update copy:

| Benefit | Old Copy | New Copy |
|---------|----------|----------|
| TIME | "Hours back every week" | "8 hours back every month. That's a full workday for your business, not your inbox." |
| CLARITY | "Financial overview" | "One dashboard. Every invoice. Every receipt. Search by date, amount, or supplier instantly." |
| CONTROL | "Better decisions" | "Quarterly VAT prep in 10 minutes, not 10 hours. Your accountant will thank you." |

### Enhancements:
- Add specific metrics (8 hours, 10 minutes)
- Mention Danish context (VAT prep, SKAT)
- Include comparison ("not 10 hours")

---

## SECTION 9: TESTIMONIALS (New Component)

**File:** `src/components/Testimonials.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|       What our users say                                          |
|                                                                   |
|   +------------------------------------------------------+        |
|   |                                                      |        |
|   |  "I used to spend every Sunday sorting invoices.     |        |
|   |   Now I check Ordomation once a week and             |        |
|   |   everything is already done."                       |        |
|   |                                                      |        |
|   |                        - Thue, Ordomation Founder    |        |
|   +------------------------------------------------------+        |
|                                                                   |
|   [ < ]  1/3  [ > ]                                               |
|                                                                   |
+------------------------------------------------------------------+
```

### 3 Testimonials (use founder quotes for now):

1. **Thue Tonnesen, Ordomation**
> "I built this because I was tired of spending Sundays sorting invoices. Now the system does it while I sleep."

2. **Joachim Gensmann, Ordomation**
> "Small businesses deserve enterprise-grade automation. We're making that accessible."

3. **Beta User (placeholder)**
> "Finally, a tool that understands how Danish businesses actually work. SKAT compliance built in."

### Specifications:
- **Carousel:** Auto-rotate every 5 seconds, pause on hover
- **Navigation:** Dots or arrows
- **Animation:** Smooth crossfade between quotes
- **Quote styling:** Large quote marks, italic text, muted author name

---

## SECTION 10: FOUNDERS (Enhanced)

**File:** `src/components/Founders.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|       Meet the team                                               |
|                                                                   |
|   +------------------+              +------------------+          |
|   |                  |              |                  |          |
|   |    [PHOTO]       |              |    [PHOTO]       |          |
|   |                  |              |                  |          |
|   +------------------+              +------------------+          |
|                                                                   |
|     Thue Tonnesen                  Joachim Gensmann              |
|     Infrastructure                  Strategy                      |
|                                                                   |
|     [LinkedIn] [GitHub]             [LinkedIn]                    |
|                                                                   |
|    "Server architect who          "Product thinker who            |
|     built infrastructure           makes sure Ordomation          |
|     for 14K+ emails."              solves real problems."         |
|                                                                   |
|   ─────────────────────────────────────────────────────           |
|                                                                   |
|   "Friends since HTX Haderslev. We saw small businesses           |
|    struggle with manual processes that big companies              |
|    automate away. Ordomation is our answer."                      |
|                                                                   |
+------------------------------------------------------------------+
```

### Photo Placeholders:
**USER WILL PROVIDE ACTUAL PHOTOS.** For now, create styled placeholder circles:
- Gradient background using --gradient-1/2
- Initials "TT" and "JG" as fallback
- Size: 120px x 120px, circular
- Path: `public/images/thue.jpg` and `public/images/joachim.jpg`

### Correct Information:
- **Thue Tonnesen** (Infrastructure)
  - LinkedIn: https://www.linkedin.com/in/thue-tonnesen-414475245/
  - GitHub: https://github.com/Thue-T
  - Bio: "Server architect who built infrastructure for 14,000+ emails."

- **Joachim Gensmann** (Strategy)
  - LinkedIn: https://www.linkedin.com/in/joachim-gensmann/
  - Bio: "Product thinker who makes sure Ordomation solves real problems."

### Shared Story:
> "Friends since HTX Haderslev. We saw small businesses struggle with manual processes that big companies automate away. Ordomation is our answer: enterprise-grade automation at prices Danish SMBs can actually afford."

---

## SECTION 11: WAITLIST CTA (New Component - Critical)

**File:** `src/components/Waitlist.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|  +---------------------------------------------------------+      |
|  |                                                         |      |
|  |      Ready to stop sorting invoices?                    |      |
|  |                                                         |      |
|  |      Join the waitlist. Early access starts Q2 2026.    |      |
|  |                                                         |      |
|  |      +---------------------------+  +-----------+       |      |
|  |      | your@email.com            |  | Join Now  |       |      |
|  |      +---------------------------+  +-----------+       |      |
|  |                                                         |      |
|  |      No spam. Unsubscribe anytime. Danish-hosted.       |      |
|  |                                                         |      |
|  +---------------------------------------------------------+      |
|                                                                   |
+------------------------------------------------------------------+
```

### Copy:
- **Headline:** "Ready to stop sorting invoices?"
- **Subheadline:** "Join the waitlist. Early access starts Q2 2026."
- **Input placeholder:** "your@email.com"
- **Button:** "Join Now" or "Get Early Access"
- **Trust text:** "No spam. Unsubscribe anytime. Danish-hosted."

### Specifications:
- **Card:** Glassmorphism effect
- **Border:** Animated gradient border (like Linear's signup)
- **Input:** Large, clean, white text on dark
- **Button:** `background: var(--accent)`, full-width on mobile

### Form Submission:
**POST to n8n webhook (user's choice)**

```html
<form action="https://192.168.0.195:30678/webhook/waitlist" method="POST">
  <input type="email" name="email" placeholder="your@email.com" required />
  <button type="submit">Join Now</button>
</form>
```

Note: The exact webhook URL will be configured later. For now, create the form structure and add a TODO comment.

### Animated Border:
```css
.waitlist-card {
  position: relative;
  background: var(--glass-bg);
  border-radius: 24px;
}

.waitlist-card::before {
  content: '';
  position: absolute;
  inset: -2px;
  background: linear-gradient(
    90deg,
    var(--gradient-1),
    var(--gradient-2),
    var(--gradient-3),
    var(--gradient-1)
  );
  background-size: 300% 100%;
  border-radius: 26px;
  z-index: -1;
  animation: gradient-border 3s linear infinite;
}

@keyframes gradient-border {
  0% { background-position: 0% 50%; }
  100% { background-position: 300% 50%; }
}
```

---

## SECTION 12: FOOTER (Enhanced)

**File:** `src/components/Footer.astro`

### Visual:
```
+------------------------------------------------------------------+
|                                                                   |
|  ORDOMATION               Product           Company               |
|                           Features          About                 |
|  Intelligent automation   How It Works      Team                  |
|  for Danish SMBs          Roadmap           Contact               |
|                                             GitHub                |
|                                                                   |
|  ─────────────────────────────────────────────────────────────   |
|                                                                   |
|  [GitHub] [LinkedIn]      hello@ordomation.com         Denmark    |
|                                                                   |
|  (c) 2026 Ordomation      Privacy  Terms                          |
|                                                                   |
+------------------------------------------------------------------+
```

### Three-Column Layout:
1. **Logo + Tagline:** "Intelligent automation for Danish SMBs"
2. **Product Links:** Features, How It Works, Roadmap (anchor links)
3. **Company Links:** About (scrolls to founders), Team, Contact, GitHub

### Bottom Row:
- Social icons: GitHub, LinkedIn
- Email: hello@ordomation.com
- Location: Denmark (with flag emoji)
- Copyright: (c) 2026 Ordomation
- Legal links: Privacy, Terms (can be placeholder # links)

---

## UPDATE index.astro

**File:** `src/pages/index.astro`

```astro
---
import Layout from '../layouts/Layout.astro';
import Nav from '../components/Nav.astro';
import Hero from '../components/Hero.astro';
import SocialProof from '../components/SocialProof.astro';
import Problem from '../components/Problem.astro';
import LiveDemo from '../components/LiveDemo.astro';
import HowItWorks from '../components/HowItWorks.astro';
import Features from '../components/Features.astro';
import Benefits from '../components/Benefits.astro';
import Testimonials from '../components/Testimonials.astro';
import Founders from '../components/Founders.astro';
import Waitlist from '../components/Waitlist.astro';
import Footer from '../components/Footer.astro';
---

<Layout title="Ordomation - Intelligent Business Automation">
  <Nav />
  <main>
    <Hero />
    <SocialProof />
    <Problem />
    <LiveDemo />
    <HowItWorks />
    <Features />
    <Benefits />
    <Testimonials />
    <Founders />
    <Waitlist />
  </main>
  <Footer />
</Layout>
```

---

## FILE STRUCTURE (Final)

```
src/
├── layouts/
│   └── Layout.astro
├── components/
│   ├── Nav.astro              # NEW
│   ├── Hero.astro             # REDESIGN
│   ├── SocialProof.astro      # NEW
│   ├── Problem.astro          # NEW (replaces PainPoints)
│   ├── LiveDemo.astro         # NEW (replaces Vision)
│   ├── HowItWorks.astro       # NEW (replaces Journey)
│   ├── Features.astro         # NEW
│   ├── Benefits.astro         # ENHANCE
│   ├── Testimonials.astro     # NEW
│   ├── Founders.astro         # ENHANCE
│   ├── Waitlist.astro         # NEW
│   └── Footer.astro           # ENHANCE
├── pages/
│   └── index.astro            # UPDATE imports
└── styles/
    └── global.css             # ADD new variables
public/
├── images/
│   ├── thue.jpg               # Placeholder for photo
│   └── joachim.jpg            # Placeholder for photo
└── CNAME
```

---

## TESTING CHECKLIST

After completing each section, verify:

### Desktop (1440px):
- [ ] Nav is sticky and blurs on scroll
- [ ] Hero headline is impactful, product visual renders
- [ ] Social proof metrics animate
- [ ] Problem section has emotional weight
- [ ] Live demo animation triggers on scroll
- [ ] How it works steps connect visually
- [ ] Features bento grid is aligned
- [ ] Benefits cards hover properly
- [ ] Testimonials rotate smoothly
- [ ] Founders photos display (or placeholders)
- [ ] Waitlist form submits (or shows TODO)
- [ ] Footer links work

### Mobile (375px):
- [ ] Nav hamburger works
- [ ] Hero stacks properly
- [ ] All sections readable
- [ ] Touch targets are 44px+
- [ ] No horizontal scroll

### Performance:
- [ ] Page loads in <3 seconds
- [ ] Lighthouse performance >80
- [ ] No console errors
- [ ] GSAP animations are 60fps

---

## DEPLOYMENT

When complete:
```bash
npm run build
git add .
git commit -m "Elite redesign: 12-section conversion-focused landing page"
git push origin main
```

GitHub Actions will auto-deploy to ordomation.com.

---

## VISION REMINDER

This site should make visitors FEEL the future, not understand the code.

- Don't explain how the AI works technically
- Don't list implementation details
- DO show transformation: chaos -> clarity
- DO make them want to join the waitlist
- DO feel as premium as Stripe or Linear
- DO resonate emotionally with Danish small business owners
