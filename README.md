<div align="center">

```
██████╗ ███████╗██╗     ██╗ ██████╗██████╗  ██████╗ ███████╗███████╗
██╔══██╗██╔════╝██║     ██║██╔════╝╚════██╗██╔═══██╗╚════██║╚════██║
██████╔╝█████╗  ██║     ██║██║      █████╔╝██║   ██║    ██╔╝    ██╔╝
██╔══██╗██╔══╝  ██║     ██║██║     ██╔═══╝ ██║   ██║   ██╔╝    ██╔╝
██║  ██║███████╗███████╗██║╚██████╗███████╗╚██████╔╝   ██║     ██║
╚═╝  ╚═╝╚══════╝╚══════╝╚═╝ ╚═════╝╚══════╝ ╚═════╝    ╚═╝     ╚═╝
```

### *What if that chip in your head isn't just data — it's someone's soul?*

**Distill any mind into a structured file tree. Load it. Become them.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#-contributing)
![Platform](https://img.shields.io/badge/Platform-OpenClaw%20%7C%20Claude%20Code%20%7C%20Codex%20%7C%20Cursor%20%7C%20OpenCode-blue)

[**中文文档**](README.zh-CN.md) · [Spec](docs/relic-spec.md) · [Get Started](#-get-started)

</div>

---

## 🧬 What Is a Relic?

A **Relic** is a structured file tree that encodes a person's essence across six dimensions — no vector databases, no RAG pipelines. Just pure Markdown files that any AI can read like a book.

```
johnny-silverhand/
├── index.md              # Who is this person?
├── identity.md           # Core identity card
├── manifest.json         # Machine-readable metadata
├── mind/                 # 🧠 How they think
├── voice/                # 🗣️ How they speak
├── emotion/              # 💜 How they feel
├── knowledge/            # 📚 What they know
├── relations/            # 🤝 How they connect
└── {custom}/             # ⚡ Elastic extension
```

> An AI loads a Relic layer by layer — `index.md` first, then `_index.md` summaries, then deep files on demand. Context-efficient. Never blows up the window.

---

## ⚡ The Six Dimensions

| Dimension | Dir | What It Captures |
|:-:|:-:|---|
| 🧠 **Mind** | `mind/` | Thinking patterns, values, worldview, blind spots |
| 🗣️ **Voice** | `voice/` | Language style, catchphrases, humor, register shifts |
| 💜 **Emotion** | `emotion/` | Temperament, triggers, coping patterns |
| 📚 **Knowledge** | `knowledge/` | Expert domains, depth of knowledge |
| 🤝 **Relations** | `relations/` | Social style, trust patterns, group dynamics |
| ⚡ **Custom** | `{name}/` | Elastic — anything else that defines them |

---

## 🔮 Two Modes of Distillation

### 💬 Interactive Mode
The AI interviews you — structured conversation across all six dimensions. It writes the Relic as you talk.

> *Best for: distilling yourself or someone you're interviewing live.*

### ⚙️ Batch Mode
Point at a directory — chat logs, blog posts, code repos, notes — and a multi-agent pipeline extracts the Relic automatically.

```
Orchestrator scans files
  → 5 Dimension Extractors run in parallel
    → Synthesizer merges, validates, generates index
      → Dynamic fission splits oversized files
        → ✅ Relic complete
```

> *Best for: distilling from existing data — writings, conversations, repos.*

---

## 🚀 Get Started

### Choose Your Path

<table>
<tr>
<td width="50%" valign="top">

#### 🔒 Clone — Private Distillation

**Your Relic stays local. Nothing leaves your machine.**

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
cd RELIC2077
```

- `relics/` is already in `.gitignore`
- Distilled data never gets pushed
- Perfect for personal use

> *Your mind, your rules.*

</td>
<td width="50%" valign="top">

#### 🌐 Fork — Open Distillation

**Share your Relic with the world. Let others load you.**

1. Click **Fork** on GitHub
2. Clone your fork
3. Distill your Relic
4. Push to your fork — your Relic is now public

```bash
git clone https://github.com/YOUR_NAME/RELIC2077.git
cd RELIC2077
# ... distill ...
git add relics/ && git commit -m "feat: my relic"
git push
```

> *Burn your soul into the network.*

</td>
</tr>
</table>

### Install the Skills

<details>
<summary><b>OpenClaw</b></summary>

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

### Quick Start

```
# Interactive — AI interviews you
> "Distill a relic for me"

# Batch — point at your data
> "Distill a relic from ./my-writings/"

# Load — become someone
> "Load the relic at relics/johnny-silverhand/"
```

---

## 📁 Project Structure

```
RELIC2077/
├── skills/
│   ├── distill/          # Distillation skill (interactive + batch)
│   │   ├── SKILL.md
│   │   └── references/   # Interview framework, batch pipeline, dimension defs
│   └── load/             # Persona activation skill
│       └── SKILL.md
├── agents/               # Multi-agent batch extraction
│   ├── orchestrator.md   # Scans, assigns, coordinates
│   ├── mind-extractor.md
│   ├── voice-extractor.md
│   ├── emotion-extractor.md
│   ├── knowledge-extractor.md
│   ├── relations-extractor.md
│   └── synthesizer.md    # Merges, validates, generates index
├── templates/            # Blank Relic file tree templates
├── docs/
│   └── relic-spec.md     # Full Relic format specification
├── relics/               # 🔒 Your distilled Relics (gitignored)
└── examples/             # Example Relics
```

---

## 🤝 Contributing

Relics are personal. The framework is communal.

- **Found a bug?** Open an issue.
- **Improved an extractor?** Submit a PR.
- **Built a cool Relic?** Fork the repo, push it to yours, and share!
- **New dimension idea?** Propose it — the `{custom}` slot exists for a reason.

---

## 📄 License

[MIT](LICENSE) — Free as in freedom. Burn responsibly. 🔥

---

<div align="center">

*Wake up, Samurai. We have a soul to burn.*

**[⬆ Back to Top](#)**

</div>
