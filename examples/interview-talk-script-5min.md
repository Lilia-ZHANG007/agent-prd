# 面试讲稿 · agent-prd 项目 5 分钟演示（中英双语）

> 使用方式：每段先中文后英文。全文约 5 分钟（中文 3 分钟 + 英文 2 分钟，可按面试要求只讲其一）。
> 结构：开场钩子 → 仓库是什么 → 三个关键决策 → 收尾升华。

---

## ① 开场钩子（约 40 秒 / Opening Hook）

**中文：**

> "面试前我做了两件事：第一，把五款头部 AI 产品——Perplexity、Cursor、Claude Code、Codex、Notion AI——做了黑客级的案头拆解，一直拆到它们泄露的系统 Prompt 原文和检索架构；第二，我把拆解沉淀成了一个可复用的 Skill 工作流 `agent-prd`，并用它真实产出了一份完整的 Agent 产品 PRD。今天我用 5 分钟讲清楚这条'从调研到决策'的链路。"

**English:**

> "Before this interview, I did two things. First, I ran a hacker-level desk teardown of five leading AI products — Perplexity, Cursor, Claude Code, Codex, and Notion AI — down to their leaked system prompts and retrieval architectures. Second, I distilled that research into a reusable workflow skill called `agent-prd`, and used it to produce a complete, real PRD. In the next five minutes, I'll walk you through this research-to-decision pipeline."

---

## ② 仓库是什么（约 60 秒 / What the Repo Is）

**中文：**

> "这个仓库有三层。第一层是 `SKILL.md`：一个八阶段工作流，从需求澄清、痛点定位，到 Agent 架构六模块——模型、工具、Prompt 封装、RAG、记忆、循环——再到评估指标和商业化。第二层是 references：PRD 模板、设计模式速查、评估指标体系，其中设计模式全部提炼自五份拆解，比如 RAG 决策树——什么时候该建向量索引、什么时候该让 Agent 自主检索、什么时候该用可执行环境当 ground truth。第三层是实战样例：一份虚拟在 Kimi 内部立项的'Lighthouse 深度研究 Agent'PRD，用来证明这个工作流的产出质量。"

**English:**

> "The repo has three layers. First, `SKILL.md`: an eight-phase workflow — from requirement clarification and pain-point analysis, through six architecture modules — models, tools, prompt encapsulation, RAG, memory, and the agent loop — down to evaluation metrics and monetization. Second, the references: a PRD template, a design-pattern playbook, and an evaluation framework. The patterns are distilled from my five teardowns — for example, a RAG decision tree: when to pre-build a vector index, when to let the agent search on its own, and when an executable environment is the ground truth. Third, a worked example: a full PRD for 'Lighthouse', a hypothetical deep-research agent incubated at Kimi, demonstrating the workflow's output quality."

---

## ③ 三个关键决策（约 100 秒 / Three Key Decisions）

**中文：**

> "我挑三个决策，每个都能看出调研怎么变成设计。
>
> **第一，研究计划对用户可见、可编辑。** Perplexity 的泄露 Prompt 明确写着'用户看不到规划系统的工作'——这对通用用户是对的，但专业研究员要的是掌控感。所以 Lighthouse 刻意反着做：计划可见、可编辑、轨迹可回放。同一个机制，不同用户群，结论相反——这就是定位决定设计。
>
> **第二，引用是生成约束，不是后处理。** Perplexity 把逐句引用写进系统 Prompt 的强制规则；我在此之上加了一层校验：引用 ID 必须真实存在于本轮证据集，校验失败的句子直接标灰。对研究产品，引用正确率是生死线，我把它定为 ≥95% 的一票否决指标。
>
> **第三，成本结构前置到设计阶段。** Codex 的前缀缓存工程能把输入成本降 40–55%，Claude Code 用轻量模型跑探索子任务。Lighthouse 的单位经济学显示：毛利临界点就在缓存命中率和轻量模型分流比例上——所以这两个工程指标直接进了 PRD 的核心指标表，而不是留给工程团队后补。"

**English:**

> "Let me pick three decisions that show how research became design.
>
> **First, the research plan is visible and editable.** Perplexity's leaked prompt explicitly states 'the user has not seen the other system's work' — correct for casual users, but professional researchers demand control. So Lighthouse deliberately does the opposite: visible plans, editable steps, replayable traces. Same mechanism, different audience, opposite conclusion — positioning drives design.
>
> **Second, citations are a generation constraint, not post-processing.** Perplexity hard-codes per-sentence citation rules into its system prompt; I added a verification layer on top: every citation ID must exist in the current evidence set, and sentences that fail verification get greyed out. For a research product, citation accuracy is existential — I set it as a ≥95% release-blocking metric.
>
> **Third, cost structure is designed upfront, not patched later.** Codex's prefix-caching engineering cuts input costs by 40 to 55 percent; Claude Code routes exploration to lightweight models. Lighthouse's unit economics show the gross-margin tipping point sits exactly on cache hit rate and lightweight-model offloading — so both became first-class metrics in the PRD, not afterthoughts for engineering."

---

## ④ 收尾升华（约 40 秒 / Closing）

**中文：**

> "这个项目想证明的一件事是：AI 产品的竞争壁垒正在从模型层下沉到编排层和数据层——而产品经理的价值，就是把这些工程事实翻译成定位、指标和商业模式。五份拆解是我的调研能力，`agent-prd` 是我的沉淀能力，Lighthouse PRD 是我的产出能力。谢谢，欢迎提问。"

**English:**

> "This project demonstrates one belief: the competitive moat of AI products is sinking from the model layer down to the orchestration and data layers — and a product manager's job is to translate those engineering facts into positioning, metrics, and business models. The five teardowns show my research capability; `agent-prd` shows my ability to systematize; the Lighthouse PRD shows my output. Thank you — I welcome your questions."

---

## 附：可能被追问的问题与应答要点 / Likely Follow-ups

| 追问 | 应答要点 |
|---|---|
| 为什么样例选深度研究而不是 Coding Agent？ | Kimi 已有长上下文与搜索心智，研究场景是长上下文优势的最大兑现点；Coding 赛道已极度拥挤 |
| Why a research agent, not a coding agent? | Kimi's long-context strength pays off most in research; the coding-agent space is already crowded |
| 引用正确率 95% 怎么达到的？ | 生成约束 + 后处理校验 + 标灰降级三件套；评测集 500 条逐句标注，发版必回归 |
| 如果巨头免费跟进怎么办？ | 押注中文垂直索引和 Space 私有数据资产——通用产品复制不了的两个数据层 |
| 工作流本身怎么验证有效？ | 样例 PRD 即验证；且 skill 已在 GitHub 开源，可复现、可迭代 |

---

> 讲稿对应的仓库：https://github.com/Lilia-ZHANG007/agent-prd
