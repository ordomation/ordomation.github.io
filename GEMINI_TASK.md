# GEMINI TASK: Build Premium Ordomation Landing Page

## Mission
Create a dark, premium, interactive landing page that communicates VISION, not implementation. Think Stripe meets Linear meets futuristic data visualization. Minimal text, maximum impact.

## Design References
Study these before building:
- https://stripe.com - Animated gradients, premium feel
- https://linear.app - Precision minimalism, purposeful motion
- https://vercel.com - Bold simplicity, dark theme excellence

## Technical Stack
- **Framework:** Astro 4.x
- **Animations:** GSAP + ScrollTrigger (install via npm)
- **3D/WebGL:** Three.js for hero background (optional, CSS fallback acceptable)
- **Styling:** Vanilla CSS (dark theme)
- **Hosting:** GitHub Pages

## CRITICAL: Testing Requirements
After each major section, you MUST:
1. Run `npm run dev` and verify in browser
2. Test scroll animations work smoothly
3. Test on mobile viewport (375px)
4. Fix any errors before proceeding

---

## Color Palette (DARK THEME ONLY)

```css
:root {
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
}
```

---

## Typography

```css
/* Inter font - already imported */
h1 { font-size: clamp(40px, 8vw, 72px); font-weight: 700; letter-spacing: -0.03em; }
h2 { font-size: clamp(28px, 5vw, 48px); font-weight: 600; letter-spacing: -0.02em; }
h3 { font-size: clamp(20px, 3vw, 28px); font-weight: 600; }
body { font-size: 18px; line-height: 1.6; color: var(--text-primary); background: var(--bg-primary); }
.muted { color: var(--text-muted); }
```

---

## PAGE SECTIONS (Build in Order)

### 1. HERO SECTION

**File:** `src/components/Hero.astro`

