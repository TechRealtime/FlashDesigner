# Pattern Blueprint: Loading States & Skeletons (`loading-and-skeletons.md`)

> **Objective:** Maintain structural layout stability during data loading and avoid empty screen flash.

---

## 1. When to Use Skeletons vs. Spinners

| UI Scenario | Recommended Loading Pattern | Reason |
| :--- | :--- | :--- |
| **Initial Page Load / Data Fetching** | **Skeleton Screens** | Preserves layout shape, reduces perceived load time, prevents layout shift. |
| **Inline Button Action** (e.g. "Saving...") | **Circular Spinner** inside button | Keeps the user in context without replacing the entire component. |
| **File / Media Upload** | **Determinate Progress Bar (%)** | Provides concrete feedback on network progress. |
| **Streaming Text Generation** | **Tail Shimmer Cursor** | Shows active LLM token arrival. |

---

## 2. Skeleton Screen Best Practices

* **Mirror the Real Component:**
  * Use a circle for avatars: `w-10 h-10 rounded-full bg-zinc-200 dark:bg-zinc-800 animate-pulse`.
  * Use rounded bars for text lines: `h-4 w-3/4 rounded bg-zinc-200 dark:bg-zinc-800 animate-pulse`.
  * Use large rectangles for charts or cards: `h-48 w-full rounded-xl bg-zinc-200 dark:bg-zinc-800 animate-pulse`.
* **Shimmer Pulse Speed:**
  * Keep the pulse animation smooth and subtle (`duration-1000` or `duration-1500`).
  * Avoid rapid flashing or high-contrast strobe effects.

---

## 3. Circular Button Spinner Pattern

When an action is actively submitting:
```html
<button disabled class="inline-flex items-center justify-center gap-2 px-4 py-2 rounded-lg bg-blue-600 text-white opacity-80 cursor-not-allowed">
  <!-- Subtle circular spinner -->
  <svg class="animate-spin h-4 w-4 text-white" viewBox="0 0 24 24" fill="none">
    <circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
    <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8v4a4 4 0 00-4 4H4z"></path>
  </svg>
  <span>Saving...</span>
</button>
```
