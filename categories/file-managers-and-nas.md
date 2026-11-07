# Category Spec: File Managers, Cloud Drives & NAS Interfaces (`file-managers-and-nas.md`)

> **Scope:** Cloud storage drives (Google Drive / Dropbox style), Network Attached Storage (NAS) consoles (Synology / TrueNAS / cPanel File Manager), and Mobile File Explorers.

---

## 1. Universal Layout Archetypes

Based on production-grade designs, file management systems universally split into three layout archetypes:

### Archetype A: Cloud Drive & Collaboration (Desktop 3-Pane)
Best for: Team file sharing, Google Drive / Dropbox alternatives, SaaS asset managers.

```text
+----------------------------------------------------------------------------------------------------+
| [Logo] CloudStorage  [ Search files & folders... ⌘K ]                 [ Go Pro ] [ Share ] [Avatar]|
+-------------------+--------------------------------------------------------------+-----------------+
| Navigation        | My Files > Secret Folder (Breadcrumb)          [+ Upload] [Filter] | File Details    |
| - Home       (10) |--------------------------------------------------------------|                 |
| - Recent          | Recent Files (Horizontal Card Carousel)                      | [ File Icon ]   |
| - Shared with Me  | [ File.pdf ]  [ Image.png ]  [ Folder ]  [ Code.tsx ]        | accounts.txt    |
| - Trash           |--------------------------------------------------------------| Modified: 02/15 |
|                   | Public Files (Data Table)                                    |                 |
| FOLDERS           | [ ] Name            Size     Modified   Permissions  Actions | File Overview   |
| - Work            | [ ] Invoice.doc     44 MB    Yesterday  [View Only]   [...]  | 👁️ 198 Views     |
| - Images          | [✓] ReactApp.tsx    155 KB   Today      [Editor]      [...]  | ✏️ 16 Edits      |
|                   +--------------------------------------------------------------|                 |
| [Storage: 85GB]   | [ ↑ Drag and drop files here to upload (Max 50MB) ]          | [Donut Storage] |
+-------------------+--------------------------------------------------------------+-----------------+
```

### Archetype B: Developer NAS & Web Host File Explorer (Live Split Preview)
Best for: cPanel File Manager, FTP/NAS browsers, Code & Server file navigators.

```text
+----------------------------------------------------------------------------------------------------+
| Top Bar: [Upload ↑]  [+ New Folder]  [Delete 🗑️]  [Download ↓]              [View: List | Grid]    |
+---------------------+---------------------------------------+--------------------------------------+
| Directory Tree      | File List (Multi-Select Table)        | Live Code / Media Preview            |
| v public_html       | [ ] Name        Size     Last Mod     | functions.php (PHP File)    [✕ Close]|
|   > assets          | [ ] wp-content  --       May 10, 2026 | 1  <?php                             |
|   v wp-content      | [ ] index.php   1.2 KB   May 12, 2026 | 2  /**                               |
|     > plugins       | [✓] style.css   3.6 KB   May 12, 2026 | 3   * Theme setup                    |
|     > themes        | [✓] functions   2.8 KB   May 12, 2026 | 4   */                               |
+---------------------+---------------------------------------+--------------------------------------+
```

### Archetype C: Mobile File Manager & Storage Cleaner
Best for: iOS Files / Android Files by Google, mobile storage management.

```text
+-----------------------------------+   +-----------------------------------+
| File Manager        [ 🔍 Search ] |   | ← Internal Storage                |
|                                   |   |                                   |
| +-------------------------------+ |   |           ( 66% )                 |
| | (66%) Internal Storage        | |   |         Used: 85 GB               |
| | 85 GB of 128 GB used          | |   |       Available: 43 GB            |
| +-------------------------------+ |   |                                   |
| | (37%) Cloud Storage           | |   | [ 🧹 Free Up Space Banner       ] |
| | 131 GB of 2 TB used           | |   |                                   |
| +-------------------------------+ |   | Category Breakdown:               |
| Favorites              [See All]  |   | 📱 Apps       55 GB [========== ] |
| [📁 Download]  [📁 Canva]         |   | 🎬 Videos     9.9 GB [===       ] |
| Recent Files           [See All]  |   | 📄 Documents  9.0 GB [==        ] |
| [📄 Photo.jpg] [📊 Sheet.xlsx]    |   | 🖼️ Images     6.8 GB [=         ] |
|-----------------------------------|   |-----------------------------------|
| [🏠 Home] [📁 Files] [☁️ Cloud]   |   | [🏠 Home] [📁 Files] [☁️ Cloud]   |
+-----------------------------------+   +-----------------------------------+
```

