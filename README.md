# agent-prd

> 为 AI Agent 产品撰写通用 PRD 的结构化工作流 Skill（兼容 Kimi / Claude Code / Codex 等支持 SKILL.md 的 Agent 运行时）。

把"设计一款 Agent"从拍脑袋变成一条可复用的流水线：**需求澄清 → 痛点定位 → 场景定义 → Agent 架构（模型/工具/Prompt/RAG/记忆/循环）→ 权限安全 → 评估指标 → 商业化 → 里程碑**，最终产出一份可直接评审的完整 PRD。

## 为什么需要它

写 Agent 产品的 PRD 和传统软件 PRD 有本质区别：

- 你设计的不是功能，是**一个自主系统的行为边界**——Prompt 封装、工具权限、循环止损、拒答策略都是产品决策；
- RAG 路线（预建索引 vs Agentic 检索 vs 可执行环境）没有默认答案，选错就是架构返工；
- "任务成功率、引用正确率、缓存命中率"这些指标必须先于功能定义，否则上线后无法评估。

本 Skill 把这些问题固化为工作流与决策树，设计模式提炼自 Perplexity、Cursor、Claude Code、Codex、Notion AI 五款头部产品的公开架构与泄露/开源系统 Prompt。

## 仓库结构

```
agent-prd/
├── SKILL.md                              # 工作流主文件（Agent 读取的入口）
├── references/
│   ├── prd-template.md                   # PRD 完整章节模板（填空式 + 质检清单）
│   ├── agent-design-patterns.md          # Agent 设计模式速查（模型/Prompt/RAG/权限/定价）
│   └── evaluation-metrics.md             # 评估指标体系与评测集设计方法
└── README.md
```

## 安装

将整个 `agent-prd/` 目录放入你的 skills 目录之一：

- `~/.config/agents/skills/`（推荐）
- `~/.kimi/skills/`
- `~/.claude/skills/`
- 或项目级 `.agents/skills/`

## 使用

对 Agent 说出触发语即可，例如：

- "帮我设计一款面向律师的合同审查 Agent，写一份 PRD"
- "我要立项一个代码审查 Agent，帮我理清架构决策"
- "给我们的企业知识库助手写产品需求文档"

Agent 会先进入 Phase 0 向你确认 5 个关键约束（目标用户、替代的工作流、运行形态、数据边界、模型策略），然后逐阶段推进，最终按模板产出完整 PRD 并过质检清单。

## 产出物包含

- 一句话定位 + Non-goals
- 用户画像与核心场景（触发→行为序列→成功产出→失败兜底）
- 六大架构决策：模型路由 / 工具集 / Prompt 封装 / RAG 路线 / 记忆分层 / 循环与人机断点
- 权限模型与危险操作清单
- 分层指标体系与评测集设计
- 定价结构与单位经济学
- 三段式路线图与风险表

## License

MIT
