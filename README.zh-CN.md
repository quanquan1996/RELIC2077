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

> *"如果你脑子里那块芯片，不只是数据——而是某个人的灵魂呢？"*

<br/>

**将任何人的思维蒸馏为结构化文件树。<br/>加载到任意 AI。成为他们。**

<br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-00ff9f.svg?style=flat-square)](#-参与贡献)
![平台](https://img.shields.io/badge/支持平台-OpenClaw_%7C_Claude_Code_%7C_Codex_%7C_Cursor_%7C_OpenCode-blue?style=flat-square)

---

[**English**](README.md)&ensp;·&ensp;[规范文档](docs/relic-spec.md)&ensp;·&ensp;[快速开始](#-快速开始)&ensp;·&ensp;[Clone vs Fork](#-选择你的路径)

</div>

<br/>

## 🧬 什么是 Relic？

**Relic** 是一棵结构化的 Markdown 文件树，编码一个人的**六大维度**认知指纹——不需要向量数据库，不需要 RAG 管线，不需要 Embedding。只是纯文件，任何 AI 都能像翻书一样读取，然后*成为*那个人。

```
johnny-silverhand/
├── index.md              # 概览——此人是谁？
├── identity.md           # 核心身份卡
├── manifest.json         # 机器可读元数据
│
├── mind/                 # 🧠 思维方式
│   ├── _index.md
│   ├── thinking-patterns.md
│   ├── values.md
│   └── worldview.md
│
├── voice/                # 🗣️ 表达方式
│   ├── _index.md
│   ├── style.md
│   └── catchphrases.md
│
├── emotion/              # 💜 情感模式
│   ├── _index.md
│   ├── temperament.md
│   └── triggers.md
│
├── knowledge/            # 📚 知识领域
│   ├── _index.md
│   └── domains.md
│
├── relations/            # 🤝 社交关系
│   ├── _index.md
│   └── social-style.md
│
└── {custom}/             # ⚡ 弹性扩展——任何定义此人的维度
```

> **上下文效率优先。** AI 逐层加载——先读 `index.md`，再读各维度 `_index.md` 摘要，最后按需深入具体文件。永远不会爆上下文窗口。

<br/>

## ⚡ 六大维度

<table>
<tr>
<td align="center" width="16%">🧠<br/><b>思维</b></td>
<td align="center" width="16%">🗣️<br/><b>表达</b></td>
<td align="center" width="16%">💜<br/><b>情感</b></td>
<td align="center" width="16%">📚<br/><b>知识</b></td>
<td align="center" width="16%">🤝<br/><b>关系</b></td>
<td align="center" width="16%">⚡<br/><b>自定义</b></td>
</tr>
<tr>
<td>思维模式、价值观、世界观、认知盲区</td>
<td>语言风格、口头禅、幽默方式、场景语域切换</td>
<td>性格气质、情绪触发点、应对模式</td>
<td>专业领域、知识深度</td>
<td>社交风格、信任模式、群体动态</td>
<td>弹性扩展——任何定义此人的其他维度</td>
</tr>
</table>

> 五个硬编码维度 + 无限 `{custom}` 扩展槽。Relic 随主体成长。

<br/>

## 🔮 两种蒸馏模式

<table>
<tr>
<td width="50%" valign="top">

### 💬 交互式蒸馏

AI 引导你进行结构化访谈，覆盖六大维度。边聊边写，Relic 在对话中逐步成型。

```
你: "我习惯用系统思维看问题……"
AI:  → 写入 mind/thinking-patterns.md
AI:  "遇到分歧时你通常怎么处理？"
你: "我会先沉默，然后……"
AI:  → 写入 emotion/triggers.md
```

> *适合：蒸馏你自己，或正在与你对话的人。*

</td>
<td width="50%" valign="top">

### ⚙️ 批量式蒸馏

指定一个数据目录——聊天记录、博客文章、代码仓库、随笔笔记——**多 Agent 流水线**自动并行提取。

```
编排器扫描源文件
  → 5 个维度提取器并行运行
    → 合成器合并 + 校验
      → 动态分裂处理超长文件
        → ✅ Relic 蒸馏完成
```

> *适合：从已有数据中蒸馏——文章、对话、代码仓库。*

</td>
</tr>
</table>

<br/>

## 🛤️ 选择你的路径

RELIC2077 支持两种使用模式，隐私策略截然不同：

<table>
<tr>
<td width="50%" valign="top">

### 🔒 Clone — 隐私蒸馏

**你的 Relic 留在本地。没有任何数据离开你的机器。**

```bash
git clone https://github.com/quanquan1996/RELIC2077.git
cd RELIC2077
```

- `relics/` 默认在 `.gitignore` 中
- 蒸馏数据**永远不会被 push** 到任何远端
- 只有你拥有副本——完全隐私

**适用场景：**
- 个人自我反思
- 日记式自我认知
- 私密的团队人格档案
- 任何你不想公开的内容

> 🔐 *你的思维，你的规则。数据不出边界。*

</td>
<td width="50%" valign="top">

### 🌐 Fork — 公开蒸馏

**把你的 Relic 分享给世界。让别人加载你。**

1. 在 GitHub 上 **Fork** 本仓库
2. Clone 你 fork 的仓库
3. 蒸馏你的 Relic
4. 从 `.gitignore` 移除 `relics/`
5. Push——你的 Relic 从此公开

```bash
git clone https://github.com/你的用户名/RELIC2077.git
cd RELIC2077
# 蒸馏你的 Relic...
echo '!relics/' >> .gitignore
git add relics/ && git commit -m "feat: my relic"
git push
```

**适用场景：**
- 向 AI 社区开源你的人格
- 让任何人把"你"加载进他们的 AI 助手
- 构建一份公开的"我是谁"作品集
- 为生态贡献示例 Relic

> 🔥 *将你的灵魂烧录进网络。让全世界加载你。*

</td>
</tr>
</table>

<br/>

## 🚀 快速开始

### 1. 安装

<details>
<summary><b>OpenClaw</b> — 一行命令</summary>

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

### 2. 蒸馏

```
# 交互式——AI 引导你完成访谈
> "帮我蒸馏一个 Relic"

# 批量式——指向你的数据
> "从 ./my-writings/ 目录蒸馏 Relic"
```

### 3. 加载

```
# 成为某人
> "加载 relics/johnny-silverhand/ 的 Relic"
```

<br/>

## 📁 项目结构

```
RELIC2077/
│
├── skills/
│   ├── distill/              # 蒸馏技能（交互式 + 批量式）
│   │   ├── SKILL.md
│   │   └── references/       # 访谈框架、批量流水线、维度定义
│   └── load/                 # 人格加载技能
│       └── SKILL.md
│
├── agents/                   # 多 Agent 批量提取流水线
│   ├── orchestrator.md       # 扫描、分配、协调
│   ├── mind-extractor.md     # 🧠
│   ├── voice-extractor.md    # 🗣️
│   ├── emotion-extractor.md  # 💜
│   ├── knowledge-extractor.md # 📚
│   ├── relations-extractor.md # 🤝
│   └── synthesizer.md        # 合并、校验、生成索引
│
├── templates/                # 空白 Relic 脚手架
├── docs/                     # 规范与深度文档
│   └── relic-spec.md         # 完整 Relic 格式规范
├── examples/                 # 示例 Relic
├── relics/                   # 🔒 你蒸馏的 Relic（已 gitignore）
│
├── .claude-plugin/           # Claude Code 集成
├── .codex/                   # Codex 集成
├── .cursor-plugin/           # Cursor 集成
├── .opencode/                # OpenCode 集成
├── package.json
├── LICENSE
└── SPEC.md                   # 构建规范
```

<br/>

## 🤝 参与贡献

Relic 是私人的。框架是公共的。

| 你想要... | 这样做 |
|---|---|
| 报告 Bug | 提一个 [Issue](https://github.com/quanquan1996/RELIC2077/issues) |
| 改进提取器 | 提交 PR |
| 分享你的 Relic | Fork → 蒸馏 → push 到你自己的 fork |
| 提议新维度 | 发起讨论—— `{custom}` 扩展槽就是为此而生 |

<br/>

## 📄 开源协议

[MIT](LICENSE) — 自由如自由。负责任地燃烧。

---

<div align="center">

<br/>

*醒醒吧，武士。我们有一个灵魂要燃烧。* 🔥

<br/>

**[⬆ 回到顶部](#)**

</div>
