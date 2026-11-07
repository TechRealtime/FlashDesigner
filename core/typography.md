# Core Foundation: Typography Hygiene (`typography.md`)

> **Objective:** Establish clean, legible, human-grade typography without screaming all-caps or excessive font weights.

---

## 1. Approved Font Stacks

| Hierarchy Level | Recommended Fonts | CSS Font-Family Stack |
| :--- | :--- | :--- |
| **Default UI Sans** | **Inter** / **SF Pro** | `'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif` |
| **Editorial & Clean** | **Google Sans** / **Open Sans** | `'Google Sans', 'Open Sans', system-ui, sans-serif` |
| **Code & Monospace** | **JetBrains Mono** / **Geist Mono** | `'JetBrains Mono', 'Fira Code', 'Courier New', monospace` |

---

## 2. Weight Discipline (No Hyper-Bold Fonts)

* ❌ **Banned:** `font-black` (900) and pervasive `font-extrabold` (800). Heavy weights create visual mud and overwhelm the eye.
* ✅ **Approved Scale:**
  * **Hero & Page Titles:** `font-semibold` (600) or `font-bold` (700).
  * **Card Headings & Section Titles:** `font-semibold` (600).
  * **Interactive Labels & Badges:** `font-medium` (500).
  * **Body Text & Paragraphs:** `font-normal` (400).

---

## 3. Casing & Text Rules

### The "No Screaming" Rule
* ❌ **Never** write card headings, page titles, or modal titles in all uppercase:
  * Bad: `CREATE NEW WORKSPACE FOR YOUR TEAM`
* ✅ **Always** use Sentence Case or Title Case:
  * Good (Sentence Case): `Create new workspace for your team`
  * Good (Title Case): `Create New Workspace for Your Team`

### When to Use Uppercase
Uppercase is permitted **only** for micro-metadata tags (e.g. status badges, table column headers, or breadcrumbs) and **must** be combined with small font sizes and wide letter spacing:
```html
<!-- Allowed uppercase exception: Table column headers -->
<span class="text-xs font-semibold tracking-wider uppercase text-zinc-500">
  Status
</span>
```

---

## 4. Vertical Rhythm & Line Height
* Long paragraphs: Always specify comfortable reading line-height (`leading-relaxed` or `line-height: 1.625`).
* Short titles: Keep line-height tight to prevent awkward vertical gaps (`leading-tight` or `line-height: 1.25`).