---

## 2. Essential Component Blueprints

### A. Drag & Drop Upload Zone
* **Idle State:** Muted dashed border (`border-2 border-dashed border-zinc-300 dark:border-zinc-700 rounded-2xl p-6 text-center bg-zinc-50/50 dark:bg-zinc-900/40`).
* **Drag-Over State:** Accent highlight (`border-blue-500 bg-blue-50/50 dark:bg-blue-950/20 scale-[1.01] transition-transform duration-150`).
* **Requirements:**
  * Centered upload icon inside a soft circular pill.
  * Clear action text: *"Click to upload or drag and drop"*.
  * Muted subtext listing supported formats and maximum file size (e.g. *"SVG, PNG, JPG, PDF up to 25MB"*).

### B. Storage Donut Gauge & Category Meters
* **Donut Chart Breakdown:**
  * Centered bold percentage/size (`text-2xl font-semibold` e.g., `"85.1 GB"`) with muted sub-label (`"Total Used"`).
  * Segmented SVG stroke colors matching the legend below:
    * Documents: Blue (`#3B82F6`)
    * Media/Videos: Purple (`#8B5CF6`)
    * System/Other: Slate (`#94A3B8`)
* **Linear Progress Bars:**
  * Always provide category icon + category name + file count + storage size.
  * Bar height: `h-2` with full rounded pill ends (`rounded-full bg-zinc-100 dark:bg-zinc-800`), filled with smooth transitions.

### C. Directory Tree View (NAS / cPanel Style)
* **Chevron Toggles:** Collapsible chevron icon (`>`) rotates 90 degrees (`rotate-90`) when expanded.
* **Indentation Scale:** Exactly `16px` (`pl-4`) per nested folder depth.
* **Selection State:** Active row highlighted with soft background (`bg-blue-50 dark:bg-blue-950/40 text-blue-600 dark:text-blue-400 font-medium rounded-lg`).

### D. File & Folder Cards (Grid vs. List Toggles)
* **Folder Cards:**
  * Clean folder icon (contrasting neutral or subtle accent color).
  * Title with `truncate` so long names do not push card bounds.
  * Micro-metadata: File count (e.g. `"118 files"`) and total weight (`"2.8 GB"`).
  * Quick-action footer: Download icon, Share icon, and overflow trigger (`...`).
* **Collaborator Avatar Stacks:**
  * Overlapping circular avatars (`-space-x-2 flex items-center`).
  * Overflow badge when more than 3 collaborators exist (`+3` pill with `text-xs font-medium text-zinc-600 dark:text-zinc-300 bg-zinc-100 dark:bg-zinc-800 border-2 border-white dark:border-zinc-900 rounded-full w-6 h-6 flex items-center justify-center`).

### E. Live File/Code Inspector Sidebar
* When a user selects a file (e.g. `functions.php` or `screenshot.png`):
  * **Top Header:** File icon + full filename + close button (`✕`).
  * **Tab Switcher:** `[Preview]` vs. `[Details]`.
  * **Code View:** Monospace font (`font-mono text-xs`), line numbers, syntax highlighting, and an instant `"Edit"` button.
  * **Metadata View:** File size, dimensions (for images), MIME type, creation date, and last modified timestamp.

---

## 3. Responsive Adaptation Strategy

| Screen Size | Layout Transformation |
| :--- | :--- |
| **Desktop (> 1200px)** | Full 3-pane layout: Left Navigation (220px) + Center File Area (flex-1) + Right Inspector (300px). |
| **Laptop / Tablet (768px – 1199px)** | 2-pane layout: Left Navigation + Center File Area. The Right Inspector collapses into a sliding **Right Drawer / Sheet** that opens only when a file is clicked. |
| **Mobile (< 768px)** | Single-pane mobile layout: Left navigation collapses into a **Bottom Tab Bar** (`Home`, `Files`, `Cloud`, `Storage Clean`). Cards switch to a 1-column list with swipe-for-actions. |

---

## 4. Micro-Interactions & Safety Guardrails

1. **Batch Selection Toolbar:**
   * When 1 or more checkboxes are checked, a floating bottom or top action pill emerges:
     `"[✓ 2 Files Selected]  [Download ↓]  [Move 📁]  [Delete 🗑️]"`
2. **Deletion Safety (Undo Toast):**
   * Never hard-delete files without immediate safety. Trigger a 5-second top floating notification:
     `"2 files moved to Trash. [Undo Action]"`
3. **Download Acknowledgment:**
   * Clicking download shows an instant spinner or checkmark inside the button: `"Preparing download..."` $\rightarrow$ `"Downloading..."`.
