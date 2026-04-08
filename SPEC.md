# RELIC2077 — Build Spec

## 项目概述
RELIC2077 是一个 AI Skill，能将任何人的思想、性格、知识蒸馏成结构化的文件树（Relic），也能加载 Relic 让 AI "变成"那个人。灵感来自赛博朋克2077的 Relic 芯片。

## 核心架构

### 文件树 = 知识库
- 不用 RAG/向量数据库，用纯文件树
- 目录结构即索引，`_index.md` 即摘要
- 动态分裂：单文件 > 2000字自动拆分为子目录 + `_index.md`
- AI 按需逐层读取，永远不会爆上下文窗口

### 两大功能
1. **Distill（蒸馏）** — 输入素材 → 输出 Relic 文件树
2. **Load（加载）** — 读取 Relic → AI 扮演该人格

### 两种蒸馏模式
1. **交互式** — AI 引导用户回答问题，逐步构建 Relic
2. **批量式** — 用户指定目录/Git仓库，多 Agent 并行提取

## 目标目录结构

```
RELIC2077/
├── README.md
├── package.json
├── LICENSE
├── skills/
│   ├── distill/
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── interview.md
│   │       ├── batch.md
│   │       └── dimensions.md
│   └── load/
│       └── SKILL.md
├── agents/
│   ├── orchestrator.md
│   ├── mind-extractor.md
│   ├── voice-extractor.md
│   ├── emotion-extractor.md
│   ├── knowledge-extractor.md
│   ├── relations-extractor.md
│   └── synthesizer.md
├── templates/
│   ├── index.md
│   ├── identity.md
│   ├── manifest.json
│   ├── mind/
│   │   ├── _index.md
│   │   ├── thinking-patterns.md
│   │   ├── values.md
│   │   └── worldview.md
│   ├── voice/
│   │   ├── _index.md
│   │   ├── style.md
│   │   └── catchphrases.md
│   ├── emotion/
│   │   ├── _index.md
│   │   ├── temperament.md
│   │   └── triggers.md
│   ├── knowledge/
│   │   ├── _index.md
│   │   └── domains.md
│   └── relations/
│       ├── _index.md
│       └── social-style.md
├── docs/
│   └── relic-spec.md
├── relics/                    ← 蒸馏产物存放
└── examples/                  ← 留空
```

## 六个维度（硬骨架）

| 维度 | 目录 | 内容 |
|------|------|------|
| 思维 | mind/ | 思维模式、价值观、世界观、盲区 |
| 表达 | voice/ | 语言风格、口头禅、幽默方式 |
| 情感 | emotion/ | 性格气质、触发点、应对模式 |
| 知识 | knowledge/ | 专业领域、深度知识 |
| 关系 | relations/ | 社交风格、关键关系 |
| 自定义 | {custom}/ | 弹性扩展，按需创建 |

## 批量模式多 Agent 编排

### 编排流程
```
orchestrator 扫描目录
  → 分析文件类型/大小
  → 并行派发给 5 个维度 extractor
  → 各 extractor 独立上下文提取
  → synthesizer 合成校验
  → 生成 index.md + manifest.json
  → 密度检查 → 超阈值分裂
```

### 文件分配策略
- < 50KB → 整文件分配
- 50KB-200KB → 切片分配
- > 200KB → 分多轮处理
- 文件类型：.md/.txt 直接分配，.json/.csv 结构化提取，代码文件提取思维+技术偏好

### Agent 职责

| Agent | 职责 |
|-------|------|
| orchestrator | 扫描目录、分配任务、协调流程 |
| mind-extractor | 从素材提取思维模式、价值观、世界观 |
| voice-extractor | 从素材提取语言风格、口头禅、表达习惯 |
| emotion-extractor | 从素材提取情感模式、性格气质 |
| knowledge-extractor | 从素材提取知识领域、专业深度 |
| relations-extractor | 从素材提取社交风格、关系模式 |
| synthesizer | 合成所有维度、一致性校验、生成索引 |

## 交互式模式

1. 读 dimensions.md 了解要收集的维度
2. 按 interview.md 框架逐步提问
3. 实时填充 Relic 文件
4. 检测空白维度 → 追问
5. 用户确认 → 进入校验

## Load（加载）流程

1. 读 index.md → 全貌
2. 读 identity.md → 身份
3. 读各维度 _index.md → 概览
4. 进入对话 → 按需深入读取

## Relic 文件规范

### _index.md 三要素
1. 摘要（200字以内精炼概括）
2. 子文件导航（每个子文件一行说明）
3. 阅读建议（快速/标准/深度三档）

### manifest.json
```json
{
  "name": "人名",
  "version": "1.0",
  "created": "ISO日期",
  "total_files": 数量,
  "total_tokens_estimate": 估算token数,
  "depth_max": 最大层深,
  "dimensions": {
    "mind": { "files": N, "tokens": N },
    ...
  }
}
```

### 动态分裂规则
- 单文件 > 2000字 → 分裂为目录
- 原文件名变为目录名
- 目录内创建 `_index.md`（摘要）+ 主题子文件
- 递归适用

## 平台兼容

支持 OpenClaw / Claude Code / Codex / Cursor / OpenCode 等主流 AI 编码平台安装使用。package.json 和插件配置文件需覆盖多平台。
