# Ordomation Website Plan

**Domain:** ordomation.com
**Hosting:** GitHub Pages
**Type:** Static landing page
**Framework:** Plain HTML/CSS/JS (or Astro for simplicity)
**Date:** 2026-02-22

---

## Brand Identity

### Name Meaning
**Ordomation** = Order + Automation
Bringing order to business chaos through intelligent automation.

### Tagline Options
1. "Intelligent automation for small businesses"
2. "Order from chaos, automatically"
3. "Automation that understands your business"

### Brand Values
- **Simple** - Clean, no bloat, gets out of your way
- **Intelligent** - AI-powered, learns and adapts
- **Local** - Danish-focused, understands local businesses
- **Reliable** - Works in the background, always on

---

## Design System

### Color Palette

```css
/* Primary */
--midnight: #0f172a;      /* Dark blue-black, main text */
--slate: #475569;         /* Secondary text */
--cloud: #f8fafc;         /* Background */
--white: #ffffff;         /* Cards, sections */

/* Accent */
--electric: #3b82f6;      /* Primary blue, CTAs */
--electric-hover: #2563eb; /* Button hover */
--glow: #60a5fa;          /* Subtle highlights */

/* Semantic */
--success: #22c55e;       /* Green for positive */
--warning: #f59e0b;       /* Amber for alerts */
```

### Typography

```css
/* Primary Font */
font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;

/* Headings */
h1: 56px / 700 / -0.02em tracking
h2: 40px / 600 / -0.01em tracking
h3: 24px / 600

/* Body */
body: 18px / 400 / 1.7 line-height
small: 14px / 400
```

### Layout Principles

1. **Max-width:** 1200px container, centered
2. **Spacing:** 8px base unit (8, 16, 24, 32, 48, 64, 96, 128)
3. **Sections:** Full-width backgrounds, contained content
4. **Mobile-first:** Stack vertically on mobile, side-by-side on desktop
5. **White space:** Generous padding (96px+ between sections)

---

## Page Structure

### Single Page Layout

