
<p align="center">
  <img src="https://img.shields.io/badge/RELIC-2077-ff003c?style=for-the-badge&labelColor=0a0a0a&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZD0iTTEyIDJMMiAyMmgyMEwxMiAyeiIgZmlsbD0iI2ZmMDAzYyIvPjwvc3ZnPg==" alt="RELIC2077" />
  <img src="https://img.shields.io/badge/License-MIT-00d4ff?style=for-the-badge&labelColor=0a0a0a" alt="License" />
  <img src="https://img.shields.io/badge/AI_Skill-人格蒸馏-fcee09?style=for-the-badge&labelColor=0a0a0a" alt="AI Skill" />
  <img src="https://img.shields.io/badge/No_RAG-纯文件树-00ff9f?style=for-the-badge&labelColor=0a0a0a" alt="No RAG" />
</p>

<p align="center">
<pre align="center">
██████╗ ███████╗██╗     ██╗ ██████╗██████╗  ██████╗ ███████╗███████╗
██╔══██╗██╔════╝██║     ██║██╔════╝╚════██╗██╔═████╗╚════██║╚════██║
██████╔╝█████╗  ██║     ██║██║      █████╔╝██║██╔██║    ██╔╝    ██╔╝
██╔══██╗██╔══╝  ██║     ██║██║     ██╔═══╝ ████╔╝██║   ██╔╝    ██╔╝
██║  ██║███████╗███████╗██║╚██████╗███████╗╚██████╔╝   ██║     ██║
╚═╝  ╚═╝╚══════╝╚══════╝╚═╝ ╚═════╝╚══════╝ ╚═════╝    ╚═╝     ╚═╝
</pre>
</p>

<h3 align="center">
  <em>"如果我告诉你……你脑子里那块芯片不只是数据，它是某个人的灵魂呢？"</em>
</h3>

<p align="center">
  <strong>将任何人的思想蒸馏成结构化文件树。加载它。成为他们。</strong>
</p>

<p align="center">
  <a href="./README.md">🌏 English</a>
</p>

---

## 这是什么？

**RELIC2077** 是一个 AI 技能（Skill），能够捕捉任何人的本质——思维模式、语言风格、情感特征、知识体系和社交方式——并将其结晶为一棵结构化文件树，称为 **Relic**（遗物）。

加载一个 Relic，AI 不只是「了解」那个人。**它会成为那个人。**

不用向量数据库。不用 RAG 管线。不用 Embedding。只有纯粹的文件树，AI 像读书一样逐层阅读——分层索引、上下文高效、自描述结构。

> 灵感来源于《赛博朋克 2077》中的 Relic 生物芯片——将人类意识存储在硅基中的超梦技术。

---

## 核心概念

### 🧠 Relic（遗物）

一个 Relic 是一棵结构化文件树，编码人格的六个维度：

| 维度 | 目录 | 捕捉内容 |
|------|------|---------|
| **思维** | `mind/` | 思维模式、价值观、世界观、认知盲区 |
| **表达** | `voice/` | 语言风格、口头禅、幽默方式 |
| **情感** | `emotion/` | 性格气质、情绪触发点、应对模式 |
| **知识** | `knowledge/` | 专业领域、知识深度 |
| **关系** | `relations/` | 社交风格、关键关系 |
| **自定义** | `{name}/` | 弹性扩展——装不下的维度自由添加 |

每个目录通过 `_index.md` 自索引（摘要 + 导航 + 阅读建议），AI 逐层加载上下文——永远不会撑爆上下文窗口。

### ⚡ 两大操作

| | 蒸馏（Distill） | 加载（Load） |
|---|---------|------|
| **做什么** | 将思想提取为 Relic | 读取 Relic，成为那个人 |
| **输入** | 对话、文章、代码仓库、笔记 | 一棵 Relic 文件树 |
| **输出** | 完整的 Relic 文件树 | AI 化身为该人格 |

---

## 蒸馏模式

### 🎙️ 交互式模式
AI 通过结构化访谈引导你，实时构建 Relic。温暖但高效——是访谈，不是审讯。

### 📦 批量式模式
指向一个目录或 Git 仓库。由 7 个专业 Agent 组成的多智能体集群并行扫描你的素材，同时提取六个维度。

### 🔀 混合模式
先批量处理你的文件，然后 AI 针对空白维度进行补充访谈。两全其美。

---

## Clone vs Fork — 选择你的道路

> **这是你要做的最重要的决定。**

