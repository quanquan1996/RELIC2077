<div align="center">

```
██████╗ ███████╗██╗     ██╗ ██████╗██████╗  ██████╗ ███████╗███████╗
██╔══██╗██╔════╝██║     ██║██╔════╝╚════██╗██╔═══██╗╚════██║╚════██║
██████╔╝█████╗  ██║     ██║██║      █████╔╝██║   ██║    ██╔╝    ██╔╝
██╔══██╗██╔══╝  ██║     ██║██║     ██╔═══╝ ██║   ██║   ██╔╝    ██╔╝
██║  ██║███████╗███████╗██║╚██████╗███████╗╚██████╔╝   ██║     ██║
╚═╝  ╚═╝╚══════╝╚══════╝╚═╝ ╚═════╝╚══════╝ ╚═════╝    ╚═╝     ╚═╝
```

### *如果我告诉你……你脑子里那块芯片不只是数据，而是某个人的灵魂呢？*

**将任何人的思维蒸馏为结构化文件树。加载它。成为他们。**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](#-参与贡献)
![Platform](https://img.shields.io/badge/平台-OpenClaw%20%7C%20Claude%20Code%20%7C%20Codex%20%7C%20Cursor%20%7C%20OpenCode-blue)

[**English**](README.md) · [规范文档](docs/relic-spec.md) · [快速开始](#-快速开始)

</div>

---

## 🧬 什么是 Relic？

**Relic** 是一棵结构化文件树，编码一个人的六大维度本质——不需要向量数据库，不需要 RAG 管线。只是纯粹的 Markdown 文件，任何 AI 都能像翻书一样读取。

```
johnny-silverhand/
├── index.md              # 此人概览
├── identity.md           # 核心身份卡
├── manifest.json         # 机器可读元数据
├── mind/                 # 🧠 思维方式
├── voice/                # 🗣️ 表达方式
├── emotion/              # 💜 情感模式
├── knowledge/            # 📚 知识领域
├── relations/            # 🤝 社交关系
└── {custom}/             # ⚡ 弹性扩展
```

> AI 逐层加载 Relic——先读 `index.md`，再读各维度 `_index.md` 摘要，最后按需深入具体文件。上下文高效，永远不会爆窗口。

---

## ⚡ 六大维度

| 维度 | 目录 | 蒸馏内容 |
|:-:|:-:|---|
| 🧠 **思维** | `mind/` | 思维模式、价值观、世界观、认知盲区 |
| 🗣️ **表达** | `voice/` | 语言风格、口头禅、幽默方式、场景语域切换 |
| 💜 **情感** | `emotion/` | 性格气质、情绪触发点、应对模式 |
| 📚 **知识** | `knowledge/` | 专业领域、知识深度 |
| 🤝 **关系** | `relations/` | 社交风格、信任模式、群体动态 |
| ⚡ **自定义** | `{name}/` | 弹性扩展——任何定义此人的其他维度 |

---

## 🔮 两种蒸馏模式

### 💬 交互式蒸馏
AI 引导你进行结构化访谈，覆盖六大维度。边聊边写，Relic 在对话中逐步成型。

> *适合：蒸馏你自己，或正在与你对话的人。*

### ⚙️ 批量式蒸馏
指定一个目录——聊天记录、博客文章、代码仓库、随笔笔记——多 Agent 流水线自动并行提取。

```
编排器扫描文件
  → 5 个维度提取器并行运行
    → 合成器合并、校验、生成索引
      → 动态分裂处理超长文件
        → ✅ Relic 蒸馏完成
```

> *适合：从已有数据中蒸馏——文章、对话、仓库。*

---

## 🚀 快速开始

### 选择你的路径

<table>
<tr>
<td width="50%" valign="top">

#### 🔒 Clone — 隐私蒸馏

**你的 Relic 留在本地。没有任何数据离开你的机器。**

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
cd RELIC2077
```

- `relics/` 已在 `.gitignore` 中
- 蒸馏数据永远不会被 push
- 适合个人使用、保护隐私

> *你的思维，你的规则。*

</td>
<td width="50%" valign="top">

#### 🌐 Fork — 公开蒸馏

**把你的 Relic 分享给世界。让别人加载你。**

1. 在 GitHub 上点击 **Fork**
2. Clone 你 fork 的仓库
3. 蒸馏你的 Relic
4. Push 到你的 fork——你的 Relic 从此公开

```bash
git clone https://github.com/你的用户名/RELIC2077.git
cd RELIC2077
# ... 蒸馏 ...
git add relics/ && git commit -m "feat: my relic"
git push
```

> *将你的灵魂烧录进网络。*

</td>
</tr>
</table>

### 安装技能

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
# Claude Code 会自动检测 .claude-plugin/plugin.json
```
</details>

<details>
<summary><b>Codex</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# 参见 .codex/INSTALL.md 配置说明
```
</details>

<details>
<summary><b>Cursor</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# Cursor 会自动检测 .cursor-plugin/plugin.json
```
</details>

<details>
<summary><b>OpenCode</b></summary>

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
# 参见 .opencode/INSTALL.md 配置说明
```
</details>

### 开始使用

```
# 交互式——AI 引导你完成访谈
> "帮我蒸馏一个 Relic"

# 批量式——指向你的数据
> "从 ./my-writings/ 目录蒸馏 Relic"

# 加载——成为某人
> "加载 relics/johnny-silverhand/ 的 Relic"
```

---

## 📁 项目结构

```
RELIC2077/
├── skills/
│   ├── distill/          # 蒸馏技能（交互式 + 批量式）
│   │   ├── SKILL.md
│   │   └── references/   # 访谈框架、批量流水线、维度定义
│   └── load/             # 人格加载技能
│       └── SKILL.md
├── agents/               # 多 Agent 批量提取
│   ├── orchestrator.md   # 扫描、分配、协调
│   ├── mind-extractor.md
│   ├── voice-extractor.md
│   ├── emotion-extractor.md
│   ├── knowledge-extractor.md
│   ├── relations-extractor.md
│   └── synthesizer.md    # 合并、校验、生成索引
├── templates/            # 空白 Relic 文件树模板
├── docs/
│   └── relic-spec.md     # 完整 Relic 格式规范
├── relics/               # 🔒 你蒸馏的 Relic（已 gitignore）
└── examples/             # 示例 Relic
```

---

## 🤝 参与贡献

Relic 是私人的。框架是公共的。

- **发现 Bug？** 提 Issue。
- **改进了提取器？** 提 PR。
- **蒸馏了一个酷炫的 Relic？** Fork 仓库，push 到你自己的 fork，分享出去！
- **新维度灵感？** 来提案——`{custom}` 扩展槽就是为此而生。

---

## 📄 开源协议

[MIT](LICENSE) — 自由如自由。负责任地燃烧。🔥

---

<div align="center">

*醒醒吧，武士。我们有一个灵魂要燃烧。*

**[⬆ 回到顶部](#)**

</div>
