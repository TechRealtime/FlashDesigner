# Core Foundation: Dual Theming Engine (`theming.md`)

> **Objective:** Guarantee clean, robust light and dark themes with independent class switching that never flickers or breaks.

---

## 1. Class-Based Architecture (No OS Lock-in)

Do **NOT** rely strictly on `@media (prefers-color-scheme: dark)`. The theme must be controlled via an explicit CSS class on the root element (`<html>` or `<body>`):

```html
<!-- Light Mode -->
<html class="light">

<!-- Dark Mode -->
<html class="dark">
```

### Theme Storage & Hydration
* Persist the choice in `localStorage.getItem('flash-theme')`.
* On first load, check `localStorage`. If absent, gracefully fallback to the user's OS preference (`window.matchMedia('(prefers-color-scheme: dark)').matches`), then set the class immediately to prevent a white-flash flicker.

---

## 2. High-Contrast Semantic Color Tokens

Avoid pure black `#000000` and pure white `#FFFFFF` on every surface, which causes eye strain. Use calibrated zinc/slate tones:

| Token | Light Mode Value | Dark Mode Value | Usage |
| :--- | :--- | :--- | :--- |
| **`bg-canvas`** | `#F8FAFC` (Slate-50) | `#09090B` (Zinc-950) | App background |
| **`bg-surface`** | `#FFFFFF` (White) | `#18181B` (Zinc-900) | Cards, modals, sidebars |
| **`border-subtle`**| `#E2E8F0` (Slate-200) | `#27272A` (Zinc-800) | 1px dividers, card outlines |
| **`text-primary`** | `#0F172A` (Slate-900) | `#F4F4F5` (Zinc-100) | Main titles, primary content |
| **`text-muted`** | `#64748B` (Slate-500) | `#A1A1AA` (Zinc-400) | Subtitles, meta tags, timestamps |
| **`accent-primary`**| `#2563EB` (Blue-600) | `#3B82F6` (Blue-500) | Primary CTA buttons, focus rings |

---

## 3. Theme Toggle Control
The theme switch should be placed accessibly in the top navigation bar.
* **Icon Feedback:** Shows Sun (`☀️`) in dark mode (indicating "Switch to Light") and Moon (`🌙`) in light mode (indicating "Switch to Dark").
* **Animation:** Smooth 90-degree rotational spin on click (`transition-transform duration-300 transform active:rotate-90`).
