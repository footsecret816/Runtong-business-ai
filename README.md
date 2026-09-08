# Runtong Business AI Harness｜润通外贸业务 AI 框架

> **中文**：一个面向 B2B 外贸业务的、模型无关（Model-Agnostic）的 Business AI Harness，用于客户开发、询盘分析、项目推进、商务谈判、技术沟通、风险控制、企业知识调用与客户记忆协同。
>
> **English**: A model-agnostic Business AI Harness for B2B trade workflows, including prospecting, inquiry analysis, project follow-up, negotiation, technical communication, risk control, company knowledge, and customer-memory integration.

**当前状态 / Current status:** V1 Baseline 已发布至 `main` / V1 Baseline released on `main`.

---

# 中文说明

## 这个项目是做什么的？

这个仓库不是一个单独的 Prompt，也不是绑定某一个 AI 模型的聊天机器人。

它的目标是把真实外贸业务中反复验证过的工作方法，沉淀成一套可以跨模型、跨 AI 智能体平台迁移的 **Business AI 业务框架**。

核心思想是：

> **模型负责智能，框架负责业务方法与行为一致性。**

因此，即使未来底层模型从 GPT 换成 Claude、DeepSeek 或其他模型，核心业务逻辑仍尽量保持一致。

## 核心架构原则：Generic Core First

任何一个 AI 平台都不是这个项目的中心。

```text
Business Core（通用业务核心）
+ Company Pack（企业知识包）
+ Customer Memory（客户记忆）
+ Evals（评测体系）
        ↓
Platform Adapter（平台适配层）
        ↓
Codex / Claude Code / DeepSeek Harness / WorkBuddy / Accio Work / 未来平台
        ↓
目标模型 + 平台可用工具
```

平台专属文件只负责“接线”和“部署”。真正的业务逻辑应保留在 Core、Skills、Cases、Company Packs、Memory Rules 和 Evals 中。

## V1 已包含

- **1 个主 Business Copilot 入口** — `AGENTS.md`
- **1 个轻量 Business Kernel** — `core/BUSINESS_KERNEL.md`
- **1 套模型无关运行规则** — `core/MODEL_AGNOSTIC_RUNTIME.md`
- **8 个核心业务 Skills** — `skills/`
- **Golden Cases + Anti-patterns** — `cases/`
- **跨模型 Benchmark + E2E 验收** — `evals/`
- **可替换 Company Packs** — `knowledge/company-packs/`
- **Customer Memory Schema** — `schemas/customer-memory.md`
- **平台适配层** — `adapters/`

## 主要业务能力

V1 主要覆盖：

- 新客户开发与客户筛选
- 客户询盘 / 邮件 / 消息拆解
- 客户要求 vs 工厂现实 vs 商业 / 合规边界的 Gap 判断
- MOQ、价格、付款、交期等商务谈判
- 工厂技术信息与客户语言之间的转换
- 商务邮件、WhatsApp、LinkedIn 等沟通输出
- 风险与承诺边界控制
- 项目下一步动作判断

## 核心行为原则

- 简单问题保持简单，不强行套大模板。
- 复杂商业问题先判断 **Gap → Strategy → Communication**，而不是直接翻译。
- 明确区分：已确认事实、推测、未知信息、待确认信息。
- 当前项目事实优先于公司通用知识和历史案例。
- AI 可以分析和建议，但不得擅自承诺价格、MOQ 特批、付款条件、交期、赔偿、认证或未确认技术结论。
- Golden Cases 用来学习判断方式，不能作为当前客户的事实证据。

## 企业知识层

企业专属知识与通用 Business Core 分离。

当前 RUNTONG / WAYEAH Company Pack 位于：

`knowledge/company-packs/runtong/`

包括：

- 企业定位
- 产品能力
- 供应链模式
- 合规 / 认证边界
- 市场与客户类型
- 业务 SOP
- 来源追溯
- 按需加载的产品分类知识

以后如果换成另一家公司，只需要增加或替换 Company Pack，不需要重写 Business Kernel 和 Skills。

## Customer Memory

本仓库目前保存的是 **客户记忆结构（Schema）**，而不是大量真实客户历史。