**Visual:**
```
┌─────────────────────────────────────────────────────────────┐
│  [Animated gradient mesh background - purples/blues/pinks] │
│                                                             │
│                                                             │
│           Your business,                                    │
│           running itself.                                   │
│                                                             │
│     Intelligent automation that learns,                     │
│        organizes, and optimizes.                            │
│                                                             │
│              [ See the Vision ↓ ]                           │
│                                                             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Requirements:**
- Full viewport height (100vh)
- Animated gradient mesh background (CSS or Three.js)
  - Colors flow: indigo → purple → pink → back
  - Subtle, slow movement (20-30s cycle)
- Headline: "Your business, running itself."
- Subtext: "Intelligent automation that learns, organizes, and optimizes."
- Single CTA button with glow effect on hover
- Text fades in on load (0.5s delay, 1s duration)

**Gradient Animation (CSS approach):**
```css
.hero-bg {
  background: linear-gradient(-45deg, #0a0a0a, #1e1b4b, #4c1d95, #831843, #0a0a0a);
  background-size: 400% 400%;
  animation: gradient 20s ease infinite;
}
@keyframes gradient {
  0%, 100% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
}
```

---

### 2. THE JOURNEY - Scroll-Triggered Flow

**File:** `src/components/Journey.astro`

**Visual (horizontal transformation on scroll):**
```
SCROLL PROGRESS: ████████░░░░░░░░░░░░

[  📧  ]  →  [  🤖  ]  →  [  📊  ]  →  [  💡  ]
  Chaos       Process      Order       Insight

"Emails"    "AI Works"   "Structured"  "Decisions"
```

**Requirements:**
- Section height: 300vh (creates scroll distance)
- Content stays sticky while user scrolls
- 4 stages appear sequentially as user scrolls through
- Use GSAP ScrollTrigger for timeline:
  ```javascript
  // Install: npm install gsap
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  gsap.registerPlugin(ScrollTrigger);
  ```
- Each stage:
  - Icon (use SVG, animate stroke-dasharray for draw effect)
  - Single word label
  - Connecting line draws between stages
- Colors shift from red/orange (chaos) to blue/green (clarity)

**Stage Content:**
1. Chaos (red glow): Scattered email icon
2. Process (purple glow): AI/brain icon
3. Order (blue glow): Grid/structure icon
4. Insight (green glow): Lightbulb icon

---

### 3. ABSTRACT VISION - Particle Flow

**File:** `src/components/Vision.astro`

**Visual:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│    ○ ○ ○ ○ ○ ○ ○                                           │
│      ○ ○ ○ ○ ○  ↘                                          │
│        ○ ○ ○ ○    ↘                                        │
│          ○ ○ ○      → [ ◉ CLARITY ]                        │
│            ○ ○   ↗                                          │
│              ○ ↗                                            │
│    ○ ○ ○ ○ ○ ○                                             │
│                                                             │
│         "One glance. Complete clarity."                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Requirements:**
- Canvas element with particle animation (Three.js or vanilla Canvas)
- Small glowing orbs float randomly
- On scroll: orbs converge toward center point
- Center point pulses with glow
- Mouse interaction: orbs gently repel from cursor
- Text appears when particles fully converge

**Fallback (if Three.js too complex):**
- Use CSS with multiple animated `<div>` elements
- Apply transform animations on scroll
- Still achieves the visual effect

---

### 4. PAIN POINTS - Strike-Through Animation

**File:** `src/components/PainPoints.astro`

**Visual:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│     We remove the repetitive.                               │
│     You focus on what matters.                              │
│                                                             │
│     ~~Manual invoice sorting~~  →  Automatic                │
│     ~~Searching through emails~~  →  Instant                │
│     ~~Spreadsheet chaos~~  →  Structured                    │
│     ~~Repetitive bookkeeping~~  →  Handled                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Requirements:**
- Each line animates on scroll-into-view
- Strike-through is SVG line that draws across text
- Original text fades to 50% opacity
- Replacement text fades in from right
- Stagger animation: 0.3s delay between each line

**Animation Sequence (per line):**
1. Line visible, no strike
2. SVG line draws across (0.5s)
3. Text dims to muted
4. Arrow and replacement fade in (0.3s)

---

### 5. BENEFITS - Animated Cards

**File:** `src/components/Benefits.astro`

**Visual:**
```
┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
│       ⏱️        │  │       📈        │  │       🎯        │
│                 │  │                 │  │                 │
│      TIME       │  │    CLARITY      │  │    CONTROL      │
│                 │  │                 │  │                 │
│  Hours back     │  │  Financial      │  │  Better         │
│  every week     │  │  overview       │  │  decisions      │
└─────────────────┘  └─────────────────┘  └─────────────────┘
```

**Requirements:**
- 3 cards in row (stack on mobile)
- Cards have subtle border glow on hover
- Icons animate on scroll-into-view:
  - Time: Clock hands spin once
  - Clarity: Line graph draws itself
  - Control: Target crosshair pulses
- Glassmorphism effect: `backdrop-filter: blur(10px)`
- Cards scale slightly on hover (1.02)

---

### 6. FOUNDERS

**File:** `src/components/Founders.astro`

**Visual:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│        ┌────────┐              ┌────────┐                  │
│        │   TT   │              │   JG   │                  │
│        └────────┘              └────────┘                  │
│                                                             │
│     Thue Tonnesen          Joachim Gensmann                │
│      Infrastructure              Strategy                   │
│                                                             │
│        [in] [gh]                  [in]                     │
│                                                             │
│    "Friends since HTX Haderslev. Building what             │
│     small businesses deserve."                              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**CRITICAL - Correct Information:**
- **Thue Tonnesen** (NOT Tønnesen)
  - Role: Infrastructure
  - LinkedIn: https://www.linkedin.com/in/thue-tonnesen-414475245/
  - GitHub: https://github.com/Thue-T

- **Joachim Gensmann**
  - Role: Strategy
  - LinkedIn: https://www.linkedin.com/in/joachim-gensmann/

**Requirements:**
- Circular avatar placeholders with initials (TT, JG)
- Initials have gradient background matching brand
- Social links use simple icons, glow on hover
- Single shared story line below
- Fade in on scroll

---

### 7. FOOTER

**File:** `src/components/Footer.astro`

**Visual:**
```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  ORDOMATION                          hello@ordomation.com  │
│                                               Denmark 🇩🇰   │
│                                                 [GitHub]   │
│                                                             │
│  © 2026                                                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Requirements:**
- Minimal, two-column layout
- Same dark background as rest of site
- Email is mailto link
- GitHub links to https://github.com/ordomation
- No excessive links or content

---

## DEPENDENCIES TO INSTALL

```bash
npm install gsap
```

Add to `package.json` if not auto-added.

---

## FILE STRUCTURE (Final)

```
src/
├── layouts/
│   └── Layout.astro        # Dark theme, Inter font, GSAP script
├── components/
│   ├── Hero.astro          # Animated gradient hero
│   ├── Journey.astro       # Scroll-triggered 4-stage flow
│   ├── Vision.astro        # Particle convergence animation
│   ├── PainPoints.astro    # Strike-through animations
│   ├── Benefits.astro      # Animated benefit cards
│   ├── Founders.astro      # Team with correct info
│   └── Footer.astro        # Minimal footer
├── pages/
│   └── index.astro         # Imports all components
└── styles/
    └── global.css          # Dark theme, animations
```

---

## TESTING CHECKLIST

After building, verify:

- [ ] Hero gradient animates smoothly
- [ ] Journey section scroll-triggers work
- [ ] Particles/orbs animate (or CSS fallback works)
- [ ] Strike-through animations fire on scroll
- [ ] Benefit cards hover effects work
- [ ] All links work (LinkedIn, GitHub, email)
- [ ] Mobile responsive (test 375px, 768px, 1024px)
- [ ] No console errors
- [ ] Page loads in <3 seconds
- [ ] Lighthouse performance >80

---

## DEPLOYMENT

When complete:
```bash
git add .
git commit -m "Redesign: Premium dark theme with interactive animations"
git push origin main
```

GitHub Actions will auto-deploy to ordomation.com.

---

## REMINDER: VISION OVER IMPLEMENTATION

This site should make visitors FEEL the future, not understand the code.

- Don't explain how the AI works
- Don't list technical features
- Don't show architecture diagrams
- DO show transformation: chaos → clarity
- DO make them want to learn more
- DO feel premium and trustworthy
