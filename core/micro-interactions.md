# Core Foundation: Micro-Interactions & Action Feedback (`micro-interactions.md`)

> **Objective:** Ensure every user action provides instantaneous visual confirmation with smooth, iOS-grade physics.

---

## 1. Action Acknowledgments (The "Never Wonder" Rule)

Every interactive button that triggers a mutation, copy, or save must visually acknowledge the user's click.

### The "Copy to Clipboard" Pattern
When a user clicks any copy button or copy icon:
1. **Instant Icon Swap:** The copy icon morphs into a green checkmark (`✓`).
2. **Text Swap:** The text temporarily changes from `"Copy"` to `"Copied!"`.
3. **Timer Reset:** After `2000ms`, cleanly transition back to the default state.

```tsx
// React / UI Reference Implementation:
function CopyButton({ textToCopy }: { textToCopy: string }) {
  const [copied, setCopied] = useState(false);

  const handleCopy = async () => {
    await navigator.clipboard.writeText(textToCopy);
    setCopied(true);
    setTimeout(() => setCopied(false), 2000);
  };

  return (
    <button
      onClick={handleCopy}
      className="inline-flex items-center gap-1.5 px-3 py-1.5 text-xs font-medium rounded-md transition-all duration-200 bg-zinc-100 hover:bg-zinc-200 dark:bg-zinc-800 dark:hover:bg-zinc-700 text-zinc-800 dark:text-zinc-200 active:scale-95"
    >
      {copied ? (
        <>
          <CheckIcon className="w-3.5 h-3.5 text-emerald-500 transition-transform duration-200 scale-110" />
          <span className="text-emerald-500 font-semibold">Copied!</span>
        </>
      ) : (
        <>
          <ClipboardIcon className="w-3.5 h-3.5 text-zinc-500" />
          <span>Copy</span>
        </>
      )}
    </button>
  );
}
```

---

## 2. iOS-Grade Physics & Motion Curves

* **The Spring Feel (Active Press):**
  * When a user taps or clicks a button, apply a subtle downward scale: `active:scale-[0.98]` or `active:scale-95`.
* **Timing & Curves:**
  * Default transition: `transition-all duration-150 ease-out` (Fast entrance).
  * Modal/Drawer opening: `transition-transform duration-300 cubic-bezier(0.16, 1, 0.3, 1)` (Apple standard spring).
  * ❌ **Never** use slow linear transitions (`transition-all duration-500 linear`), which feel sluggish and laggy.

---

## 3. Top-Side Toast Notifications
For major events (e.g., "Settings updated", "Project deleted", "Link shared"):
* **Position:** Floating top-right on desktop, top-center on mobile devices.
* **Appearance:** Dark glassmorphism pill (`bg-zinc-900/90 text-white backdrop-blur-md shadow-xl border border-zinc-800 rounded-xl px-4 py-3`).
* **Auto-Dismiss:** Dismiss automatically after 3.5 seconds with an optional manual close (`✕`) button.