```
┌─────────────────────────────────────────────────────────┐
│                        NAVIGATION                        │
│  [Logo: ORDOMATION]                    [EN/DA] [GitHub]  │
├─────────────────────────────────────────────────────────┤
│                                                          │
│                         HERO                             │
│                                                          │
│     "Automation that understands                         │
│         your business"                                   │
│                                                          │
│     Intelligent document processing                      │
│     and bookkeeping automation for                       │
│     Danish small businesses                              │
│                                                          │
│     [Learn More ↓]   [View on GitHub →]                 │
│                                                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│                     WHAT WE DO                           │
│                                                          │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐       │
│  │    📧       │ │    🤖       │ │    📊       │       │
│  │   Email     │ │    AI       │ │   Book-     │       │
│  │  Capture    │ │ Classify    │ │  keeping    │       │
│  └─────────────┘ └─────────────┘ └─────────────┘       │
│                                                          │
│  From inbox → to organized archive → ready for          │
│  your accountant, automatically.                        │
│                                                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│                    CURRENT PROJECT                       │
│              (The Email Library System)                  │
│                                                          │
│  Building an intelligent email archival and              │
│  classification system that:                             │
│                                                          │
│  • Monitors multiple email accounts                      │
│  • Extracts and classifies invoices automatically        │
│  • Organizes files by date, sender, and type            │
│  • Prepares data for e-conomic/Dinero integration       │
│  • Maintains full SKAT compliance                        │
│                                                          │
│  Tech: n8n • PostgreSQL • Groq AI • TrueNAS             │
│                                                          │
│  [View Architecture →]                                   │
│                                                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│                       WHO WE ARE                         │
│                                                          │
│  ┌──────────────────┐  ┌──────────────────┐            │
│  │   [Photo]        │  │   [Photo]        │            │
│  │                  │  │                  │            │
│  │ Thue Tønnesen    │  │ Joachim Gensmann │            │
│  │                  │  │                  │            │
│  │ Server admin &   │  │ [TBD based on    │            │
│  │ automation       │  │  LinkedIn info]  │            │
│  │ architect        │  │                  │            │
│  │                  │  │                  │            │
│  │ [LinkedIn] [GH]  │  │ [LinkedIn] [GH]  │            │
│  └──────────────────┘  └──────────────────┘            │
│                                                          │
│  We met at HTX Haderslev and have been building         │
│  projects together ever since. From hardware            │
│  hacks to full-stack automation systems.                │
│                                                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│                    OPEN SOURCE                           │
│                                                          │
│  Everything we build is open. Check out our             │
│  repositories:                                           │
│                                                          │
│  • ordomation/email-library - Email archival system     │
│  • ordomation/n8n-templates - Workflow templates        │
│  • ordomation/docs - Documentation                       │
│                                                          │
│  [View All Repos →]                                      │
│                                                          │
├─────────────────────────────────────────────────────────┤
│                                                          │
│                       FOOTER                             │
│                                                          │
│  ORDOMATION                       Contact                │
│  Bringing order to business       hello@ordomation.com   │
│                                                          │
│  [GitHub] [LinkedIn]              Denmark 🇩🇰            │
│                                                          │
│  © 2026 Ordomation                                       │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

---

## Section Details

### 1. Navigation (Sticky)
- Logo on left (text-based: "ORDOMATION" in Inter 700)
- Right side: Language toggle (EN/DA), GitHub icon link
- Transparent on hero, white with shadow when scrolled
- Height: 64px

### 2. Hero Section
- Full viewport height (100vh)
- Centered text alignment
- Subtle gradient background: white → cloud (#f8fafc)
- Main headline: 56px, midnight color
- Subheadline: 20px, slate color, max-width 600px
- Two CTAs: Primary (filled blue), Secondary (outlined)
- Optional: Subtle animated grid or dots pattern in background

### 3. What We Do
- Three feature cards in a row
- Each card: Icon (emoji or simple SVG), title, brief description
- Clean white cards with subtle shadow
- Cards animate in on scroll (fade up)

### 4. Current Project
- Left: Project description text
- Right: Simplified architecture diagram or screenshot
- Dark section (midnight background, white text) for contrast
- Tech stack badges at bottom

### 5. Who We Are
- Two founder cards side by side
- Circular or rounded-square photos (placeholder if none available)
- Name, role, brief bio (2-3 lines)
- Social links (LinkedIn, GitHub)
- Below cards: shared backstory paragraph

### 6. Open Source
- Simple list or cards for repositories
- Each repo: icon, name, description, stars (if pulling from GitHub API)
- Link to GitHub organization

### 7. Footer
- Two columns on desktop, stacked on mobile
- Left: Logo, tagline
- Right: Contact email, location
- Social links
- Copyright

---

## Technical Implementation

### Option A: Plain HTML/CSS/JS
```
ordomation.com/
├── index.html
├── css/
│   ├── style.css
│   └── responsive.css
├── js/
│   └── main.js
├── assets/
│   ├── images/
│   │   ├── thue.jpg
│   │   ├── joachim.jpg
│   │   └── og-image.png
│   └── icons/
│       └── favicon.ico
├── CNAME
└── README.md
```

### Option B: Astro (Recommended)
```
ordomation.com/
├── src/
│   ├── layouts/
│   │   └── Layout.astro
│   ├── components/
│   │   ├── Nav.astro
│   │   ├── Hero.astro
│   │   ├── Features.astro
│   │   ├── Project.astro
│   │   ├── Team.astro
│   │   ├── OpenSource.astro
│   │   └── Footer.astro
│   ├── pages/
│   │   └── index.astro
│   └── styles/
│       └── global.css
├── public/
│   ├── images/
│   ├── favicon.ico
│   └── CNAME
├── astro.config.mjs
├── package.json
└── README.md
```

### GitHub Pages Setup
1. Create organization: `github.com/ordomation`
2. Create repo: `ordomation.github.io` (for the website)
3. Enable GitHub Pages in repo settings
4. Add CNAME file with `ordomation.com`
5. Configure DNS at domain registrar:
   - A record: 185.199.108.153 (GitHub Pages)
   - A record: 185.199.109.153
   - A record: 185.199.110.153
   - A record: 185.199.111.153
   - CNAME: www → ordomation.github.io

---

## Content Draft

### Hero
**Headline:** Automation that understands your business

**Subhead:** Intelligent document processing and bookkeeping automation for Danish small businesses. From inbox to organized archive, automatically.

### What We Do
**Card 1 - Email Capture**
Monitor multiple email accounts. Extract attachments automatically. No more manual downloading.

**Card 2 - AI Classification**
Our AI reads invoices like a human. Identifies suppliers, amounts, dates. Learns your business patterns.

**Card 3 - Bookkeeping Ready**
Files organized by quarter, numbered sequentially, ready for e-conomic or Dinero. SKAT compliant from day one.

### Current Project
**Title:** The Email Library

**Description:** We're building an open-source email archival and classification system designed for Danish small businesses. It monitors Gmail accounts, extracts invoices and receipts, classifies them using AI, and organizes them into a structured archive ready for your accountant.

**Tech Stack:** n8n (workflow automation), PostgreSQL (metadata), Groq LLaMA 3.3 70B (classification), TrueNAS (storage)

### Team Bios

**Thue Tønnesen**
Server admin and automation architect. Builds the infrastructure that keeps everything running. Passionate about TrueNAS, Kubernetes, and making complex systems simple.

**Joachim Gensmann**
[TBD - need LinkedIn info or user input]

**Shared Story:**
We met at HTX Haderslev, where our shared love for building things brought us together. From hardware projects to software systems, we've been collaborating on ideas ever since. Ordomation is where we bring automation to small businesses that deserve the same tools as the big players.

### Open Source
We believe in building in the open. Our tools are free to use, modify, and contribute to.

---

## Inspiration Sources

Referenced design patterns from:
- [Stripe](https://stripe.com) - Clean fintech aesthetic
- [Retool](https://retool.com) - Developer-focused clarity
- [Linear](https://linear.app) - Minimal dark sections
- [Vercel](https://vercel.com) - Modern, fast, focused

Design research from:
- [Best Landing Page Examples 2025](https://www.orizon.co/blog/our-10-favourite-landing-page-designs-in-fall-2025-and-why-they-convert)
- [Startup Landing Page Examples](https://landingi.com/blog/startup-landing-page-examples/)

---

## Next Steps

1. ✅ Website plan created (this document)
2. ⬜ Create folder structure in Ai_Auto
3. ⬜ Create GitHub organization (ordomation)
4. ⬜ Create website repository
5. ⬜ Create GEMINI_TASK.md for implementation
6. ⬜ Get founder photos
7. ⬜ Complete Joachim's bio
8. ⬜ Build and deploy