真实客户 / 项目记忆未来应尽量放在独立的数据层中，并保留：

- 信息来源
- 记录时间
- 当前有效状态
- 新旧事实覆盖关系
- 项目 / 工厂适用范围

## 跨平台适配

平台适配规范见：

- `adapters/PLATFORM_ADAPTER_CONTRACT.md`
- `adapters/COMPATIBILITY_MATRIX.md`

当前设计目标包括：

- Codex
- Claude Code
- DeepSeek Harness
- WorkBuddy / CodeBuddy
- Accio Work
- 其他未来 AI Agent 平台

不会提前为所有平台复制一套业务逻辑。真正使用某个平台时，只实现对应的薄 Adapter，然后运行同一套 Evals 验证效果。

## 当前 V1 状态

V1 已完成当前模型上的架构级 E2E 验收，并在发现“最新项目事实 vs 旧记忆”的优先级缺口后完成修正。

这代表 **V1 架构可以进入真实平台测试**，但不代表已经证明所有模型 / Harness 的效果完全相同。

不同平台或模型正式使用前，仍应运行 `evals/` 中的统一测试集。

---

# English Overview

## What is this project?

This repository is not a single prompt and is not tied to one AI model or agent platform.

Its purpose is to externalize reusable business methods learned from real B2B trade workflows into a portable **Business AI Harness**.

The guiding principle is:

> **The model provides intelligence; the framework preserves business method and behavioral consistency.**

## Architecture principle: Generic Core First

No platform is the center of this repository.

```text
Business Core
+ Company Pack
+ Customer Memory
+ Evals
        ↓
Platform Adapter
        ↓
Codex / Claude Code / DeepSeek Harness / WorkBuddy / Accio Work / future platform
        ↓
Target model + available tools
```

Platform-specific files are adapters only. Canonical business logic remains in the Core, Skills, Cases, Company Packs, Memory rules, and Evals.

## What V1 contains

- **1 primary Business Copilot entry** — `AGENTS.md`
- **1 lightweight Business Kernel** — `core/BUSINESS_KERNEL.md`
- **1 model-agnostic runtime contract** — `core/MODEL_AGNOSTIC_RUNTIME.md`
- **8 broad business skills** — `skills/`
- **Golden Cases + Anti-patterns** — `cases/`
- **cross-model benchmarks + E2E acceptance** — `evals/`
- **swappable Company Packs** — `knowledge/company-packs/`
- **customer-memory schema** — `schemas/customer-memory.md`
- **thin platform adapters** — `adapters/`

## Core behavior

- Simple tasks stay simple.
- Complex commercial conflicts follow **Gap → Strategy → Communication**.
- Confirmed facts, inference, unknowns, and items to confirm remain distinct.
- Current project facts outrank company-general knowledge and abstract cases.
- The AI may recommend but must not invent approval for price, MOQ exceptions, payment terms, delivery commitments, compensation, certifications, or technical conclusions.
- Reusable cases teach reasoning patterns; they are never current-customer evidence.

## Company knowledge

Company-specific knowledge is isolated from the reusable core.

The current RUNTONG / WAYEAH Company Pack is under:

`knowledge/company-packs/runtong/`

A different company should add or replace a Company Pack without changing the Core Kernel or Skills.

## Customer memory

The reusable repository currently stores the **memory schema**, not large volumes of raw customer history.

Real customer/project memory should remain in a separate data layer where possible, with provenance, timestamps, scope, and superseded-fact handling preserved.

## Platform portability

See:

- `adapters/PLATFORM_ADAPTER_CONTRACT.md`
- `adapters/COMPATIBILITY_MATRIX.md`

Native adapters should be implemented only when a platform is actually selected, then validated against the same canonical Evals.

## V1 status

V1 has passed an architecture-level E2E simulation on the current model after one source-precedence fix.

This means the V1 architecture is ready for real platform testing. It does **not** mean that every target model or harness has already been proven equivalent.

See `PROJECT.md` for the architecture baseline and `evals/` for validation assets.

---

> **隐私提醒 / Privacy note:** Real customer data should not be placed in the reusable core case library. / 真实客户数据不应放入可复用的核心案例库中。
