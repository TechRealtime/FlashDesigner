# FlashDesigner: Document Catalog & Category Index (`INDEX.md`)

> **INSTRUCTION FOR AI AGENTS:**
> Consult this index to find the exact design specification matching the user's application needs. Read the recommended document **before** architecting your frontend code.

---

## 🗂️ Application Categories (`categories/`)

| Application Type | Keywords / Use Cases | Primary Spec File | Required Patterns |
| :--- | :--- | :--- | :--- |
| **HR Dashboards & People Analytics** | HRMS, employee directories, payroll, talent acquisition, attendance tracking, people analytics | [`categories/hr-analytics-and-portals.md`](categories/hr-analytics-and-portals.md) | `patterns/buttons-and-actions.md`, `patterns/loading-and-skeletons.md` |
| **File Managers, Cloud Drives & NAS** | Cloud storage, Dropbox/Drive clone, NAS explorer, cPanel file manager, folder trees, storage donut charts | [`categories/file-managers-and-nas.md`](categories/file-managers-and-nas.md) | `patterns/buttons-and-actions.md`, `patterns/loading-and-skeletons.md` |
| **LLM Chat & Agentic Workbenches** | ChatGPT/Claude/Arena interfaces, Antigravity-style agent IDEs, prompt bento grids, tool execution accordions, code diff review bars | [`categories/llm-chat-and-dashboards.md`](categories/llm-chat-and-dashboards.md) | `patterns/buttons-and-actions.md`, `patterns/loading-and-skeletons.md` |
| **Enterprise CRM & Lead Pipelines** | Customer portals, contact registries, lead velocity barcodes, floating batch action docks, data health sliders | [`categories/enterprise-crm-and-pipelines.md`](categories/enterprise-crm-and-pipelines.md) | `patterns/buttons-and-actions.md`, `patterns/loading-and-skeletons.md` |
| **Portfolios & Personal Sites** | Developer portfolios, interactive resumes, light/dark parity, embedded AI inquiry bars, timeline markers | [`categories/portfolios-and-personal-sites.md`](categories/portfolios-and-personal-sites.md) | `core/typography.md`, `core/theming.md` |
| **SaaS, Revenue & Intelligence Dashboards** | PulseBoard-style MRR tracking, AI brand visibility & AEO analytics, revenue arc gauges, source classification tables | [`categories/saas-dashboards.md`](categories/saas-dashboards.md) | `patterns/buttons-and-actions.md`, `patterns/loading-and-skeletons.md` |
| **B2B Data Tables & Filters** *(Coming soon)* | Complex filtering, bulk actions, dense spreadsheets, pagination, data grids | `categories/b2b-data-tables.md` | `patterns/buttons-and-actions.md` |
| **Landing Pages & Bento Grids** *(Coming soon)* | Marketing pages, product showcases, feature bento grids, pricing tables | `categories/landing-pages.md` | `core/typography.md`, `core/micro-interactions.md` |

---

## 🏛️ Core Design Foundations (`core/`)

| Guide | Description | File Path |
| :--- | :--- | :--- |
| **Multi-Screen Responsiveness** | Breakpoint system, preventing card squishing and button text wrapping on mobile. | [`core/responsiveness.md`](core/responsiveness.md) |
| **Typography & Font Stacks** | Font pairing (Inter, Google Sans, Open Sans), casing rules, and weight constraints. | [`core/typography.md`](core/typography.md) |
| **Micro-Interactions & Feedback** | Instant feedback ("Copied!", checkmarks), iOS-style easing curves, and toast notifications. | [`core/micro-interactions.md`](core/micro-interactions.md) |
| **Dual Theming Engine** | Explicit class-based Dark/Light mode, theme toggles, and high-contrast color tokens. | [`core/theming.md`](core/theming.md) |

---

## 🧩 Reusable Component Patterns (`patterns/`)

| Pattern | Description | File Path |
| :--- | :--- | :--- |
| **Buttons & Action Controls** | Click states (hover, active, disabled), morphing feedback (Copy -> Copied!), touch targets. | [`patterns/buttons-and-actions.md`](patterns/buttons-and-actions.md) |
| **Loading & Skeleton States** | Layout skeleton loaders, shimmer animations, and circular inline button spinners. | [`patterns/loading-and-skeletons.md`](patterns/loading-and-skeletons.md) |
