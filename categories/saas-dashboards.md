# Category Spec: SaaS, Revenue & Intelligence Dashboards (`saas-dashboards.md`)

> **Scope:** Business management consoles, Revenue & MRR tracking (PulseBoard style), AI Brand Visibility & Intelligence (AEO / GEO monitors), and cloud analytics portals.

---

## 1. Master Layout Structure

```text
+----------------------------------------------------------------------------------------------------+
| [Logo] AI Visibility Intelligence   [ Search anything... ⌘K ]          [🔔] [📅 1 June - 30 June]  |
+----------------------------------------------------------------------------------------------------+
| INSIGHT BANNER:                                                                                    |
| [✨ Weekly Insight: Your AI visibility increased 12.4% compared to previous week]  [View Insight ↗] [✕]|
+----------------------------------------------------------------------------------------------------+
| REVENUE & KPI ROW:                                                                                 |
| +---------------------+ +---------------------+ +---------------------+ +-----------------------+ |
| | Total Revenue       | | Monthly Recurring   | | ARPU                | | Churn Rate            | |
| | $84,210             | | $21,450             | | $17.18              | | 3.2%                  | |
| | ↗ +13.8% MoM        | | ↗ +21.8% MoM        | | ↗ +16.8% MoM        | | ↘ -12.8% MoM          | |
| +---------------------+ +---------------------+ +---------------------+ +-----------------------+ |
+-------------------------------------------------------+--------------------------------------------+
| MULTI-SERIES SPLINE CHART:                            | REVENUE ARC / GAUGE:                       |
|                                                       |                                            |
| Revenue Growth & Brand Mentions                       | Revenue by Source:                         |
| Timeframe Toggle: [ Days | Week | Month ]             |               ( $84,210 )                  |
| Peak Tooltip: [ 5 MAY 2026 | 509K Active Leads ]      |             ↗ +16.8% Last Month            |
|                                                       |                                            |
| [ Multi-colored lines: Nexora, Quantive, Searchly ]   | • Subscriptions (62%)     $52,120          |
|                                                       | • One-time Sales (20%)    $16,840          |
|                                                       | • Add-ons (10%)           $8,420           |
|                                                       | • Refunds (03%)           $2,620           |
+-------------------------------------------------------+--------------------------------------------+
| LEADERBOARD & CITATION SOURCES:                                                                    |
|                                                                                                    |
| Brand Performance Leaderboard:                         Most Referenced Sources:                    |
| #  Brand         Visibility  Perception  Avg. Pos      Source          Usage   Classification      |
| 1  Nexora        46.9%       • 71        #2.1          [in] linkedin   72%     [• Community]       |
| 2  Quantive      42.7%       • 63        #3.5          [yt] youtube    58%     [• Media]           |
| 3  Searchly      39.8%       • 58        #4.8          [rd] reddit     44%     [• Discussion]      |
| 4  InsightFlow   37.2%       • 54        #5.9          [gh] github     24%     [• Technical]       |
+----------------------------------------------------------------------------------------------------+
```

---

## 2. Advanced Component Blueprints

### A. The Weekly Insight Action Banner
* Placed at the very top of the dashboard canvas:
* Style: Muted emerald or slate surface (`bg-emerald-50 dark:bg-emerald-950/20 border border-emerald-200 dark:border-emerald-900/50 rounded-xl p-3 flex items-center justify-between`).
* Content: Bold key metric callout + direct action link (`[ View Insight ↗ ]`) and a quick dismiss button (`✕`).

### B. The Semi-Circle Revenue Arc Gauge
* Displays revenue by category:
  * Central metric: Total revenue (`text-3xl font-bold`) + delta badge (`↗ +16.8% Last month`).
  * SVG semi-circle arc segmented into color-coded shares (Subscriptions blue `#3B82F6`, Sales orange `#F97316`, Add-ons green `#10B981`, Refunds red `#EF4444`).
  * Itemized breakdown rows: Dot + Category label + Percentage share + Monetary amount formatted cleanly.

### C. Source Classification Pills
In intelligence and traffic source tables, categorize domains with semantic pill tags:
* **Community:** `bg-teal-500/10 text-teal-600 dark:text-teal-400`
* **Media:** `bg-rose-500/10 text-rose-600 dark:text-rose-400`
* **Discussion:** `bg-amber-500/10 text-amber-600 dark:text-amber-400`
* **Editorial:** `bg-blue-500/10 text-blue-600 dark:text-blue-400`
* **Technical:** `bg-purple-500/10 text-purple-600 dark:text-purple-400`
* **Startup:** `bg-indigo-500/10 text-indigo-600 dark:text-indigo-400`

### D. Timeframe Segmented Switcher
* Clean pill group: `[ Days | Week | Month ]`.
* Active tab has high-contrast background (`bg-zinc-900 text-white dark:bg-white dark:text-zinc-900 rounded-lg px-3 py-1 font-medium shadow-sm transition-all`).

---

## 3. Responsive Safeguards for High-Density Dashboards
1. **Desktop (> 1200px):** 2-column analytics grid (Chart + Arc Gauge) and 2-column table split (Leaderboard + Referenced Sources).
2. **Tablet (768px – 1199px):** Stacks into single-column rows with charts retaining full height (`h-72`).
3. **Mobile (< 768px):**
   * Tables become horizontally scrollable with sticky brand/source name column.
   * KPI row becomes a swipeable horizontal snap carousel (`flex overflow-x-auto snap-x gap-3 pb-2`).
