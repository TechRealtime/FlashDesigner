# Core Foundation: Multi-Screen Responsiveness (`responsiveness.md`)

> **Objective:** Ensure zero layout breaking, no awkward button text wraps, and seamless scaling across all screen sizes and aspect ratios.

---

## 1. Breakpoint Reference Standards

| Breakpoint | Minimum Width | Target Devices | Layout Behavior |
| :--- | :--- | :--- | :--- |
| **`xs` / Mobile** | `320px – 639px` | Smart phones (iPhone SE, Pro Max, Galaxy) | Single column, full-width actions, hidden sidebars |
| **`sm` / `md` Tablet**| `640px – 1023px`| iPads, tablets, foldable devices | 2-column grids, collapsed icon navigation |
| **`lg` / Laptop** | `1024px – 1439px`| Standard laptops, MacBook Air | Multi-column layouts, expanded sidebars |
| **`xl` / `2xl` Wide**| `1440px – 2560px`| External monitors, 4K displays | Centered bounded container (`max-w-7xl` or `max-w-screen-2xl`) |

---

## 2. Preventing Button & Card Line Breaks

### The Problem
On narrow or mobile screens, poorly styled buttons often wrap text onto two lines (e.g., "Add to\nCart"), making the UI look broken and amateurish.

### The FlashDesigner Fix
1. **Never Allow Unintended Button Wrapping:**
   * Always apply `whitespace-nowrap` to button action labels.
   * Pair with `shrink-0` so flex containers do not crush the button width.
   ```html
   <!-- Correct Button Pattern -->
   <button class="inline-flex items-center justify-center whitespace-nowrap shrink-0 px-4 py-2 rounded-lg font-medium text-sm transition-colors">
     Save Changes
   </button>
   ```

2. **Flex Action Toolbars:**
   * Group toolbars using `flex flex-wrap items-center gap-2` or let buttons scroll horizontally with a subtle scroll indicator (`overflow-x-auto no-scrollbar`).

3. **Card Content Truncation:**
   * For titles inside cards, use single-line ellipsis (`truncate`) or a strict 2-line clamp (`line-clamp-2`). Never allow titles to unpredictably push card heights out of alignment.

---

## 3. Container & Viewport Hygiene
* **No Accidental Horizontal Scrollbars:**
  * Root wrapper should protect against overflow: `overflow-x-hidden w-full min-h-screen`.
* **Mobile-First Padding:**
  * Use responsive padding tokens: `px-4 sm:px-6 lg:px-8`.
  * Never use hardcoded pixel widths (`width: 500px`). Always use fluid or percentage-based widths with max bounds (`w-full max-w-lg`).