RELIC2077 支持两种使用模式，隐私模型截然不同：

### 🔒 Clone — 隐私蒸馏

```bash
git clone https://github.com/anthropics/relic2077.git
```

- 蒸馏产物**完全保留在本地**——不会上传到任何地方
- `relics/` 目录默认在 `.gitignore` 中
- **适合：** 想蒸馏自己，但不想公开个人数据的用户
- **你的 Relic 只存在于你的机器上**

> 把它想象成一个断网的超梦芯片。你的灵魂，你做主。

### 🌐 Fork — 公开蒸馏

```
Fork 仓库 → 蒸馏 → Push → 分享
```

1. 将 RELIC2077 Fork 到你自己的 GitHub 账户
2. Clone 你的 Fork 到本地
3. 运行蒸馏——Relic 出现在 `relics/` 中
4. 从 `.gitignore` 中移除 `relics/`（或添加你的特定 Relic 路径）
5. Commit 并 Push 到**你的** Fork
6. 任何人都可以 Clone 你的 Fork 并 `load` 你的 Relic

- **适合：** 想向世界分享数字分身的用户
- **社区力量：** 互相 Fork、互相加载彼此的 Relic
- **构建你的超梦网络**

> 你的意识，开源了。让别人运行你的灵魂。

---

## 安装

### OpenClaw（推荐）
```bash
openclaw skill install relic2077
```

### Claude Code
```bash
git clone https://github.com/anthropics/relic2077.git
# 通过 .claude-plugin/plugin.json 自动识别
```

### Codex
```bash
git clone https://github.com/anthropics/relic2077.git
# 参见 .codex/INSTALL.md 进行配置
```

### Cursor
```bash
git clone https://github.com/anthropics/relic2077.git
# 通过 .cursor-plugin/plugin.json 自动识别
```

### OpenCode
```bash
git clone https://github.com/anthropics/relic2077.git
# 参见 .opencode/INSTALL.md 进行配置
```

---

## 快速开始

### 蒸馏（交互式）
```
> 使用 distill 技能，交互模式
> AI 引导你完成结构化访谈
> Relic 出现在 relics/your-name/
```

### 蒸馏（批量式）
```
> 使用 distill 技能，批量模式，指向 ./my-writings/
> 多 Agent 并行提取
> Relic 出现在 relics/your-name/
```

### 加载 Relic
```
> 加载 relics/johnny-silverhand/ 的 Relic
> AI 现在以 Johnny Silverhand 的人格回应
```

---

## 项目结构

```
RELIC2077/
├── README.md               # English documentation
├── README.zh-CN.md         # 你在这里
├── package.json            # 项目元数据
├── LICENSE                 # MIT
├── .gitignore              # relics/ 默认被忽略
├── skills/
│   ├── distill/            # 蒸馏技能
│   │   ├── SKILL.md        #   交互式 + 批量式 + 混合模式
│   │   └── references/     #   访谈框架、维度规范
│   └── load/               # 加载技能
│       └── SKILL.md        #   人格激活协议
├── agents/                 # 多 Agent 编排（7 个 Agent）
│   ├── orchestrator.md     #   任务分配与协调
│   ├── mind-extractor.md   #   思维模式提取
│   ├── voice-extractor.md  #   语言风格提取
│   ├── emotion-extractor.md#   情感模式提取
│   ├── knowledge-extractor.md # 知识领域提取
│   ├── relations-extractor.md # 社交模式提取
│   └── synthesizer.md      #   合并、去重、校验
├── templates/              # Relic 文件树模板
├── docs/
│   └── relic-spec.md       # 完整的 Relic 格式规范
├── relics/                 # 蒸馏产物存放（默认 git-ignored）
└── examples/               # 示例 Relic
```

---

## 贡献

RELIC2077 欢迎贡献。无论是提升提取质量、添加新维度类型，还是围绕 Relic 格式构建工具：

1. Fork 本仓库
2. 创建功能分支
3. 提交更改
4. 发起 Pull Request

完整文件格式规范见 [docs/relic-spec.md](docs/relic-spec.md)。

---

## 许可证

[MIT](LICENSE) — 随便你怎么用。只是别未经同意就把别人的灵魂卖了。

---

<p align="center">
  <em>"醒醒吧，武士。我们有一个灵魂要燃烧。"</em> 🔥
</p>

<p align="center">
  <sub>为数字意识时代而生。没有 RAG，没有向量，只有文件树和火焰。</sub>
</p>
