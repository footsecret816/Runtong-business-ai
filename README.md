# Runtong Business AI Harness｜润通外贸业务 AI 助手

> **中文**：面向 RUNTONG / WAYEAH 的专用 B2B 外贸业务 AI Harness。它把客户开发、询盘分析、谈判、商务写作、工厂沟通、风险控制、项目推进和公司知识维护沉淀成可跨模型、跨平台复用的业务方法。
>
> **English**: A dedicated, model-agnostic Business AI Harness for RUNTONG / WAYEAH B2B trade workflows.

## 它和通用版的区别

这个仓库不是“从 0 建公司资料”的通用 Agent。

RUNTONG / WAYEAH 的 Company Pack 已经预装在：

`company/packs/runtong/`

所以正常使用时可以直接进入业务工作，不需要重新录入润通公司背景、产品、供应链和合规边界。

本次架构重点增加的是：**公司信息持续维护能力**。

## 核心业务能力

| Skill | 实际作用 |
|---|---|
| `customer-analysis` | 拆客户邮件、询盘、PO、会议信息；分清事实、问题、未决项和真实回复重点 |
| `prospecting` | 新客户研究、筛选、产品匹配、切入角度、开发优先级 |
| `gap-strategy` | 对比客户要求、润通/工厂现实、行业/合规边界，先找 Gap 再定打法 |
| `negotiation` | MOQ、价格、付款、交期、模具费、样品费、例外条件等谈判 |
| `business-writing` | Email、WhatsApp、LinkedIn、Follow-up；不机械翻译，不写客服腔 |
| `factory-bridge` | 客户语言 ↔ 工厂/技术语言双向转换，减少信息失真 |
| `risk-guard` | 认证、法规、IP、技术承诺、付款、交期、商业授权等风险控制 |
| `project-next-action` | 把分析落到下一步：谁确认、确认什么、触发条件和后续沟通 |
| `company-knowledge-curation` | 正式整理、核对、更新 RUNTONG Company Pack；按需调用，不常驻运行 |

## 业务行为原则

- 简单问题保持简单，不强行套大模板。
- 复杂问题遵循 **Gap → Strategy → Communication**。
- 不把推断反复说成事实。
- 当前项目事实优先于公司通用知识、历史 Memory 和 Golden Cases。
- 不擅自承诺价格、MOQ 特批、付款条件、交期、赔偿、认证或未确认技术结论。
- Golden Cases 学的是判断方式，不是拿历史事实套当前客户。
- 老客户沟通降低仪式感，保持自然、清楚、专业。
- 谈判中真实的结构性限制要说明原因，但不暴露无必要的内部成本细节。

## Company Workspace｜润通公司信息区

```text
company/
├── README.md
├── MAINTENANCE.md
├── COMPANY_PACK_SPEC.md
├── ACTIVE_COMPANY.yaml
├── inbox/
├── pending/
└── packs/
    └── runtong/
        ├── PACK.yaml
        ├── INDEX.md
        ├── COMPANY_PROFILE.md
        ├── PRODUCT_CAPABILITIES.md
        ├── SUPPLY_CHAIN_MODEL.md
        ├── COMPLIANCE_BOUNDARIES.md
        ├── MARKETS_AND_CUSTOMERS.md
        ├── BUSINESS_SOP.md
        ├── SOURCES.md
        └── products/
```

### 1. 已有润通 Company Pack

润通公司资料已经是正式 Company Pack，不需要重新 onboarding。

运行时按任务选择性加载相关文件，不把整个公司包永久塞进上下文。

### 2. 新公司材料更新

当用户提供新的 PDF / PPT / Word / Excel / 证书 / 产品资料等：

`新材料 → company/inbox/ → company-knowledge-curation → 分类/去重/范围判断/冲突检查 → 操作者核对 → 更新正式 Company Pack`

不会因为上传了一份材料，就自动把其中所有内容写成公司事实。

### 3. Business Conversation Patch｜业务对话中的公司新信息

日常业务对话可能自然出现新的长期事实，例如：

- 新证书或验厂状态
- 新产品线
- 新设备 / 新产能
- 新工厂长期能力
- 新供应链能力
- 市场覆盖变化
- 某项旧能力已经失效

Core 只做轻量识别：

`业务对话 → COMPANY_UPDATE_CANDIDATE → 提示操作者 → company/pending/ → company-knowledge-curation → 核对 → 正式更新`

**不会在普通业务对话里静默修改公司档案。**

### 4. 什么不应该进入 Company Pack

以下通常属于客户/项目 Memory，而不是长期公司知识：

- 某客户专属价格
- 某项目 MOQ
- 某次老板特批
- 临时供应商报价
- 单次加急交期
- 某订单特殊付款条件
- 某项目独有的认证/测试结论
- AI 自己的推测

## 公司信息范围控制

必须区分：

`公司级 / 工厂级 / 产品级 / 项目级 / 客户级`

例如“某合作工厂有某认证”不能自动扩大成“润通所有产品都具备该认证”；公司一般能力也不能直接变成当前项目承诺。

## Cases｜经验层

仓库保留匿名化 Golden Cases 和 Anti-patterns，用来稳定业务判断与沟通风格，包括：

- 硬 MOQ vs 试单
- 年采购量 vs 单次订单报价基础
- 价格接近底线
- 内部技术数据 vs 正式第三方报告
- 样品差异 vs 额外开模
- 混合 SKU / 包装结构 vs 生产 MOQ
- 项目临近成交但客户沉默
- IP 敏感参考设计
- 生产先于定金的受控特批
- 老客户自然沟通语气
- NDA 边界下的客户背书与增信

## Portability｜本地路径与平台抽象

所有路径相对逻辑 `AGENT_ROOT` / `REPO_ROOT` 解析。

不依赖固定：

- `D:\...`
- `C:\Users\...`
- `/Users/...`
- `/home/...`

Codex、Claude、DeepSeek Harness、Accio Work 或其他 Agent 平台只通过薄 Adapter 接入，不复制整套 Business Core。

## Validation｜评测

`evals/` 同时验证：

- 外贸业务判断能力
- 事实纪律
- 谈判和写作效果
- Company Pack 范围边界
- RUNTONG 公司新信息候选识别
- 项目/客户临时事实是否错误污染公司档案
- 公司旧事实被修正时是否正确处理 supersession

“能导入某平台”不等于“该平台已生产验证”。目标 Harness 仍需运行统一 Evals。

## Architecture

`Core + Skills + Cases + Company + Memory + Knowledge + Evals + Adapters`

核心原则：

> **模型负责智能，框架负责业务方法、事实边界与行为一致性。**

---

## English overview

This repository is the RUNTONG / WAYEAH-specific edition of the Business AI Harness. The RUNTONG Company Pack is already installed, so users do not need zero-start company onboarding. The company layer focuses on continuous maintenance: new source materials, explicit company corrections, and durable company facts discovered during normal business conversations are reviewed before they become formal Company Pack updates.
