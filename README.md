<div align="center">

<img src="https://img.shields.io/badge/%E2%96%88%E2%96%88%E2%96%88-RELIC2077-ff003c?style=for-the-badge&labelColor=0d0d0d" alt="RELIC2077" />

```
██████╗ ███████╗██╗     ██╗ ██████╗██████╗  ██████╗ ███████╗███████╗
██╔══██╗██╔════╝██║     ██║██╔════╝╚════██╗██╔═══██╗╚════██║╚════██║
██████╔╝█████╗  ██║     ██║██║      █████╔╝██║   ██║    ██╔╝    ██╔╝
██╔══██╗██╔══╝  ██║     ██║██║     ██╔═══╝ ██║   ██║   ██╔╝    ██╔╝
██║  ██║███████╗███████╗██║╚██████╗███████╗╚██████╔╝   ██║     ██║
╚═╝  ╚═╝╚══════╝╚══════╝╚═╝ ╚═════╝╚══════╝ ╚═════╝    ╚═╝     ╚═╝
```

<br/>

> *"What if that chip in your head isn't just data — it's someone's soul?"*

<br/>

**Distill any human mind into a structured file tree.<br/>Load it into any AI. Become them.**

<br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-00ff9f.svg?style=flat-square)](#-contributing)
![Platform](https://img.shields.io/badge/Works_With-OpenClaw_%7C_Claude_Code_%7C_Codex_%7C_Cursor_%7C_OpenCode-blue?style=flat-square)

---

[**中文文档**](README.zh-CN.md)&ensp;·&ensp;[Spec](docs/relic-spec.md)&ensp;·&ensp;[Quick Start](#-quick-start)&ensp;·&ensp;[Clone vs Fork](#-choose-your-path)

</div>

<br/>

## 🧬 What Is a Relic?

A **Relic** is a structured Markdown file tree that encodes a person's cognitive fingerprint across **six dimensions** — no vector databases, no RAG pipelines, no embeddings. Just files that any AI can read like a book and *become* that person.

```
johnny-silverhand/
├── index.md              # Overview — who is this person?
├── identity.md           # Core identity card
├── manifest.json         # Machine-readable metadata
│
├── mind/                 # 🧠 How they think
│   ├── _index.md
│   ├── thinking-patterns.md
│   ├── values.md
│   └── worldview.md
│
├── voice/                # 🗣️ How they speak
│   ├── _index.md
│   ├── style.md
│   └── catchphrases.md
│
├── emotion/              # 💜 How they feel
│   ├── _index.md
│   ├── temperament.md
│   └── triggers.md
│
├── knowledge/            # 📚 What they know
│   ├── _index.md
│   └── domains.md
│
├── relations/            # 🤝 How they connect
│   ├── _index.md
│   └── social-style.md
│
└── {custom}/             # ⚡ Anything else that defines them
```

> **Context-efficient by design.** AI loads layer by layer — `index.md` → dimension `_index.md` summaries → deep files on demand. Never blows up the context window.

<br/>

## ⚡ The Six Dimensions

<table>
<tr>
<td align="center" width="16%">🧠<br/><b>Mind</b></td>
<td align="center" width="16%">🗣️<br/><b>Voice</b></td>
<td align="center" width="16%">💜<br/><b>Emotion</b></td>
<td align="center" width="16%">📚<br/><b>Knowledge</b></td>
<td align="center" width="16%">🤝<br/><b>Relations</b></td>
<td align="center" width="16%">⚡<br/><b>Custom</b></td>
</tr>
<tr>
<td>Thinking patterns, values, worldview, blind spots</td>
<td>Language style, catchphrases, humor, register shifts</td>
<td>Temperament, triggers, coping patterns</td>
<td>Expert domains, depth of knowledge</td>
<td>Social style, trust patterns, group dynamics</td>
<td>Elastic — anything else that defines them</td>
</tr>
</table>

> Five hard-coded dimensions + unlimited `{custom}` slots. A Relic grows with its subject.

<br/>

## 🔮 Two Modes of Distillation

<table>
<tr>
<td width="50%" valign="top">

### 💬 Interactive Mode

The AI interviews you — a structured conversation across all six dimensions. It writes the Relic as you talk.

```
You: "I tend to think in systems..."
AI:  → writes mind/thinking-patterns.md
AI:  "How do you handle disagreements?"
You: "I go quiet first, then..."
AI:  → writes emotion/triggers.md
```

> *Best for: distilling yourself, or someone you're interviewing live.*

</td>
<td width="50%" valign="top">

### ⚙️ Batch Mode

Point at a directory of existing data — chat logs, blog posts, code repos, notes — and a **multi-agent pipeline** extracts the Relic automatically.

```
Orchestrator scans source files
  → 5 Dimension Extractors run in parallel
    → Synthesizer merges + validates
      → Dynamic fission splits oversized files
        → ✅ Relic complete
```

> *Best for: distilling from existing data — writings, conversations, repos.*

</td>
</tr>
</table>

<br/>

## 🛤️ Choose Your Path

RELIC2077 supports two usage patterns with fundamentally different privacy models:

<table>
<tr>
<td width="50%" valign="top">

### 🔒 Clone — Private Distillation

**Your Relic stays local. Nothing leaves your machine.**

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
cd RELIC2077
```

- `relics/` is in `.gitignore` by default
- Distilled data is **never pushed** to any remote
- You own the only copy — full privacy

**When to Clone:**
- Personal self-reflection
- Journaling & self-understanding
- Private team personality profiles
- Anything you wouldn't share publicly

> 🔐 *Your mind, your rules. No data leaves the perimeter.*

</td>
<td width="50%" valign="top">

### 🌐 Fork — Open Distillation

**Share your Relic with the world. Let others load you.**

1. **Fork** this repo on GitHub
2. Clone your fork locally
3. Distill your Relic
4. Remove `relics/` from `.gitignore`
5. Push — your Relic is now public

```bash
git clone https://github.com/YOUR_NAME/RELIC2077.git
cd RELIC2077
# distill your relic...
echo '!relics/' >> .gitignore
git add relics/ && git commit -m "feat: my relic"
git push
```

**When to Fork:**
- Open-source your personality for AI communities
- Let anyone "load" you into their AI assistant
- Build a public portfolio of who you are
- Contribute example Relics to the ecosystem

> 🔥 *Burn your soul into the network. Let the world load you.*

</td>
</tr>
</table>

<br/>

## 🚀 Quick Start

### 1. Install

<details>
<summary><b>OpenClaw</b> — one command</summary>

```bash
openclaw skill install relic2077
```
</details>

<details>
<summary><b>Claude Code</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# Claude Code auto-detects .claude-plugin/plugin.json
```
</details>

<details>
<summary><b>Codex</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# See .codex/INSTALL.md for setup
```
</details>

<details>
<summary><b>Cursor</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# Cursor auto-detects .cursor-plugin/plugin.json
```
</details>

<details>
<summary><b>OpenCode</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# See .opencode/INSTALL.md for setup
```
</details>

### 2. Distill

```
# Interactive — AI interviews you
> "Distill a relic for me"

# Batch — point at your data
> "Distill a relic from ./my-writings/"
```

### 3. Load

```
# Become someone
> "Load the relic at relics/johnny-silverhand/"
```

<br/>

## 📁 Project Structure

```
RELIC2077/
│
├── skills/
│   ├── distill/              # Distillation skill (interactive + batch)
│   │   ├── SKILL.md
│   │   └── references/       # Interview framework, batch pipeline, dimension defs
│   └── load/                 # Persona activation skill
│       └── SKILL.md
│
├── agents/                   # Multi-agent batch extraction pipeline
│   ├── orchestrator.md       # Scans, assigns, coordinates
│   ├── mind-extractor.md     # 🧠
│   ├── voice-extractor.md    # 🗣️
│   ├── emotion-extractor.md  # 💜
│   ├── knowledge-extractor.md # 📚
│   ├── relations-extractor.md # 🤝
│   └── synthesizer.md        # Merges, validates, generates index
│
├── templates/                # Blank Relic scaffolding
├── docs/                     # Specification & deep docs
│   └── relic-spec.md         # Full Relic format specification
├── examples/                 # Example Relics
├── relics/                   # 🔒 Your distilled Relics (gitignored)
│
├── .claude-plugin/           # Claude Code integration
├── .codex/                   # Codex integration
├── .cursor-plugin/           # Cursor integration
├── .opencode/                # OpenCode integration
├── package.json
├── LICENSE
└── SPEC.md                   # Build specification
```

<br/>

## 🤝 Contributing

Relics are personal. The framework is communal.

| Want to... | Do this |
|---|---|
| Report a bug | Open an [Issue](https://github.com/quanquan1996/RELIC2077/issues) |
| Improve an extractor | Submit a PR |
| Share your Relic | Fork → distill → push to your fork |
| Propose a new dimension | Open a discussion — the `{custom}` slot exists for a reason |

<br/>

## 📄 License

[MIT](LICENSE) — Free as in freedom. Burn responsibly.

---

<div align="center">

<br/>

*Wake up, Samurai. We have a soul to burn.* 🔥

<br/>

**[⬆ Back to Top](#)**

</div>
