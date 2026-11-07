# Category Spec: HR Dashboards, People Analytics & Organization Portals (`hr-analytics-and-portals.md`)

> **Scope:** HR management systems (HRMS/HRIS), people analytics dashboards, employee directories, payroll overviews, talent acquisition pipelines, and internal organization portals.

---

## 1. Universal Layout Architecture

HR dashboards require high data density while maintaining visual breathability. The universal standard uses a multi-tier dashboard layout:

```text
+----------------------------------------------------------------------------------------------------+
| [Logo] Workly HR     [ 🔍 Search employees, teams, or roles... ⌘K ]          [🔔 2] [Theme] [Profile] |
+----------------------------------------------------------------------------------------------------+
| Welcome Back, Sarah 👋  "Here's what's happening with your team today."   [📅 Nov 1 - Nov 7] [+ New] |
+----------------------------------------------------------------------------------------------------+
| KPI ROW:                                                                                           |
| +------------------+ +------------------+ +------------------+ +----------------------------------+ |
| | Total Employees  | | On Leave Today   | | New Hires (MoM)  | | Attrition Rate                   | |
| | 128              | | 12               | | 6                | | 4.0%                             | |
| | ↗ +12% [||||||]  | | ↗ +2% [||||||]   | | ↗ +20% [||||||]  | | ↘ -1.2% [~~~~~~~~]              | |
| +------------------+ +------------------+ +------------------+ +----------------------------------+ |
+----------------------------------------------------+-----------------------------------------------+
| ANALYTICS GRID:                                    | SIDEBAR / SCHEDULE RAIL:                      |
|                                                    |                                               |
| Attendance & Hiring Trends (Spline Chart)          | Mini Calendar [ January 2026 ]                |
| - Time filters: [ 7d | 30d | 1y | All ]            | [ 15 | 16 | 17 | (18) | 19 | 20 ]             |
| - Interactive tooltip: Present: 180 | Absent: 12   |                                               |
|                                                    | Today's Meetings:                             |
| Team Distribution (Donut)  Leave Overview (Bars)   | | Teal: 1-on-1 with Alex [Avatar Stack +3]    |
| - Product: 40              - Monthly leave spikes  | | Blue: Design Review    [Avatar Stack +5]    |
| - Engineering: 32          - April highlight (12)  |                                               |
| - Design: 28                                       | Quick Actions:                                |
|                                                    | [+ Add Employee] [Request Leave] [Export CSV] |
+----------------------------------------------------+-----------------------------------------------+
| EMPLOYEE DIRECTORY & ACTIVITIES TABLE:                                                             |
| [ 🔍 Search ]  [ All Statuses v ]  [ All Departments v ]  [ View: List | Board ]      [ Export CSV ]|
| [ ] ID       Name & Avatar       Role           Department    Join Date    Status         Actions  |
| [ ] #EMP01   Sarah Lee (Avatar)  Lead Designer  Product       Jan 12, 2026 [• Full-time]  [👁️] [...]|
| [✓] #EMP02   David Kim (Avatar)  Accountant     Finance       Feb 02, 2026 [• On Leave]   [👁️] [...]|
+----------------------------------------------------------------------------------------------------+
```

---

## 2. Key Metric & KPI Card Blueprints

### A. Trend-Sparkline Metric Card
* **Header:** Metric label (`text-xs font-medium text-zinc-500 dark:text-zinc-400 uppercase tracking-wider`) with matching category icon.
* **Large Metric:** `text-2xl sm:text-3xl font-semibold text-zinc-900 dark:text-zinc-100`.
* **Footer:**
  * Trend Badge: Pill with upward green arrow (`↗ +12%` in `bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 text-xs font-semibold px-2 py-0.5 rounded-full`).
  * Micro Sparkline: Subtle mini bar chart (5–6 vertical bars) or mini trend line illustrating month-over-month trajectory.

### B. Radial & Semi-Circle Gauge Card
* Used for capacity limits (e.g., Attendance Rate `90%`, Open Jobs `70 Total Jobs`).
* Semi-circle SVG arc gauge (`stroke-dasharray`) with center metric count.
* Legend beneath displaying status breakdown (e.g., `• Sick Leave  • Day Off  • On Time`).

### C. Split Count Metric Card
* For hybrid workforces or employee classifications:
  * Top half: `150 Full-time Employees`
  * Divider: 1px subtle divider
  * Bottom half: `50 Freelance / Contractors`

