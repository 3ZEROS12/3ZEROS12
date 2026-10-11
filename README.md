# Jason Song (@3ZEROS12)

I build low-overhead runtime extensions, terminal UI layout engines, and offline data/OCR pipelines. Currently studying Big Data Management and Application at Xidian University (`GPA 3.8/4.0`, Xi'an).

Most of my open-source work starts from physical friction encountered during daily engineering:
- **The 5-to-15-second generation wait**: After hitting `Enter` in a terminal coding agent, the pause is too short to switch to a browser and just long enough for focus to drift.
- **Terminal geometry and context bloat**: East Asian full-width characters (`2` cells vs. `1` ASCII cell) tear closed terminal borders on narrow split panes, while `500`-line test stack traces flood the context window and trigger premature compaction.
- **Session amnesia**: Pressing `Ctrl+C` exits the process and wipes working memory, while tracking tasks in `TODO.md` pollutes git history and burns system prompt tokens on every turn.
- **Air-gapped field operations**: At bank branch terminals with zero internet access, staff spend `15` minutes manually transcribing `60`-row skewed paper renewal receipts into Excel.

[**npm (`~jason-zeros`)**](https://www.npmjs.com/~jason-zeros) · [**GitHub (`@3ZEROS12`)**](https://github.com/3ZEROS12) · [**Email (`jiaxinsong312@gmail.com`)**](mailto:jiaxinsong312@gmail.com)

---

## Pi Terminal Suite

Four composable packages published on npm for [Pi Coding Agent](https://github.com/earendil-works/pi-coding-agent). Each package mounts to a separate spatial or runtime slot (`aboveEditor`, runtime tool hooks, `belowEditor`, and `status-only` footer) so all four run together with zero widget overlap:

```text
  ┌─ aboveEditor HUD (pi-lingual · <= 9 lines · UAX #11 open left-rail tree) ──────────┐
  │  · [Original] El PR es demasiado grande, sugiero dividirlo en dos cambios          │
  │  ┌ [Spoken]   This PR is huge; we'd be better off splitting it into two changes.   │
  │  ├ [Written]  The PR scope is overly broad; decomposing into two commits is advised│
  │  └ [Vocab]    overly broad · be better off · split into · atomic commits           │
╭─┴─ Pi Editor & Runtime Hooks (toolflow · stage-gated tools & -95% log dehydration) ──╮
│ ❯ pin: Refactor auth flow: 1. Extract interface 2. HttpOnly cookie 3. Unit tests     │
╰─┬─ belowEditor Sticky Strip (pi-anchor · 0ms pin: intercept & session jump) ─────────╯
  ├─► ⌖ #1 [■■□□ 2/4] Refactor auth flow ▸ Unit tests (app · auth.ts ↪)
  └─► status-only Footer (pi-tui-status-beautifier): plan ❯ ◆ 3  toolflow ❯ ⌬ 2/5  (+2 idle)
```

| Package | Registry & Monthly Downloads | Slot & Mechanism | Verification |
| :--- | :--- | :--- | :--- |
| **[`pi-lingual`](https://github.com/3ZEROS12/pi-lingual)** | [![npm](https://img.shields.io/npm/v/pi-lingual?color=blue&label=npm)](https://www.npmjs.com/package/pi-lingual) [![downloads](https://img.shields.io/npm/dm/pi-lingual?color=22c55e&label=downloads)](https://www.npmjs.com/package/pi-lingual) | **`aboveEditor` UAX #11 Tree HUD & Prompt Rewriter**: Renders a dual-register (`[Spoken]` standup phrasing + `[Written]` RFC prose) overlay (`<= 9` lines, Kinsoku line-head punctuation rules) or rewrites native prompts into technical English while preserving code blocks verbatim. Zero tokens injected into chat history; `50`-entry in-memory LRU cache. | `93/93` tests pass |
| **[`toolflow`](https://github.com/3ZEROS12/toolflow)** | [![npm](https://img.shields.io/npm/v/toolflow?color=blue&label=npm)](https://www.npmjs.com/package/toolflow) [![downloads](https://img.shields.io/npm/dm/toolflow?color=22c55e&label=downloads)](https://www.npmjs.com/package/toolflow) | **Runtime Tool Sandboxing & `-95%` Log Dehydration**: Keeps core tools persistent while stage-gating heavy MCP schemas across research, implementation, and read-only review phases. Redirects command outputs exceeding `40` lines to disk, returning exit codes and root failure summaries, and blocks destructive writes to `.env*` and `.git*`. | `26/26` suites pass |
| **[`pi-tui-status-beautifier`](https://github.com/3ZEROS12/pi-tui-status-beautifier)** | [![npm](https://img.shields.io/npm/v/pi-tui-status-beautifier?color=blue&label=npm)](https://www.npmjs.com/package/pi-tui-status-beautifier) [![downloads](https://img.shields.io/npm/dm/pi-tui-status-beautifier?color=22c55e&label=downloads)](https://www.npmjs.com/package/pi-tui-status-beautifier) | **`status-only` Badge Folding & 0-I/O Footer Engine**: Normalizes extension status strings across `6` visual presets while leaving Pi's native telemetry lines untouched. Folds idle badges into `(+N idle)` on narrow (`<80`-col) split panes and performs `0` synchronous disk reads during TUI redraw loops. | `18/18` tests pass |
| **[`pi-anchor`](https://github.com/3ZEROS12/anchor)** | [![npm](https://img.shields.io/npm/v/pi-anchor?color=blue&label=npm)](https://www.npmjs.com/package/pi-anchor) [![downloads](https://img.shields.io/npm/dm/pi-anchor?color=22c55e&label=downloads)](https://www.npmjs.com/package/pi-anchor) | **`0ms` `belowEditor` Sticky Strip & Session Jump**: Intercepts `pin:` notes in `0ms` with `0` LLM calls. Renders `[■■□□]` step bars, bookmarks `.jsonl` session transcripts (`↪`) for one-click context switches, stores state globally in `~/.anchor/` with `fs.openSync('wx')` locks (`0` repo files, `0` Turn-2+ prompt tokens), and auto-archives on `git commit`. | `25/25` assertions pass |

```bash
pi install npm:pi-lingual
pi install npm:toolflow
pi install npm:pi-tui-status-beautifier
pi install npm:pi-anchor
```

---

## Applied Systems, Vision & Data Engineering

### [`lingual-desktop`](https://github.com/3ZEROS12/lingual-desktop) · Native Windows Ambient Writing Companion
`TypeScript` · `Electron` · `C# UI Automation` · `MinGW C` · `24/24 Tests Pass`

- Extends the dual-register translation workflow from the terminal to any Windows text input (X, Slack, Discord, Notion, Chrome) alongside existing IMEs.
- Reads focused input controls directly in UTF-8 via native C# `UIA ValuePattern` (`<2ms`) with an atomic clipboard transaction guard (`<160ms`) and `Esc` three-second undo.
- Includes a process guard that detects terminal emulators (`WindowsTerminal`, `WezTerm`, `PowerShell`, `cmd`) and passes `Enter` keystrokes through with zero interception.

### [`bank-asset-table-ocr-extractor`](https://github.com/3ZEROS12/bank-asset-table-ocr-extractor) · Air-Gapped Financial Table OCR & Risk Verification Workbench
`Python` · `RapidOCR (ONNX Runtime)` · `OpenCV` · `PyMuPDF` · `openpyxl`

- Built during my summer internship at Chang'an Bank (Client Department) to digitize `60`-row paper asset renewal receipts on offline branch terminals (`0%` external network access).
- Combines affine deskewing, morphological grid-line removal (Telea inpainting), `15`-digit customer ID row-anchor alignment, ink-density blank-cell detection (`<1.5%` black pixel ratio), `2x` bicubic super-resolution with CLAHE contrast stretching, and `3`-offset spatial voting.
- Cut single-sheet processing time from `15` minutes to `8-18` seconds across `500+` credit archives, reaching `100%` row recall and `96.9%-99.9%` cell accuracy with automatic Excel anomaly highlighting.

### [`digit-recognition-fastapi`](https://github.com/3ZEROS12/digit-recognition-fastapi) · Document Vision Preprocessing & Async Inference API
`Python` · `PyTorch` · `OpenCV` · `FastAPI`

- Built during a technical internship at Xi'an Jianhe Information Technology alongside standalone Python executables for automated global IP data extraction and cleaning.
- Pairs a PyTorch CNN with OpenCV preprocessing (contour extraction, deskewing, red-channel stamp filtering, character segmentation) to serve structured JSON predictions over async FastAPI endpoints.

### [`Gabriel`](https://github.com/3ZEROS12/Gabriel) · Desktop GUI Sidecar & Local Hybrid Search Sandbox `[Archived Prototype]`
`Python` · `SQLite FTS5` · `sqlite-vec` · `39/39 pytest Pass`

- Early desktop sidecar built to monitor autonomous CLI coding agent transcripts (`Claude Code`, `Cursor`, `Antigravity`) in a `1/4`-screen window without interrupting long refactoring loops.
- Implemented dual-track Reciprocal Rank Fusion (`SQLite FTS5` BM25 + `sqlite-vec` embeddings) and one-click error snapshot pinning. Archived after distilling its core workflows directly into in-terminal primitives (`pi-anchor` and `toolflow`).

### [`rea`](https://github.com/3ZEROS12/rea) · Agentic Reverse Engineering & Binary Inspection Workflows
`TypeScript` · `Python` · `Agent Tooling`

- Explores agent-driven reverse engineering pipelines from application-level behavior and network protocols down to native binary disassembly and control-flow reconstruction.

---

## Engineering Notes & Design Invariants

Across my projects, I enforce a consistent set of engineering rules:

1. **Zero-Trace Revert**: Disabling an extension (`off` mode) physically deletes its keys from `settings.json` (`delete config.target`), leaving zero orphaned configuration keys.
2. **Platform Telemetry Authority**: Status bar and TUI hooks format extension badges via surgical micro-hooks without overwriting host token counters, git branch indicators, or cache hit telemetry.
3. **Unicode UAX #11 Width Determinism**: Dynamic text and multilingual strings never sit inside closed right-hand borders (`│ ... │`). Widths are computed cell-by-cell (`2` columns for CJK/emoji, `1` column for ASCII, `0` for stripped ANSI sequences) with cascading degradation to stay within host line limits.
4. **1:1 Physical Verification**: Every package ships with zero runtime dependencies or minimal locked primitives, dual ESM/CJS builds (`<90ms` cold start), OIDC trusted publishing, and test badges anchored `1:1` to physical test runner counts.

---

## Background & Technical Stack

- **Education**: B.Mgt. in Big Data Management and Application, Xidian University (`2024 - 2028 Expected`, `GPA 3.8/4.0`). Coursework includes Data Structures (`98`), Business Statistics, Analytics & Modeling (`98`), Accounting Analytics (`98`), Artificial Intelligence (`97`), C Programming (`93`), and Database Systems (`90`).
- **Languages & Runtimes**: TypeScript / Node.js, Python, C, SQL, C# / MinGW C (Win32 & UIA bridges).
- **Agent & Terminal Systems**: Pi Coding Agent SDK, TUI box-model layout solvers (Unicode UAX #11, Kinsoku Shori), AST-based tool sandboxing, context log dehydration.
- **Data, Vision & Retrieval**: PyTorch, OpenCV, RapidOCR (ONNX Runtime), SQLite FTS5, `sqlite-vec` (Reciprocal Rank Fusion), FastAPI, pandas, openpyxl, Power BI.
