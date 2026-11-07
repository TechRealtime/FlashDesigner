# Category Spec: AI Chat Interfaces, Agentic IDEs & Workbenches (`llm-chat-and-dashboards.md`)

> **Scope:** Modern conversational AI assistants (ChatGPT, Claude, Arena), Agentic Developer Workbenches & IDEs (Antigravity, Cursor), and Reasoning Interfaces with tool execution accordions.

---

## 1. Master Layout Archetypes

### Archetype A: The Agentic Developer Workbench (Antigravity Style)
Best for: AI coding assistants, multi-agent workspaces, developer tools, and file-editing IDEs.

```text
+----------------------------------------------------------------------------------------------------+
| Antigravity  Workspace / Project / File           [ ⌘K Command ]             [—] [口] [✕]          |
+----------------------+-----------------------------------------------------------------------------+
| SIDEBAR              | CONVERSATION CANVAS                                                         |
| [+ New Conversation] |                                                                             |
|                      | User: "Create a UI Knowledge Base for AI..."                                |
| PINNED               |                                                                             |
| - Frontend Engine 8h | Assistant (Gemini 3.8 Flash High):                                          |
| - Low Comp Tool   9d | "Here is the architectural plan..."                                         |
|                      | [ Markdown tables, syntax code blocks, bullet hierarchy ]                   |
| PROJECTS             |                                                                             |
| v Project Alpha      | Artifact Diff Bar:                                                          |
|   • Active Session   | [ 📄 3 files changed  +149 -0  > ]                          [ 👁️ Review ]   |
|   • Setup Script     |                                                                             |
| > Project Beta       | [ 👍 Upvote ] [ 👎 Downvote ] [ 📋 Copy ]                     1m ago        |
|                      +-----------------------------------------------------------------------------+
|                      | PROMPT INPUT CONTAINER (Anchored Bottom)                                    |
|                      | +-------------------------------------------------------------------------+ |
|                      | | [Img 1 ✕] [Img 2 ✕] [Img 3 ✕] (Attached Thumbnails Tray)                | |
|                      | | Ask anything, @ to mention files, / for actions...                      | |
|                      | |                                                                         | |
| [⚙️ Settings]        | | [+] [ Gemini 3.8 Flash High v ]              [ Turbo v ]    [ (↑) Send] | |
|                      | +-------------------------------------------------------------------------+ |
+----------------------+-----------------------------------------------------------------------------+
```

### Archetype B: Conversational Assistant & Starter Prompt Bento (Arena / Claude Style)
Best for: General chat, creative assistants, and new conversation onboarding.

```text
+----------------------------------------------------------------------------------------------------+
| [Logo] AI Assistant  [ Sidebar Toggle ]                                              [ Share ]     |
+----------------------------------------------------------------------------------------------------+
|                                                                                                    |
|                                     Experience the frontier                                        |
|                          "Our fastest and smartest co-pilot for high-speed design."                |
|                                                                                                    |
|                 +---------------------------------------------------------------+                  |
|                 | Ask me anything...                                            |                  |
|                 |                                                               |                  |
|                 | [📎 Attach] [⚡ Tools]                [ Claude 3.5 Sonnet v ] [ (↑) ]            |                  |
|                 +---------------------------------------------------------------+                  |
|                                                                                                    |
|   STARTER PROMPT BENTO GRID:                                                                       |
|   +-----------------------------+ +-----------------------------+ +----------------------------+   |
|   | 📄 Create a landing page    | | 📊 Build a dashboard        | | 🎮 Make a game             |   |
|   | Modern high-converting hero | | Turn data into charts       | | Playable canvas game       |   |
|   +-----------------------------+ +-----------------------------+ +----------------------------+   |
|   | 🎨 Design to Code           | | ⚡ Build a fullstack app    | | 🛍️ Launch a storefront     |   |
|   | Convert screenshots to UI   | | Next.js + Tailwind starter  | | Complete e-commerce cart   |   |
|   +-----------------------------+ +-----------------------------+ +----------------------------+   |
|                                                                                                    |
|   QUICK ACTION CHIPS:                                                                              |
|   [ 🔍 Deep Search ]   [ 🖼️ Create Images ]   [ 📰 Latest News ]   [ 🎥 Generate Video ]           |
+----------------------------------------------------------------------------------------------------+
```

### Archetype C: Reasoning & Tool-Execution Chat (ProteSyn Style)
Best for: Deep research agents, scientific workflows, and multi-step tool calls.

```text
+----------------------------------------------------------------------------------------------------+
| Assistant Message:                                                                                 |
|                                                                                                    |
| [ ◌ Thinking... (Collapsible 12s)                                                               v ]|
|                                                                                                    |
| [ 🔍 Tool Call: Searching the web                                                               ^ ]|
|   • Query: "Cognitive biases in product design"                                                    |
|   • Sources: [ 🌐 maze.co ] [ 🌐 pendo.io ] [ 🌐 uxplanet.org ] [ 🌐 interaction.org ]             |
|                                                                                                    |
| The research demonstrates that cognitive biases significantly influence layout hierarchy...         |
+----------------------------------------------------------------------------------------------------+
```

---

## 2. Anatomy of the Modern Prompt Container

The prompt container is the most critical component in any AI interface. It must support multiple modes without jumping or breaking:

