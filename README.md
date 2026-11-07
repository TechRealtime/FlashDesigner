# FlashDesigner ⚡

> **The AI Design System & Knowledge Base for AI Agents, LLMs, and Vibe Coders.**
> Eliminate "AI slop" and turn any AI into a senior product designer with structured, deterministic UI guidelines.

---

## 🎯 What is FlashDesigner?

When LLMs write frontend code, they default to repetitive, uninspired patterns: generic purple gradients, missing interaction feedback, awkward text wrapping on mobile screens, and cheesy AI star icons.

**FlashDesigner** is a Knowledge Base System (KBS) designed to be fed into any AI (Claude, Antigravity, Cursor, ChatGPT, Gemini, etc.) via link or prompt. It provides:
1. **Mandatory Guardrails (`RULES.md`):** Strict "do's and don'ts" prohibiting ugly AI habits and requiring professional-grade UI hygiene.
2. **Category Routing (`INDEX.md`):** Directs the AI to read *only* the specific architectural design specs relevant to your current project.
3. **Component & Interaction Blueprints (`core/` & `patterns/`):** Real-world UI tokens, responsive layout rules, smooth iOS-like micro-interactions, and smart sticky-scroll mechanics.

---

## 🚀 How to Use FlashDesigner with Any AI

### Option A: Web Link / Prompt Ingestion (Claude, ChatGPT, AI Studio)
Give your AI this instruction at the beginning of your prompt:
```markdown
Before designing or writing code, read FlashDesigner's rules and match the category for my app:
1. Read RULES.md: [link to raw RULES.md]
2. Read INDEX.md: [link to raw INDEX.md]
3. Identify the matching category and read its spec document.
4. Output your 3-point UI plan before generating code.
```

### Option B: Local IDE Rules (Cursor, Antigravity, Windsurf)
Place the `FlashDesigner` folder in your project or reference it in your workspace rules (`.cursorrules` or `.gemini/antigravity/rules/ui.md`).

---

## 📂 Repository Layout

```text
FlashDesigner/
├── llms.txt                     <-- Machine-readable index standard for AI agents
├── RULES.md                     <-- Mandatory Guardrails & AI Execution Contract
├── INDEX.md                     <-- Document catalog & category router
│
├── core/                        <-- Non-negotiable design fundamentals
│   ├── responsiveness.md        <-- Multi-screen ratio rules & overflow safety
│   ├── typography.md            <-- Font selection, weights, and casing rules
│   ├── micro-interactions.md    <-- Immediate action feedback (copy, save, toasts)
│   └── theming.md               <-- Dual dark/light theme engine & contrast
│
├── categories/                  <-- App-specific architectural guides
│   ├── llm-chat-and-dashboards.md <-- ChatGPT/Gemini-style streaming workbenches
│   └── saas-dashboards.md       <-- Analytics, KPI metrics, and sidebar layouts
│
└── patterns/                    <-- Micro-UI recipes
    ├── buttons-and-actions.md   <-- State acknowledgement & button ergonomics
    └── loading-and-skeletons.md <-- Skeletons vs. circular spinners
```
