# Pattern Blueprint: Buttons & Action Ergonomics (`buttons-and-actions.md`)

> **Objective:** Define button hierarchies, touch targets, state indicators, and inline acknowledgments.

---

## 1. Button Hierarchy Scale

| Variant | Visual Style | Use Case |
| :--- | :--- | :--- |
| **Primary** | Solid accent fill (`bg-blue-600 text-white hover:bg-blue-500 shadow-sm`) | The single main action per screen (e.g., "Deploy App", "Send Message") |
| **Secondary** | Subtle surface (`bg-zinc-100 hover:bg-zinc-200 dark:bg-zinc-800 dark:hover:bg-zinc-700 text-zinc-900 dark:text-zinc-100`) | Supporting actions (e.g., "Cancel", "Filter", "Export") |
| **Outline** | 1px border (`border border-zinc-300 dark:border-zinc-700 hover:bg-zinc-50 dark:hover:bg-zinc-800/50`) | Alternative secondary options |
| **Ghost / Icon** | Transparent background (`hover:bg-zinc-100 dark:hover:bg-zinc-800 text-zinc-600 dark:text-zinc-400`) | Icon buttons in toolbars (e.g., theme toggle, info tooltip) |
| **Destructive** | Soft red background (`bg-red-500/10 text-red-600 dark:text-red-400 hover:bg-red-500/20`) | Irreversible actions (e.g., "Delete Project") |

---

## 2. Interactive States Checklist

Every button must specify all 5 states:
1. **Default:** Crisp borders and readable text.
2. **Hover:** Subtle 10% brightness increase or elevation lift.
3. **Active/Tap:** Apple-style scale down (`active:scale-[0.98]`).
4. **Focus-Visible:** Accessible 2px focus ring (`focus-visible:ring-2 focus-visible:ring-blue-500 focus-visible:ring-offset-2`).
5. **Disabled:** Reduced opacity (`opacity-50 cursor-not-allowed pointer-events-none`).

---

## 3. Responsive Safeguards
* Always include `whitespace-nowrap` on text buttons.
* Ensure a minimum touch area of `44x44px` for mobile finger-tapping, even if the visual icon inside is only `18x18px` (use `p-2.5` or `min-w-[44px] min-h-[44px]`).