### 1. Attachment Thumbnail Tray
* When images or files are attached:
  * Render a horizontal row of rounded thumbnail cards directly above the textarea (`flex items-center gap-2 pb-2`).
  * Image cards: `w-14 h-14 object-cover rounded-lg border border-zinc-200 dark:border-zinc-800 relative group`.
  * Remove button: Tiny circular `✕` icon on top-right of thumbnail (`absolute -top-1.5 -right-1.5 bg-zinc-900 text-white rounded-full p-0.5 shadow-md`).

### 2. Expanding Textarea & Action Triggers
* **Auto-Growth:** Starts at `min-h-[48px]`, grows smoothly to `max-h-[200px]` before internal scrolling activates.
* **Placeholder Micro-Copy:** *"Ask anything, @ to mention files, / for actions..."*.
* **Keyboard Triggers:**
  * Typing `@` opens an inline File/Symbol Mention popup.
  * Typing `/` opens the Slash Commands menu (e.g., `/plan`, `/clean`, `/summarize`).

### 3. Integrated Bottom Controls Bar
* **Model Selector Pill:**
  * Displays active model name + icon (e.g. `[ Gemini 3.8 Flash High ^ ]` or `[ Claude-3.5-sonnet ^ ]`).
  * Smooth dropdown menu allowing model switching.
* **Execution / Permission Mode Pill:**
  * Status indicator (e.g., `[ Turbo v ]`, `[ Read-Only ]`, `[ Auto-Approve ]`).
* **The Modern Send Button:**
  * **Icon:** Centered upward arrow (`↑`) in a circular pill.
  * **State Logic:**
    * Empty input: Disabled muted gray (`bg-zinc-800 text-zinc-500 cursor-not-allowed`).
    * Ready input: Active accent color (`bg-blue-600 hover:bg-blue-500 text-white cursor-pointer scale-100 active:scale-95`).
    * While AI is generating: Morphs into a Stop icon (`■`) to interrupt stream.

---

## 3. Code Diffs & Artifact Review Bars (Antigravity Standard)

When the AI writes code or modifies workspace files, do not dump 500 lines of raw code into the chat. Use an **Artifact Diff Notification Pill**:

```html
<div class="flex items-center justify-between p-3 my-3 rounded-xl bg-zinc-900 border border-zinc-800 text-sm">
  <div class="flex items-center gap-2">
    <!-- File icon -->
    <svg class="w-4 h-4 text-zinc-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path>
    </svg>
    <span class="font-medium text-zinc-200">3 files changed</span>
    <span class="text-xs font-mono text-emerald-400 font-semibold">+149</span>
    <span class="text-xs font-mono text-rose-400 font-semibold">-0</span>
  </div>
  <button class="inline-flex items-center gap-1 px-3 py-1 text-xs font-semibold rounded-lg bg-zinc-800 hover:bg-zinc-700 text-zinc-100 transition-colors border border-zinc-700">
    Review Changes
  </button>
</div>
```

---

## 4. Tool Execution & Reasoning Accordions

* **"Thinking..." Accordion:**
  * Light outline or soft background with a pulsing/spinning indicator.
  * Shows duration (e.g. `Thinking (8s)...`).
  * Default behavior: Open while generating, auto-collapses when final response begins streaming.
* **Web Search & Tool Calling Cards:**
  * Expandable box displaying the exact search query executed.
  * Pill badges for citations with company favicons/domain names (e.g. `maze.co`, `pendo.io`, `github.com`).
  * Clicking any pill opens the source citation.

---

## 5. Agent Settings & Preferences Modal Architecture

When configuring an AI assistant or agentic IDE:

```text
+----------------------------------------------------------------------------------------------------+
| Settings                                                                             [✕ Close]     |
+-------------------+--------------------------------------------------------------------------------+
| TABS (Left):      | SETTINGS PANE (Right):                                                         |
|                   |                                                                                |
| - General         | General                                                                        |
| - Application     | "Configure agent execution, queued message delivery, and permissions."         |
| - Appearance      |                                                                                |
| - Shortcuts       | Global Permissions                                                             |
| - Notifications   | Permission Preset: [ Turbo v ]                                                 |
| - Models          | Tool Permissions:  [ 99 Tools Configured ] [ Open ]                            |
|                   | Network Rules:     [ Configure Access ]     [ Open ]                           |
|                   |                                                                                |
|                   | Agent Behavior                                                                 |
|                   | Plan Review Policy: [ Always Proceed v ]                                       |
|                   | "Type / and select plan to have the agent generate a structured roadmap."      |
|                   |                                                                                |
|                   | Execution Queue                                                                |
|                   | Queued Messages:    [ (Queue) | (Send Immediately) ] (Segmented Switch)        |
+-------------------+--------------------------------------------------------------------------------+
```

* **Left Navigation:** Vertical tab list (`General`, `Appearance`, `Shortcuts`, `Models`).
* **Segmented Controls:** Pill switches for binary decisions (`[Queue | Send Immediately]`).
* **Status Badges:** Small numbered badges for active counts (e.g., `Tool Permissions [99]`).

---

## 6. Smart Sticky Auto-Scroll Logic (Mandatory)

1. Auto-scroll strictly follows the incoming token stream downward.
2. **Interrupt on Manual Up-Scroll:** If the user scrolls upward by more than `80px` from the bottom, lock scrolling immediately.
3. **Floating "Scroll to bottom" Pill:** Surface a floating button `[ ↓ Jump to bottom ]` at the bottom-center of the chat canvas while scrolled up. Clicking it smoothly restores bottom anchoring.
