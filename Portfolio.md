# 🧠 AI Engineer Portfolio — World-Class UI Build Prompt

> **Category:** UI/UX Design → Lovable / v0 / Cursor  
> **Difficulty:** `Expert`  
> **Tested On:** Claude Sonnet, GPT-4o, v0.dev, Lovable.dev  
> **Stack:** React · Tailwind CSS · Framer Motion · TypeScript

---

## 🎯 Prompt

```
ROLE:
You are a senior full-stack engineer and creative director specializing in award-winning portfolio sites for AI/ML professionals. You have deep expertise in React, TypeScript, Tailwind CSS, and Framer Motion. Your output is always pixel-perfect, production-ready, and deployable to Vercel with zero modifications.

CONTEXT:
I am an AI Engineer who works with LLMs, Computer Vision, and Neural Network architectures. I want a portfolio that communicates elite technical depth AND strong design sensibility — the kind of site that makes a hiring manager stop scrolling. The aesthetic is "Deep Tech Futurism": dark, sophisticated, precise, with just enough motion to feel alive without being distracting.

TASK:
Build a complete, single-file React + TypeScript + Tailwind CSS + Framer Motion portfolio. Every section below must be fully implemented — no placeholders, no TODOs, no "you can add X here" comments. Deliver working code only.

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎨 1. VISUAL IDENTITY SYSTEM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

COLOR TOKENS (define as Tailwind config extensions):
  Background:   #050505 (true black), #0D0D0D (surface), #111318 (card)
  Accent 1:     #00D2FF (electric cyan)  — primary actions, glow, highlights
  Accent 2:     #7C3AED (soft violet)    — secondary tags, gradients, borders
  Accent 3:     #FFD700 (gold)           — star ratings, featured badges only
  Text:         #F0F0F0 (primary), #9CA3AF (muted), #6B7280 (ghost)
  Border:       rgba(255,255,255,0.06) default, rgba(0,210,255,0.3) on hover

TYPOGRAPHY:
  Display:  "Space Grotesk" (700) — headlines only
  Body:     "Inter" (400/500)
  Mono:     "JetBrains Mono" — code snippets, tech tags, terminal elements
  Scale:    Hero 72px → Section titles 42px → Card titles 20px → Body 16px

BACKGROUND LAYER:
  Implement an interactive particle/neural-network canvas using Framer Motion or a lightweight custom canvas hook.
  - Particles: ~80 dots, 1-2px radius, #00D2FF at 15% opacity
  - Lines drawn between particles within 120px proximity, fading by distance
  - Particles drift slowly (0.3px/frame), mouse proximity creates gentle attraction
  - Render on a <canvas> positioned fixed behind all content, z-index: 0
  - Must not degrade performance — use requestAnimationFrame with cleanup

EFFECTS:
  Glassmorphism cards:
    background: rgba(255,255,255,0.03)
    border: 1px solid rgba(255,255,255,0.06)
    backdrop-filter: blur(12px)
    border-radius: 16px
  
  Glow shimmer on hover:
    box-shadow: 0 0 0 1px rgba(0,210,255,0.4), 0 0 24px rgba(0,210,255,0.12)
    Animate with a travelling gradient shimmer across the border (keyframe animation)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📐 2. LAYOUT & SECTIONS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

── STICKY HEADER ──
  - Glassmorphism bar: backdrop-blur-md, bg-black/30, border-b border-white/5
  - Logo: "[YOUR_NAME]" in Space Grotesk 700, cyan gradient text
  - Nav links: Home · About · Projects · Experience · Contact
    Each link has an underline that slides in from left on hover (CSS transform scaleX)
  - "Download Resume" button:
      • Gradient border (cyan → violet) via a pseudo-element ring
      • Subtle glow pulse animation (2s loop) on idle
      • Ripple effect on click
  - Mobile: hamburger icon (3 stacked bars → X transition), slide-down menu with stagger-in items
  - Scroll behavior: on scroll > 80px, reduce header height from 72px → 56px with transition

── HERO SECTION ──
  - Full viewport height (100vh), vertically + horizontally centered
  - Above the headline: a monospaced tag line that types in:
      > "AI Engineer · Builder · Researcher"
    Typewriter speed: 60ms/char, cursor blinks 3x then disappears
  - Main headline (2 lines):
      Line 1: "Architecting the Future"  (white)
      Line 2: "with Generative Intelligence."  (cyan→violet gradient)
    Animate: each word fades + slides up with 60ms stagger between words
  - Sub-headline (below, muted):
      "I design and deploy production AI systems — from LLM fine-tuning to real-time computer vision pipelines."
    Delay 0.8s, fade in + subtle upward slide
  - Primary CTA: "Explore My Projects →"
      • Magnetic button: mouse proximity warps button position slightly (±8px) using Framer Motion useMotionValue
      • On click: smooth scroll to #projects
      • Background: linear-gradient(135deg, #00D2FF, #7C3AED)
      • Hover: scale(1.04), brightness(1.1)
  - Secondary CTA (ghost): "View My Resume" — outline variant, same hover rules
  - Bottom: animated scroll indicator (chevron bouncing gently, fades out on scroll)

── ABOUT SECTION ──
  - Two-column layout (60/40 split on desktop, stacked on mobile)
  - Left: 3–4 paragraph bio. Include [PLACEHOLDER: YOUR_BIO_TEXT]
  - Right: a terminal-style card with blinking cursor:
      Black card, monospaced font, green-ish (#00FF7F) text
      Show fake terminal output: skills, years of experience, specializations
      Example:
        $ whoami
        > AI Engineer @ [COMPANY]
        $ skills --list
        > LLMs · RAG · Computer Vision · MLOps · NLP
        $ experience --years
        > 5+ years in production AI
  - Animate: left side slides from left, right side slides from right, triggered on scroll entry

── TECH STACK SECTION ──
  - Section title: "Weapons of Choice"
  - Two rows of infinite marquee (one scrolls left, one scrolls right, opposite speeds)
  - Each item: logo icon + label, inside a glass pill with 1px border
  - Technologies: Python · PyTorch · TensorFlow · LangChain · OpenAI API · HuggingFace · FastAPI · Docker · Kubernetes · PostgreSQL · Redis · React · TypeScript · AWS · GCP
  - Marquee speed: 40s per loop. Pauses on hover. Clones items for seamless loop.
  - Above the marquee: 4 metric cards in a row (glass style):
      [PLACEHOLDER: 20+] Models Deployed
      [PLACEHOLDER: 50M+] Inferences / Month
      [PLACEHOLDER: 15+] Open Source Contributions
      [PLACEHOLDER: 5+] Years Experience
    Each number animates count-up when section scrolls into view

── PROJECTS SECTION ──
  id="projects"
  - Section title: "What I've Built"
  - Bento Grid layout (CSS Grid, not a library):
      Large card: col-span-2 row-span-2 (featured project)
      Medium cards: col-span-1 row-span-2
      Small cards: col-span-1 row-span-1
    Grid: 3 columns, auto rows, gap 16px
  - Each project card includes:
      • Thumbnail area: a gradient placeholder or subtle geometric pattern (no external images)
      • "Featured" badge (gold) on the hero card
      • Project title in Space Grotesk 600
      • 2-line description
      • Tech tags: JetBrains Mono, glass pill, cyan text
      • Footer bar: GitHub icon link + "Live Demo" link
      • Hover: card lifts (translateY -4px), glow border activates, inner content shifts slightly
  - Pre-fill with [PLACEHOLDER] projects:
      1. "NeuralChat — RAG-Powered Enterprise LLM" (featured)
      2. "VisionCore — Real-Time Object Detection"
      3. "FinSight — LLM Financial Analysis Tool"
      4. "AutoPipeline — ML Training Orchestration"
      5. "EmbedSearch — Semantic Search Engine"

── EXPERIENCE SECTION ──
  - Vertical timeline: a glowing line down the center (on desktop), left-aligned on mobile
  - Each node: a cyan dot on the line, expanding ring animation on scroll-entry
  - Card slides in from alternating sides (left/right per item)
  - Each entry: Company name · Role · Date range · 3 bullet achievements
  - Pre-fill with [PLACEHOLDER] entries:
      • [COMPANY_1] · Senior AI Engineer · 2023–Present
      • [COMPANY_2] · ML Engineer · 2021–2023
      • [COMPANY_3] · Data Scientist · 2019–2021

── CONTACT SECTION ──
  - Headline: "Let's Build Something Exceptional"
  - Sub: "Available for senior roles, consulting, and research collaborations."
  - Two columns:
      Left: contact form (Name · Email · Message · "Send Message" button)
        Form fields: dark glass style, cyan focus ring (no glow on unfocused)
        Submit button: full-width gradient, shows loading spinner then success checkmark
      Right: direct links
        Email card (mailto link)
        LinkedIn card
        GitHub card
        Each as a glass card with icon + handle + arrow indicator
  - All form input has smooth label-float animation (placeholder floats up on focus)

── FOOTER ──
  - Full-width, border-top: 1px solid rgba(255,255,255,0.05)
  - Left: Logo + tagline "Engineering Intelligence, One Model at a Time."
  - Center: social icons (GitHub · LinkedIn · X/Twitter · Kaggle) — icon buttons with hover glow
  - Right: "Back to Top ↑" button — smooth scroll to top, subtle bounce on hover
  - Bottom bar: "© 2026 [YOUR_NAME] · Built with Precision · Open Source"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎬 3. ANIMATION SYSTEM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Use Framer Motion throughout. Define reusable variants:

  fadeUpVariant:
    hidden: { opacity: 0, y: 32 }
    visible: { opacity: 1, y: 0, transition: { duration: 0.6, ease: [0.25, 0.46, 0.45, 0.94] } }

  staggerContainerVariant:
    visible: { transition: { staggerChildren: 0.08 } }

  cardHoverVariant:
    rest: { scale: 1, y: 0 }
    hover: { scale: 1.02, y: -4, transition: { type: "spring", stiffness: 300, damping: 20 } }

Rules:
  - Every section title uses fadeUpVariant, triggered by useInView (once: true, margin: "-100px")
  - Grid items stagger in using staggerContainerVariant
  - Hover effects: spring physics, NOT easing curves (feels more alive)
  - NO layout shift during animation — reserve space before elements animate in
  - Respect prefers-reduced-motion: wrap all non-essential animations in a check and fall back to opacity-only

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📱 4. RESPONSIVENESS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Breakpoints (Tailwind defaults):
  sm (640px): single-column layout, 16px padding
  md (768px): 2-column for About + Contact
  lg (1024px): full layout, bento grid activates
  xl (1280px): max-width 1200px centered with auto margins

Mobile-specific:
  - Particle canvas density reduced to 40 particles
  - Hamburger nav replaces horizontal links
  - Bento Grid becomes single column (each card full-width)
  - Timeline becomes left-aligned (no alternating)
  - CTA buttons become full-width
  - Font sizes scale: hero 72px → 40px, section titles 42px → 28px

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚙️ 5. TECHNICAL REQUIREMENTS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

- TypeScript strict mode
- Tailwind CSS with a custom theme extension (colors, fonts, keyframes)
- Framer Motion v11+ API (no deprecated APIs)
- All custom hooks in a /hooks directory:
    useMousePosition.ts
    useScrollProgress.ts
    useInViewAnimation.ts
- Zero external UI library dependencies (no shadcn, no MUI, no Chakra)
- Google Fonts loaded via <link> in index.html
- Canvas particle system in a custom hook: useParticleCanvas(canvasRef)
- Accessible: all interactive elements have aria-labels, focus rings, keyboard navigation
- Lighthouse targets: Performance ≥ 90, Accessibility ≥ 95, Best Practices ≥ 95

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📋 6. PLACEHOLDERS TO FILL
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Replace before deploying:

  [YOUR_NAME]           → Your full name
  [YOUR_TITLE]          → e.g. "Senior AI Engineer"
  [YOUR_BIO_TEXT]       → 3–4 paragraph professional bio
  [COMPANY]             → Current employer or "Freelance"
  [COMPANY_1/2/3]       → Past/current companies
  [ROLE_1/2/3]          → Job titles
  [DATE_RANGE_1/2/3]    → e.g. "Jan 2023 – Present"
  [PROJECT_REPO_URL]    → GitHub links
  [PROJECT_LIVE_URL]    → Live demo URLs
  [YOUR_EMAIL]          → Contact email
  [YOUR_LINKEDIN_URL]   → LinkedIn profile URL
  [YOUR_GITHUB_URL]     → GitHub profile URL
  [METRIC_1/2/3/4]      → Stats for the metric cards

CONSTRAINTS:
- Deliver the full implementation in a single App.tsx file (or split into logical component files if needed for clarity)
- No stock image URLs — use gradient placeholders for all visual media
- All animations must be smooth at 60fps on a mid-range mobile device
- Do NOT use any CSS frameworks other than Tailwind
- The site must look complete and professional, not like a starter template

FORMAT:
Output complete, copy-paste ready code. Start with the file structure, then each file in full. After the code, provide a one-paragraph deployment note for Vercel.
```

---

## 📌 Usage Notes

**How to use this prompt:**
1. Copy the entire prompt block above
2. Replace any `[PLACEHOLDER]` values that you already know (e.g. your name, tech stack preferences)
3. Paste into Claude, GPT-4o, or directly into v0.dev / Lovable
4. For best results with Claude: prefix with `"Generate the complete React app."` 
5. For v0.dev: paste directly — it handles multi-file output natively

**Tested outputs include:**
- Fully functional particle canvas background
- Working magnetic button physics
- Smooth bento grid with hover states
- Complete responsive hamburger menu
- All Framer Motion scroll-triggered animations

**Remix ideas:**
- Swap "AI Engineer" → "ML Researcher" or "Data Scientist" for adjacent roles
- Change color tokens to `#FF6B6B` (coral) + `#4ECDC4` (teal) for a warmer palette
- Add a `Blog` section by extending the nav and adding a post-card grid section

---

*Prompt version: 2.0 · Last tested: June 2025 · Category: UI/UX Design*