---

## 3. Data Visualization & Analytics Components

### A. Attendance & Hiring Spline Charts
* **Grid lines:** Very faint dashed lines (`stroke-zinc-200 dark:stroke-zinc-800`).
* **Multi-Point Hover Tooltip:**
  * Dark rounded card (`bg-zinc-900 text-white dark:bg-zinc-800 shadow-xl border border-zinc-700 p-2.5 rounded-xl text-xs`).
  * Displays date + breakdown per department or attendance status.
* **Timeframe Segmented Control:** Clean pill button group (`[ 1d | 7d | 1m | 1y | All ]`).

### B. Department Distribution Donut Chart
* Donut hole displaying total headcount (`128 Employees`).
* Colored legend dots matching chart segments:
  * Product: Blue (`#3B82F6`)
  * Engineering: Amber (`#F59E0B`)
  * Design: Purple (`#8B5CF6`)
  * Marketing: Emerald (`#10B981`)
  * Others: Slate (`#64748B`)

### C. Working Format Segmented Bar
* Visual representation of workplace model:
  * Horizontal bar segmented into On-Site (`46.8%`), Hybrid (`26.8%`), and Remote (`26.4%`).
  * Smooth pill edges with distinct color keys.

---

## 4. Employee Directory & Roster Data Table

### Table Anatomy & Ergonomics
* **Toolbar:**
  * Search bar with instant keyboard focus shortcut (`⌘K`).
  * Filter dropdowns: Department, Role, Employment Status (`All`, `Full-time`, `Contract`, `On Leave`).
  * View Switcher: `List View` vs. `Board / Grid View`.
* **Row Formatting:**
  * **Employee Identity:** Circular avatar (32x32px) + Name (`font-medium text-zinc-900 dark:text-zinc-100`) + Email (`text-xs text-zinc-500`).
  * **Status Badges (Mandatory Semantic Colors):**
    * **Active / Full-time:** Green pill (`bg-emerald-500/10 text-emerald-600 dark:text-emerald-400 border border-emerald-500/20`).
    * **On Leave:** Amber/Orange pill (`bg-amber-500/10 text-amber-600 dark:text-amber-400 border border-amber-500/20`).
    * **Absent / Terminated:** Red pill (`bg-rose-500/10 text-rose-600 dark:text-rose-400 border border-rose-500/20`).
    * **Freelance / Intern:** Blue/Purple pill (`bg-blue-500/10 text-blue-600 dark:text-blue-400 border border-blue-500/20`).
  * **Row Actions:** Hoverable eye icon (quick preview drawer) and overflow menu (`...`).

---

## 5. Talent Acquisition & Candidate Sourcing Cards

When displaying recruitment pools or candidate pipelines:
* **Job Requisition Bento Card:**
  * Job title (e.g. `Senior Software Engineer`) with department dot.
  * Status badge (`• Active`).
  * Candidate metric badge (`57 Candidates` in pill).
  * Recruiter byline with tiny avatar.
  * 3-dot management trigger.

---

## 6. Dual Theming Standards for HR Dashboards

* **Light Mode (Clean Studio Slate):**
  * Canvas: `#F8FAFC` (Slate-50)
  * Cards: `#FFFFFF` (Pure white) with 1px border `#E2E8F0`
  * KPI Icons: Soft pastel background circles (`bg-blue-50`, `bg-emerald-50`, `bg-purple-50`)
* **Dark Mode (High-Density Operations):**
  * Canvas: `#0E1015` (Deep slate charcoal)
  * Cards: `#161920` (Elevated charcoal) with 1px border `#232733`
  * Text: High-contrast `#F3F4F6` for headers, `#9CA3AF` for subtext
  * Contrast check: Never use low-contrast gray text on dark table rows.

---

## 7. Responsive Rules for HR Portals
1. **Desktop (> 1200px):** Full 3-column layout (Nav Sidebar + Main HR Workspace + Right Schedule/Calendar Rail).
2. **Tablet (768px – 1199px):**
   * Right Schedule Rail moves below the main analytics grid.
   * KPI cards wrap into a clean 2x2 grid.
3. **Mobile (< 768px):**
   * Sidebar collapses into mobile slide-out drawer.
   * KPI cards stack vertically or become swipeable horizontal cards.
   * Employee table enables horizontal scroll (`overflow-x-auto`) with the **Employee Name & Avatar pinned as a sticky left column** so identity is never lost while scrolling right.
