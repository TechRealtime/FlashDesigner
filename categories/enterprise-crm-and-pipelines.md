# Category Spec: Enterprise CRM, Leads & Pipeline Management (`enterprise-crm-and-pipelines.md`)

> **Scope:** Customer Relationship Management (CRM) portals (Salesforce, HubSpot, Shakuro-style), deal pipelines, contact registries, lead scoring, and bulk data operations.

---

## 1. Master CRM Architecture

```text
+----------------------------------------------------------------------------------------------------+
| [Logo] Shakuro CRM   [ Quick Actions ⌘K ]                                         [ + New Contact ]|
+----------------------------------------------------------------------------------------------------+
| HEALTH & PIPELINE SUMMARY:                                                                         |
| Total Contacts      Active Contacts       Forgotten Contacts    Contact Velocity     Data Health   |
| 936                 856 (94%)             80 (6%)               1:42 (Normal)        82% (Optimal) |
| [~~~ Mini Area ~~~] [~~~ Mini Area ~~~]   [|||||||||| Barcode]  [|||||||||| Barcode] [==•=== Slider|
+----------------------------------------------------------------------------------------------------+
| VIEW TABS: [ Default ] [ Only Important ] [ + Add View ]                        [ Customize Columns|
+----------------------------------------------------------------------------------------------------+
| TOOLBAR: [ Filters ]  [ 🔍 Search contacts, emails, or companies... ]              [ ⬇️ Export CSV ] |
+----------------------------------------------------------------------------------------------------+
| DATA TABLE:                                                                                        |
| [ ] Initials   Name              Company           Position          City            Status        |
| [✓] [AE]       Amelia Evans      Glaze & Grain     UX Researcher     Niagara Falls   [• Active]    |
| [✓] [AT]       Ava Thompson      Apex Logic        Chief Designer    Saratoga        [• New]       |
| [✓] [BT]       Benjamin Taylor   Echo Media        Lead Developer    Troy            [• VIP]       |
| [✓] [CC]       Charlotte C.      Aura Wellness     Customer Success  Ithaca          [• Non-target]|
| [✓] [EC]       Emma Collins      TerraPulse        Project Manager   Syracuse        [• Active]    |
+----------------------------------------------------------------------------------------------------+
|                                                                                                    |
|       FLOATING BATCH ACTION DOCK (Bottom Center):                                                  |
|       +------------------------------------------------------------------------------+             |
|       | [✕]  Selected: 5  |  [↑ Export]  [📁 Move]  [🗑️ Delete]  [🔒 Lock]  [...]  |             |
|       +------------------------------------------------------------------------------+             |
+----------------------------------------------------------------------------------------------------+
| USER POPOVER MENU (Bottom Left):                                                                   |
| [ Avatar ] Emily Davis (emily.d@gmail.com)                                                         |
| -------------------------------------------------------------------------------------------------- |
| [ 🔄 Switch Account > ]   [ 👥 Invite Member ]   [ ⚙️ Settings ]   [ ❓ Help ]   [ 🚪 Log Out ]    |
+----------------------------------------------------------------------------------------------------+
```

---

## 2. Key Component Blueprints

### A. The Floating Batch Action Dock (Bottom Center)
When one or more rows are selected via checkboxes, a dark floating action pill appears anchored to the bottom-center of the screen:
```html
<div class="fixed bottom-6 left-1/2 -translate-x-1/2 z-50 flex items-center gap-3 px-4 py-2.5 rounded-2xl bg-zinc-950/90 dark:bg-zinc-900/90 text-white shadow-2xl backdrop-blur-md border border-zinc-800">
  <!-- Deselect Button -->
  <button class="p-1 rounded-full hover:bg-zinc-800 text-zinc-400 hover:text-white transition-colors">
    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
  </button>
  
  <span class="text-xs font-semibold tracking-wide pr-2 border-r border-zinc-800">
    Selected: 5
  </span>

  <!-- Action Buttons -->
  <div class="flex items-center gap-1.5 text-xs font-medium">
    <button class="inline-flex items-center gap-1 px-2.5 py-1.5 rounded-lg hover:bg-zinc-800 transition-colors">
      <span>Export</span>
    </button>
    <button class="inline-flex items-center gap-1 px-2.5 py-1.5 rounded-lg hover:bg-zinc-800 transition-colors">
      <span>Move</span>
    </button>
    <button class="inline-flex items-center gap-1 px-2.5 py-1.5 rounded-lg hover:bg-rose-950/40 text-rose-400 transition-colors">
      <span>Delete</span>
    </button>
  </div>
</div>
```

### B. KPI Metrics with Data Health & Velocity Gauges
* **Contact Velocity Barcode:** A row of thin vertical bars of varying heights (`flex items-end gap-0.5 h-4`) visualizing lead velocity over time.
* **Data Health Slider:** A linear slider track with a pin marker (`w-24 h-1.5 rounded-full bg-zinc-200 relative`) displaying overall CRM data hygiene score (e.g. `82% (Optimal)`).
* **Mini Area Sparklines:** Soft filled gradient area underneath contact totals illustrating 30-day velocity.

### C. Initials Avatar Pills
* Instead of missing or broken profile images, render high-contrast initials inside rounded rectangles:
  * Container: `w-8 h-8 rounded-lg bg-zinc-100 dark:bg-zinc-800 text-zinc-700 dark:text-zinc-300 flex items-center justify-center font-semibold text-xs`.
  * Distinct fallback for names: e.g. "Amelia Evans" $\rightarrow$ `AE`.

### D. CRM Contact Status Badges
* **`VIP`:** Gold/Amber pill (`bg-amber-500/15 text-amber-700 dark:text-amber-400 border border-amber-500/30 font-semibold`).
* **`Active`:** Crisp green pill (`bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 border border-emerald-500/20`).
* **`New`:** Vibrant blue pill (`bg-blue-500/10 text-blue-600 dark:text-blue-400 border border-blue-500/20`).
* **`Non-targeted`:** Muted neutral slate (`bg-zinc-100 dark:bg-zinc-800 text-zinc-500 dark:text-zinc-400`).

---

## 3. Account Switcher & Profile Popover

Positioned in the lower-left sidebar:
* Displays current active workspace / account with avatar and email.
* Clicking pops open an elevated card (`bg-white dark:bg-zinc-900 border border-zinc-200 dark:border-zinc-800 shadow-xl rounded-xl p-1.5 min-w-[200px]`):
  * Multi-account switcher (`Switch account >`).
  * Invite team members link.
  * Preferences & Settings.
  * Logout action (red text).
