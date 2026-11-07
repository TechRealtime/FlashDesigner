# FlashDesigner: Core Design Constitution (`RULES.md`)

> **MANDATORY DIRECTIVE FOR ALL AI AGENTS & LLMS:**
> Before writing any UI, HTML, CSS, React, or frontend code, you **MUST** read and adhere strictly to these rules. Any UI produced must comply with these standards.

---

## 🏛️ Rule 1: The AI Execution Protocol
Before generating any frontend code, you must output a concise 3-step **UI Execution Plan**:
1. **Target Category:** Identify which category from `INDEX.md` you matched (e.g., `categories/llm-chat-and-dashboards.md`).
2. **Design Tokens:** Define the primary palette (Light & Dark hex/tailwind values), typography stack, and spacing baseline.
3. **Responsive Blueprint:** State how the layout adapts between Mobile (< 640px), Tablet (640px–1024px), and Desktop (> 1024px).

---

## 🚫 Rule 2: Strictly Banned "AI Slop" Tropes
Unless explicitly requested by the user, **NEVER** use the following low-quality AI tropes:
* ❌ **No AI Sparkle Stars:** Do not slap sparkling star icons (`✨`, `Sparkles`, Gemini-style multi-point stars) on every header, card, or button.
* ❌ **No Tacky Pulse Animations:** Ban continuous glowing/pulsing borders, rainbow gradient animations, or "dancing" pulsing buttons.
* ❌ **No Oversaturated Generic Gradients:** Ban arbitrary blue-to-purple (`from-blue-600 to-purple-600`) background fills. Use clean, high-depth solid surfaces with subtle 1px border dividers.

---

## 🔤 Rule 3: Typography Hygiene & Font Rules
* **No Screaming All-Caps:** Never render navigation items, headers, or card titles in full uppercase (`"THIS IS A CARD"`). Use **Sentence Case** (`"This is a card"`) or clean **Title Case** (`"This is a Card"`).
* **Controlled Weight:** Never use heavy `font-black` (900) or overused `font-extrabold` (800). Cap titles at `font-semibold` (600) and body text at `font-normal` (400) or `font-medium` (500).
* **Approved Font Families:** Default to clean, modern, high-legibility sans-serif stacks:
  * Primary: `Inter`, `Google Sans`, `Open Sans`, or iOS system `-apple-system, BlinkMacSystemFont, "SF Pro Text"`.
  * Fallbacks: Clean system sans (`system-ui, sans-serif`).

---

## 📱 Rule 4: Multi-Screen Responsiveness & Overflow Protection
* **Universal Screen Ratios:** Every layout must adapt gracefully across mobile phones (375px+), tablets, standard laptops (1366px–1440px), and wide monitors (1920px+).
* **No Button/Card Line Breaking:**
  * Button text must never break into an awkward second line on narrow screens. Use `whitespace-nowrap`, flexible minimum widths (`min-w-fit`), and appropriate flex containers (`flex-wrap gap-2`).
  * Card headings and critical badges must never overflow or cause horizontal window scrolling (`overflow-hidden`, `text-ellipsis`).
* **Touch Targets:** On mobile/touch devices, all clickable buttons and icons must maintain a minimum hit-area of at least `44x44px`.

---

## ⚡ Rule 5: Micro-Interactions & Action Acknowledgments
A professional UI **never leaves the user guessing** whether a click was registered.
* **Instant Inline Feedback:** When a user clicks an action like **Copy**, the button must immediately morph:
  * Icon switches from clipboard to checkmark (`✓`).
  * Text changes from `"Copy"` to `"Copied!"` for 2000ms before returning to the default state.
* **Button States:** Every clickable element must have distinct, defined:
  1. Default state
  2. Hover state (`hover:bg-opacity-90`, subtle elevation)
  3. Active/Pressed state (`scale-[0.98]` or darker shade)
  4. Disabled state (reduced opacity `opacity-50`, `cursor-not-allowed`)
* **iOS-Grade Smooth Transitions:** Use natural cubic-bezier ease transitions (`transition-all duration-200 ease-out` or spring curves). Never use jarring instant color snaps or sluggish > 500ms transitions.
* **Optional Toast Notifications:** Major destructive or async actions (e.g., "File saved", "Profile updated") should trigger a clean, top-right or top-center floating toast alert.

---

## 💀 Rule 6: Loading States & Skeletons
* **Content Areas:** Never leave a screen blank while fetching data. Always display a **Skeleton Loader** that mirrors the shape of the incoming content (avatar circles, text line rectangles, card blocks).
* **Button/Inline Spinners:** Reserve small circular spinners strictly for inline button actions (e.g., inside a "Submitting..." button).
* **Subtle Pulse:** Skeleton loaders must use a soft, muted gray shimmer pulse (`animate-pulse`), not bright or rapid strobing.

---

## 🌓 Rule 7: Independent Dual Theming (Light & Dark)
* **Explicit Class-Based Theming:** Theme switching must rely on explicit root classes (e.g., `<html class="dark">` or `data-theme="dark"`), **never** solely on OS media queries.
* **Reliable Toggle:** Provide an accessible frontend toggle switch (Sun/Moon icon) that smoothly toggles between modes without breaking layout or un-styling components.
* **Contrast Compliance:** Ensure WCAG AA contrast standards. Text on dark mode must never be harsh pure white (`#FFFFFF`) on pure black (`#000000`). Use zinc/slate surfaces (e.g., `#09090B` surface with `#FAFAFA` text and `#71717A` muted labels).

---

## 💬 Rule 8: LLM & Chat Dashboard Standards
When developing chat interfaces, AI workbenches, or prompt dashboards:
1. **The Send Button:** Use a modern, circular **upward arrow (`↑`)** icon (iOS/modern chat style). Do **NOT** use outdated diagonal paper airplanes.
2. **Full Markdown Support:** The interface must natively format all LLM responses:
   - Fenced code blocks with syntax highlighting, language badges, and one-click "Copy Code" buttons.
   - Clean tables, nested ordered/unordered lists, blockquotes, and KaTeX math formulas.
3. **Smooth Streaming Animations:** Text generation must render with a soft shimmering cursor or smooth fluid typewriter stream—no erratic jumping or layout shifts.
4. **Smart Sticky Auto-Scroll:**
   - Automatically stick and scroll to the bottom while the AI is streaming output.
   - **Crucial:** If the user manually scrolls up to read past history, **IMMEDIATELY pause auto-scrolling**. Do not yank the user's screen down.
   - Surface a floating *"Scroll to bottom ↓"* pill when the user is scrolled up during generation.

---

## 📸 Rule 9: Visual Verification & Self-Audit
After generating any UI:
1. Review code against the mobile breakpoint (< 640px) to verify no text clipping or button squishing.
2. If running in an agentic IDE with screenshot/browser capabilities, inspect the rendered UI visual snapshot to verify vertical alignment and visual balance before presenting it to the user.
