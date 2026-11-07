# Category Spec: Personal Portfolios, Interactive Resumes & Creator Sites (`portfolios-and-personal-sites.md`)

> **Scope:** Developer portfolios, designer personal sites, interactive resumes, founder profiles, and personal landing pages with embedded AI Q&A widgets.

---

## 1. Master Layout Architecture

Modern personal portfolios demand seamless **Light and Dark mode parity** with crisp typographic contrast, clean skill cards, timeline markers, and interactive inquiry widgets:

```text
+----------------------------------------------------------------------------------------------------+
| Portfolio.                                            [ Projects ] [ About ] [ Resume ] [ Contact ]|
+----------------------------------------------------------------------------------------------------+
| HERO SECTION:                                                                                      |
|                                                                    +--------------------+          |
| Hello, I am                                                        |                    |          |
| Waqar Ahmad.                                                       |  (Circular Photo   |          |
|                                                                    |   Portrait Avatar) |          |
| "A versatile IT & Design professional passionate about crafting    |                    |          |
|  high-performance digital experiences and scalable interfaces."   +--------------------+          |
|                                                                                                    |
| [ Get in touch (Solid) ]   [ View projects → (Outline) ]                                           |
+----------------------------------------------------------------------------------------------------+
| CORE SKILLS (3-Card Bento Grid):                                                                   |
| +-----------------------------+ +-----------------------------+ +--------------------------------+ |
| | 🎨 Graphics & UI Design     | | 🎬 Motion & Video Editing   | | 💻 IT & Systems Architecture   | |
| | Visual design, design tokens| | Frame-accurate editing,     | | Workflow automation, security, | |
| | vector systems, brand kits  | | audio enhancement, motion   | | server setup, API integrations | |
| +-----------------------------+ +-----------------------------+ +--------------------------------+ |
+----------------------------------------------------------------------------------------------------+
| INTERACTIVE AI INQUIRY BAR (Modern Engagement Widget):                                             |
|                                                                                                    |
|                             Curious about my background?                                           |
|                           "Ask any question directly below."                                       |
|                                                                                                    |
|     +----------------------------------------------------------------------------------------+     |
|     | 🔍 Ask me anything... e.g. "What tech stack did you use for the fintech project?"      |     |
|     +----------------------------------------------------------------------------------------+     |
|             Prompt hint: "Try asking about my experience with React, Tailwind, or Next.js"          |
+----------------------------------------------------------------------------------------------------+
| SUMMARY & SKILL TAG CLOUD:                                                                         |
| Summary: Narrative bio detailing communication, delivery record, and cross-functional leadership.   |
|                                                                                                    |
| Skill Tags:                                                                                        |
| [ UI/UX ] [ React ] [ TypeScript ] [ Tailwind CSS ] [ Figma ] [ System Architecture ] [ Git ]      |
+----------------------------------------------------------------------------------------------------+
| TIMELINE GRID (2-Column Experience & Education):                                                   |
| Work Experience                                    Education                                       |
| • 2024 — Present                                   • 2020 — 2024                                   |
|   Senior Frontend Engineer \| Tech Corp              BS Computer Science \| University             |
| • 2022 — 2024                                      • 2018 — 2020                                   |
|   UI Designer & Developer \| Studio Zero             Intermediate in Computer Science              |
+----------------------------------------------------------------------------------------------------+
| "LET'S CONNECT" FOOTER:                                                                            |
| "Available for new opportunities and contracts. Reach out through any channel below."              |
|                                                                                                    |
| [ 💬 WhatsApp ]       [ 📞 Phone ]       [ ✉️ Email ]       [ 💼 LinkedIn ]       [ 🐙 GitHub ]     |
+----------------------------------------------------------------------------------------------------+
```

---

## 2. Key Component Blueprints

### A. The Hero Portrait & Dual CTA
* **Circular Avatar:** High-resolution portrait wrapped in a circular crop (`w-36 h-36 sm:w-44 sm:h-44 rounded-full object-cover ring-4 ring-zinc-100 dark:ring-zinc-800 shadow-2xl`).
* **Name & Title Contrast:**
  * Greeting: Muted headline (`text-zinc-500 dark:text-zinc-400 font-medium text-lg`).
  * Big Name: High-contrast primary bold title (`text-4xl sm:text-5xl font-bold tracking-tight text-zinc-900 dark:text-zinc-50`).
* **Dual Action Buttons:**
  * Primary: High-contrast solid pill (`bg-zinc-900 text-white dark:bg-white dark:text-zinc-900 rounded-full px-6 py-2.5 font-medium hover:opacity-90 active:scale-95`).
  * Secondary: Subtle outline pill with arrow (`border border-zinc-300 dark:border-zinc-700 hover:bg-zinc-100 dark:hover:bg-zinc-800 text-zinc-800 dark:text-zinc-200 rounded-full px-6 py-2.5 font-medium`).

### B. Core Skills Cards
* 3-column responsive grid (`grid grid-cols-1 md:grid-cols-3 gap-6`).
* Card background: Elevated surface with subtle border (`bg-zinc-50 dark:bg-zinc-900/60 border border-zinc-200/80 dark:border-zinc-800 rounded-2xl p-6`).
* Icon pill: Pastel tinted background square (`w-10 h-10 rounded-xl flex items-center justify-center bg-blue-500/10 text-blue-600 dark:text-blue-400`).

### C. The Embedded AI Background Inquiry Bar
A cutting-edge differentiator for modern portfolios:
* Central container (`max-w-xl mx-auto text-center my-12`).
* Title: *"Curious about my background?"* with subtext *"Ask any question directly below."*
* Input box: Rounded pill container (`rounded-full py-3.5 px-6 border border-zinc-200 dark:border-zinc-800 bg-white dark:bg-zinc-900 shadow-sm focus-within:ring-2 focus-within:ring-blue-500`).
* Muted suggestions below: Micro-text with clickable starter prompts.

### D. Chronological Timeline Markers
* 2-column layout: Experience on left, Education on right.
* Timeline entries:
  * Indicator: Subtle bullet or pill marker (`w-2 h-2 rounded-full bg-zinc-900 dark:bg-zinc-100 mt-2`).
  * Timestamp: Monospace or muted small label (`text-xs font-mono text-zinc-500`).
  * Role & Company: Semibold headline + light location subtext.

### E. Social Connect Floating Bar
* Direct contact pills grouped in the footer:
  * Individual cards/buttons with brand icon + label (`[ WhatsApp ]`, `[ Phone ]`, `[ Email ]`, `[ LinkedIn ]`).
  * Rounded cards with 1px border (`hover:border-zinc-400 dark:hover:border-zinc-600 hover:-translate-y-0.5 transition-all`).

---

## 3. Light and Dark Theme Parity Tokens

| Element | Light Mode Token | Dark Mode Token |
| :--- | :--- | :--- |
| **Page Canvas** | `#FFFFFF` (Pure white) | `#000000` / `#09090B` (Pitch black) |
| **Card Surface** | `#F8FAFC` (Slate-50) | `#141416` (Deep charcoal) |
| **1px Dividers** | `#E2E8F0` (Slate-200) | `#222326` (Zinc-800) |
| **Primary Text** | `#09090B` (Zinc-950) | `#FAFAFA` (Zinc-50) |
| **Subtext / Bio** | `#52525B` (Zinc-600) | `#A1A1AA` (Zinc-400) |
| **Contact Pills**| White card + shadow | Charcoal card + 1px border |
