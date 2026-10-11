<h1 align="center">Jason Song (@3ZEROS12)</h1>

<p align="center">
  Systems &amp; AI Agent Infrastructure Builder<br>
  Designing low-overhead terminal runtimes, context dehydrators, and developer ergonomics for CLI coding agents.
</p>

<p align="center">
  <a href="https://www.npmjs.com/~jason-zeros">npm (~jason-zeros)</a> ·
  <a href="https://github.com/3ZEROS12/pi-lingual">pi-lingual</a> ·
  <a href="https://github.com/3ZEROS12/toolflow">toolflow</a> ·
  <a href="mailto:jiaxinsong312@gmail.com">Email</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white" alt="Node.js">
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/SQLite-003B57?style=flat-square&logo=sqlite&logoColor=white" alt="SQLite">
</p>

---

## 🛠️ Pi Terminal Suite (Published on npm)

Four composable extensions for [Pi Coding Agent](https://github.com/earendil-works/pi-coding-agent). Each package mounts to a separate terminal slot (`aboveEditor`, runtime tool hooks, `status-only` footer, and `belowEditor`) so all four run together with zero widget overlap:

| Package | Registry & Downloads | Terminal Slot & Core Mechanism | Verification |
| :--- | :--- | :--- | :--- |
| **[`pi-lingual`](https://github.com/3ZEROS12/pi-lingual)** | [![npm](https://img.shields.io/npm/v/pi-lingual?color=blue&label=npm)](https://www.npmjs.com/package/pi-lingual) [![downloads](https://img.shields.io/npm/dm/pi-lingual?color=22c55e&label=downloads)](https://www.npmjs.com/package/pi-lingual) | **`aboveEditor` UAX #11 Tree HUD & Prompt Transformer** — Dual-register (`[Spoken]` / `[Written]`) overlay (≤9 lines) and native-to-English prompt rewriting with 0 chat-history token injection and 50-entry LRU cache. | `93/93` tests pass |
| **[`toolflow`](https://github.com/3ZEROS12/toolflow)** | [![npm](https://img.shields.io/npm/v/toolflow?color=blue&label=npm)](https://www.npmjs.com/package/toolflow) [![downloads](https://img.shields.io/npm/dm/toolflow?color=22c55e&label=downloads)](https://www.npmjs.com/package/toolflow) | **Runtime Tool Sandboxing & `-95%` Log Dehydration** — Stage-gates heavy MCP schemas while keeping core tools persistent; intercepts verbose outputs (`>40` lines) to disk and guards `.env*`/`.git*` from destructive writes. | `26/26` suites pass |
| **[`pi-tui-status-beautifier`](https://github.com/3ZEROS12/pi-tui-status-beautifier)** | [![npm](https://img.shields.io/npm/v/pi-tui-status-beautifier?color=blue&label=npm)](https://www.npmjs.com/package/pi-tui-status-beautifier) [![downloads](https://img.shields.io/npm/dm/pi-tui-status-beautifier?color=22c55e&label=downloads)](https://www.npmjs.com/package/pi-tui-status-beautifier) | **`status-only` Badge Folding & 0-I/O Footer Engine** — Normalizes extension status strings across 6 presets without replacing native telemetry; folds idle badges `(+N idle)` on `<80`-col panes with 0 render-loop disk reads. | `18/18` tests pass |
| **[`pi-anchor`](https://github.com/3ZEROS12/anchor)** | [![npm](https://img.shields.io/npm/v/pi-anchor?color=blue&label=npm)](https://www.npmjs.com/package/pi-anchor) [![downloads](https://img.shields.io/npm/dm/pi-anchor?color=22c55e&label=downloads)](https://www.npmjs.com/package/pi-anchor) | **`0ms` `belowEditor` Sticky Notes & Session Jump** — Intercepts `pin:` notes in `0ms` without model calls; renders `[■■□□]` step bars, bookmarks `.jsonl` session files (`↪`), and auto-archives on `git commit`. | `25/25` assertions pass |

```bash
pi install npm:pi-lingual
pi install npm:toolflow
pi install npm:pi-tui-status-beautifier
pi install npm:pi-anchor
```

---

## 📦 Systems Research & Prototypes

### [Gabriel](https://github.com/3ZEROS12/Gabriel) `[Archived Prototype]`
**Zero-Intrusion Desktop GUI Sidecar & Local Hybrid Search Sandbox for CLI AI Agents**

* Built as a desktop sidecar to monitor autonomous CLI agent trajectories in the background; later archived as those workflows moved directly into in-terminal primitives (`pi-anchor` and `toolflow`).
* **Architecture & Verification**: Passive CLI transcript parsers (Claude Code, Cursor, Antigravity), dual-track Reciprocal Rank Fusion (SQLite FTS5 + `sqlite-vec`), and 39 automated unit/integration tests (`pytest`).

### [Digit Recognition FastAPI](https://github.com/3ZEROS12/digit-recognition-fastapi)
**Computer Vision Preprocessing & Async Inference Pipeline**

* End-to-end inference service combining a PyTorch CNN trained on MNIST, OpenCV preprocessing (contour extraction, deskewing, red-channel stamp removal), and asynchronous FastAPI endpoints.

---

## 🧭 Technical Focus

```text
Languages & Runtimes    TypeScript / Node.js, Python, SQL, C/C++
Agent Infrastructure    TUI layout engines (UAX #11), MCP sandboxing, context dehydration, CLI telemetry
Data & Search Systems   SQLite FTS5, sqlite-vec (RRF hybrid retrieval), PyTorch, OpenCV
Engineering Standards   Zero-dependency runtime design, deterministic test suites, strict TypeScript
```

## 📬 Contact

- **GitHub**: [@3ZEROS12](https://github.com/3ZEROS12)
- **npm**: [~jason-zeros](https://www.npmjs.com/~jason-zeros)
- **Email**: [jiaxinsong312@gmail.com](mailto:jiaxinsong312@gmail.com)
