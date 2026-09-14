# Runtong Business AI Harness｜润通外贸业务 AI 助手

> **中文**：这是面向 RUNTONG / WAYEAH 的专用 B2B 外贸业务 AI Harness。它不是一个单独 Prompt，也不是只负责“帮忙写邮件”的聊天机器人，而是一套把真实外贸业务方法、润通公司知识、业务经验案例、风险边界和跨平台运行规则组合起来的业务辅助系统。
>
> **English**: A dedicated, model-agnostic Business AI Harness for RUNTONG / WAYEAH B2B trade workflows, combining reusable business reasoning, company knowledge, negotiation/writing skills, cases, risk controls, and platform portability.

---

## 这个项目解决什么问题？｜Why this exists

普通大模型可以写邮件，但真实外贸工作往往不是“把中文翻成英文”这么简单。

实际工作里更常见的问题是：

- 客户真正关心的是什么？
- 客户说的要求，和工厂现在能做到的事情之间差在哪里？
- 这个 MOQ 是硬限制，还是还有谈判空间？
- 当前价格应该继续让，还是应该开始稳住底线？
- 工厂的技术回复应该怎么转换成客户听得懂、又不失真的商务语言？
- 某个认证、测试、交期、付款条件，到底是“公司一般能力”还是“当前项目已经确认”？
- 客户几天没回复，是不是应该跟进？怎么跟，才不是机械催促？
- 对话里出现了新的公司长期信息，应该记入润通公司档案，还是只属于某个客户/项目？

Runtong Business AI 的目标，是把这些反复出现的判断方式外置成一套稳定框架：

> **模型负责智能，框架负责业务方法、事实边界与行为一致性。**

因此，它不仅要“写得像业务员”，还要尽量做到：

`理解业务 → 判断事实 → 找 Gap → 定策略 → 组织沟通 → 推下一步`

---

## 它和通用版 B2B-Trade-Business-AI 有什么区别？

两套 Agent 使用相同的核心业务思路，但起点不同。

| 项目 | B2B-Trade-Business-AI | Runtong-business-ai |
|---|---|---|
| 公司身份 | 不预装任何公司 | 预装 RUNTONG / WAYEAH |
| Company Pack | 从 0 建立 | 已建立，可直接使用 |
| 日常业务 | 通用外贸业务 | 直接按润通业务背景工作 |
| 公司资料维护 | Onboarding + 后续维护 | 重点是持续补丁更新 |
| 适合谁 | 任意外贸公司 | 润通内部业务使用 |

RUNTONG / WAYEAH 的正式 Company Pack 已在：

`company/packs/runtong/`

所以正常使用时，不需要重新录入润通公司背景、产品能力、供应链模式、市场定位和合规边界。

---

## 它实际能做什么？｜Core business capabilities

### 1. 客户消息拆解｜Customer Analysis

不仅告诉你“客户这句话是什么意思”，还可以在复杂邮件中拆出：

- 客户明确提出的问题
- 已确认事实
- 仍未确认的信息
- 客户的异议 / 压力点
- 当前项目阶段
- 哪些内容真正需要回复
- 哪些只是背景信息，不需要逐句回应

简单问题保持简单；复杂邮件才做结构化拆解。

---

### 2. 新客户开发｜Prospecting

用于网站客户、展会客户、LinkedIn、B2B 平台、老线索重新开发等场景。

Agent 会优先判断：

- 客户属于什么渠道 / 类型
- 可见产品结构与定位
- 润通哪些产品更可能匹配
- 是否存在可切入的产品空位
- 适合先推哪几个方向
- 是否值得优先开发
- 第一封开发信息应该怎么切入

默认不把“发整本目录”当成唯一开发方式。

---

### 3. Gap / 策略判断｜Gap & Strategy

复杂问题优先使用三角判断：

`客户要求` vs `润通 / 工厂现实` vs `行业 / 合规 / 技术 / 商业边界`

例如：

- 客户要正式第三方报告，但工厂只有内部数据
- 客户要 5,000 支试单，但生产 MOQ 是 40,000
- 样品和客户原样很接近，但并非 1:1
- 客户要求某个时间交货，但工厂实际排期有风险
- 客户要求完全复制一个可能存在 IP 风险的设计

Agent 先找真正的 Gap，再决定应该：

`推进 / 稳预期 / 降风险 / 解释 / 谈判 / 给替代方案 / 增信 / 守住底线`

而不是直接翻译工厂回复。

---

### 4. 商务谈判｜Negotiation

覆盖常见外贸谈判：

- MOQ
- 价格
- 付款方式
- 定金 / 尾款
- 交期
- 样品费
- 模具费
- 包装 MOQ
- 特批条件
- 赔偿 / 补偿
- 年采购量 vs 单次订单量

核心原则不是“永远强硬”或“永远配合”，而是：

1. 先区分硬限制和可谈变量；
2. 再看有没有交换条件；
3. 最后决定怎么表达。

AI 不会自行发明最低价、最大折扣、老板特批或最终付款例外。

---

### 5. 商务写作｜Business Writing

支持：

- Email
- WhatsApp
- LinkedIn
- Inquiry reply
- Follow-up
- 报价说明
- 技术问题回复
- 老客户日常更新
- 局部改写 / 精简 / 调整语气

写作标准不是“更正式”，而是：

- Professional
- Natural
- Commercially aware
- Concise
- Firm when necessary
- Cooperative without sounding weak

特别避免：

- 客服腔
- 机械中译英
- 过度感谢
- 过度道歉
- 每封邮件都重新介绍公司
- 用户只要求改一句，却把整封邮件重写

老客户默认降低仪式感，保持熟悉但专业。

---

### 6. 客户 ↔ 工厂信息转换｜Factory Bridge

这是润通业务里很关键的一层。

**客户 → 工厂：**

把客户的商务/技术要求拆成工厂真正能执行和确认的问题，例如：

- 材料
- 尺寸 / 公差
- 测试方法
- 包装
- MOQ
- 模具
- 交期
- 颜色
- 生产控制
- 验收标准

**工厂 → 客户：**

把工厂常见的口语化、生产视角回复，转换成客户能理解的准确商务语言。

原则是：重构表达，不篡改事实。

---

### 7. 风险控制｜Risk Guard

在回复或决策前检查：

- 认证 / 法规表述是否过度
- 公司通用能力是否被误写成当前项目能力
- 工厂级事实是否被错误扩大成整个润通能力
- 医疗 / 功效宣称是否过头
- IP / 设计复制风险
- 技术参数是否已确认
- 交期承诺是否有依据
- 付款 / 特批 / 补偿是否超授权
- 是否暴露客户 / 供应商保密信息

需要确认的内容会保留为 `TO_CONFIRM`，而不是补一个看起来合理的答案。

---

### 8. 项目下一步推进｜Project Next Action

Agent 不只回答“怎么回”，还会在复杂项目里识别：

- 客户下一步要确认什么
- 工厂下一步要确认什么
- 我方内部还缺什么
- 哪些问题仍未关闭
- 哪个动作会触发下一阶段
- 下一次跟进应该基于什么，而不是机械催促

目标是把分析变成项目推进。

---

### 9. 公司知识维护｜Company Knowledge Curation

这是当前润通版新增的重要能力。

它不是常驻监控 Skill，而是按需调用的正式整理能力，负责：

- 读取新的公司 PDF / PPT / Word / Excel / 图片 / 证书 / 产品资料
- 提取事实
- 分类
- 去重
- 检查冲突
- 判断信息属于公司级 / 工厂级 / 产品级 / 项目级 / 客户级
- 标记待确认
- 生成审核草稿
- 接受用户多轮修正
- 用户确认后再正式更新 RUNTONG Company Pack

---

## 润通 Company Pack 已经包含什么？

当前正式 Company Pack 位于：

`company/packs/runtong/`

主要包括：

- `COMPANY_PROFILE.md` — 公司身份、定位、商业模式、核心优势
- `PRODUCT_CAPABILITIES.md` — 产品线、材料、OEM/ODM、自定义能力
- `SUPPLY_CHAIN_MODEL.md` — 供应链和合作工厂模式
- `COMPLIANCE_BOUNDARIES.md` — 认证、测试、法规、宣传、验厂、IP 边界
- `MARKETS_AND_CUSTOMERS.md` — 市场、渠道、客户类型
- `BUSINESS_SOP.md` — 从询盘到订单、生产、交付的业务流程
- `SOURCES.md` — 公司知识来源与确认记录
- `products/` — 按产品分类加载的更详细知识

当前核心业务定位覆盖鞋护理、鞋垫、足部护理、鞋类配件，并包含运动支撑 / 恢复类扩展项目；部分其他品类按项目型扩展能力处理，而不是自动等同于核心产品线。

Company Pack 提供的是公司背景和一般能力，不自动证明每个项目的价格、MOQ、认证、测试、交期或具体生产条件。

---

## 公司信息如何持续更新？｜Company maintenance

### A. 已有正式 Company Pack

润通不需要重新 onboarding。

运行时按当前任务选择性加载：

```text
客户开发
→ 公司定位 + 市场客户 + 对应产品能力

鞋垫项目
→ PRODUCT_CAPABILITIES + products/INSOLES

认证问题
→ COMPLIANCE_BOUNDARIES + 当前项目证据

工厂能力问题
→ SUPPLY_CHAIN_MODEL + 对应工厂/项目事实
```

不是每次把整个公司资料全部塞进上下文。

### B. 新公司材料

当你以后提供新的：

`PDF / PPT / Word / Excel / 证书 / 产品目录 / 工厂资料`

标准流程是：

```text
新材料
→ company/inbox/
→ company-knowledge-curation
→ 提取 / 分类 / 范围判断 / 去重 / 冲突检查
→ 生成审核稿
→ 用户补充 / 修改 / 多轮核对
→ 用户确认
→ 更新正式 RUNTONG Company Pack
```

不会把一份新资料里的所有文字直接升级为正式公司事实。

### C. 业务对话里的公司新信息

很多公司知识并不是通过正式资料出现，而是在日常工作中自然说出来，例如：

- 新证书
- 新验厂
- 新产品线
- 新设备
- 新长期产能
- 新合作工厂能力
- 新供应链能力
- 某项长期能力取消
- 某项公司事实被明确纠正

Core 只做轻量发现：

```text
业务对话
→ 发现可能长期复用的信息
→ COMPANY_UPDATE_CANDIDATE
→ 提示操作者
→ 确认是否值得进入公司档案
→ company/pending/
→ company-knowledge-curation
→ 正式更新
```

**普通业务对话不会静默修改 Company Pack。**

---

## Company 和 Customer / Project Memory 必须分开

下面这些通常不应该进入长期公司档案：

- 某客户专属价格
- 某订单 MOQ
- 某次老板特批
- 临时供应商报价
- 某一次赶货交期
- 单项目付款条件
- 单项目测试结果
- 客户 PO / 条码 / 包装版本
- 某个项目当前阶段

这些属于 Customer / Project Memory。

长期公司知识则更接近：

- 稳定产品线
- 长期供应链能力
- 已确认公司定位
- 已确认工厂长期能力
- 长期认证 / 审核状态
- 长期市场 / 渠道能力
- 公司 SOP

核心原则：

> **Company = 我们长期是谁、能做什么。**
>
> **Memory = 某个客户 / 某个项目发生了什么。**

---

## 实际任务会怎么处理？｜Behavior examples

### 例 1：简单理解

用户：

> 客户这句话什么意思？

行为：

`customer-analysis → 直接解释`

不会输出一大套局势诊断、谈判策略和风险分析。

### 例 2：客户试单低于硬 MOQ

用户：

> 客户要 5,000，工厂最低 40,000，我怎么回？

行为：

`customer-analysis → gap-strategy → negotiation → business-writing`

重点不是机械写“our MOQ is 40,000”，而是先判断这个 MOQ 是否是结构性生产限制，再设计一个 firm + cooperative 的解释方式。

### 例 3：工厂只有内部测试数据

行为：

`factory-bridge → gap-strategy → risk-guard → business-writing`

区分：

`没有测试` ≠ `有测试，但没有客户要求的正式报告形式`

然后再设计推进路径。

### 例 4：老客户日常项目更新

行为：

直接：

`状态 → 附件/参考 → 需要客户确认的事情 → 简单结尾`

不会重新介绍润通公司，也不会写成客服通知。

### 例 5：业务聊天中出现“新公司长期能力”

行为：

先完成当前业务任务，同时轻量提醒：

> 这条信息可能属于可长期复用的 RUNTONG 公司知识，是否需要加入待更新项？

只有用户确认后才进入正式整理流程。

---

## Cases｜经验层

仓库中的 Golden Cases 不是客户数据库，而是匿名化后的业务经验。

当前覆盖的典型模式包括：

- 硬 MOQ vs 小试单
- 年采购量 vs 单次订单报价基础
- 价格接近商业底线
- 内部技术数据 vs 正式第三方报告
- 样品差异 vs 额外开模
- 混合 SKU / 包装结构 vs 生产 MOQ
- 项目接近成交但客户沉默
- IP 敏感参考设计
- 不规则形状 vs 虚假精度
- 生产先于定金的受控特批
- 老客户自然沟通
- NDA 边界下的客户背书与增信

Cases 只学习：

`冲突是什么 → 为什么这样判断 → 应该采取什么策略 → 什么表达更有效`

不会把历史案例中的数字、客户、付款、价格、承诺当成当前事实。

---

## 写作和谈判风格｜Communication standard

默认目标：

`clear + commercially aware + natural + concise`

### 新客户

简洁介绍能力，但重点必须回到客户项目，而不是长篇公司宣传。

### 老客户

减少仪式感，不重复公司介绍，保持熟悉但专业。

### 谈判

先解释真实商业 / 生产逻辑，再表达立场；有边界就明确，但不把客户推开。

### 技术问题

准确优先，不用“听起来很专业”的术语代替事实。

### Follow-up

必须有重新进入对话的理由：

- 项目进度
- 新信息
- 决策点
- 关系维护
- 有价值的补充

而不是不断重复 `just following up`。

---

## Architecture｜架构

```text
Core
+ Skills
+ Cases
+ Company
+ Memory
+ Knowledge
+ Schemas
+ Evals
+ Adapters
```

### Core = 大脑

负责理解任务、事实判断、深度选择、技能路由和自检。

### Skills = 能力

负责客户分析、开发、谈判、写作、工厂桥接、风险、推进和公司知识整理。

### Cases = 经验

提供可迁移的判断模式和反例。

### Company = 润通身份

告诉 AI “我们是谁、有哪些长期能力和边界”。

### Memory = 客户 / 项目历史

记录某客户或项目发生过什么。

### Knowledge = 通用知识

保存不属于某个具体公司的行业 / 渠道 / 标准类知识。

### Adapters = 平台接线层

让同一套 Business Core 能接入不同 Agent Harness。

---

## Portability｜跨电脑、跨平台

所有仓库路径均相对逻辑：

`REPO_ROOT / AGENT_ROOT`

解析，不绑定：

- `D:\...`
- `C:\Users\...`
- `/Users/...`
- `/home/...`

正常目标体验是：

```text
Clone / Import / Install / Open
→ 平台提供或自动发现仓库根目录
→ Agent 启动
```

换电脑不应该要求重新修改整个 Agent 的本地路径。

Codex、Claude Code、DeepSeek Harness、Accio Work、WorkBuddy / CodeBuddy 等平台只通过 Adapter 接入；平台差异不应复制或重写核心商务逻辑。

---

## Safety Boundary｜安全与授权边界

AI 可以：

- 分析
- 比较
- 推荐
- 写作
- 提醒风险
- 设计推进策略

AI 不可以在没有依据时自行确认：

- 最低价格
- 最大折扣
- MOQ 特批
- 付款例外
- 赔偿金额
- 独家条件
- 最终交期
- 认证适用性
- 法规接受性
- 未确认技术性能
- 老板 / 工厂已经批准某件事

信息不足时必须保留：

`UNKNOWN / TO_CONFIRM`

而不是为了让回答完整而补事实。

---

## Validation｜评测体系

`evals/` 用来判断换模型、换平台后是不是“业务能力还在”。

主要评估：

- Task understanding
- Fact discipline
- Business diagnosis
- Strategy quality
- Risk control
- Communication quality
- Response depth
- Advancement value

并包含 RUNTONG Company Pack 专项测试，例如：

- 公司认证 / 能力范围有没有被错误放大
- 公司长期信息候选能不能正确识别
- 项目特批是否会污染公司档案
- 公司旧事实被明确纠正后是否正确 supersede
- 对话更新 → pending → curation → Company Pack 的流程是否守住确认边界

> **能够导入一个 AI 平台，不等于已经在该平台生产验证。**

真正迁移模型 / Harness 时仍需要跑同一套 Evals。

---

## Repository map｜主要目录

```text
Runtong-business-ai/
├── AGENTS.md              # Agent 入口
├── PROJECT.md             # 架构基线
├── core/                  # Business Kernel + Runtime
├── skills/                # 业务能力
├── cases/                 # Golden Cases + Anti-patterns
├── company/               # RUNTONG Company Workspace
│   ├── ACTIVE_COMPANY.yaml
│   ├── MAINTENANCE.md
│   ├── inbox/
│   ├── pending/
│   └── packs/runtong/
├── memory/                # 客户 / 项目记忆层（运行数据层）
├── knowledge/             # 通用知识
├── schemas/               # 数据结构
├── evals/                 # Benchmark / E2E
└── adapters/              # 平台适配
```

---

## English overview

Runtong Business AI is the RUNTONG / WAYEAH-specific edition of the reusable B2B Trade Business AI architecture.

Unlike the generic edition, the RUNTONG Company Pack is already installed and active. The agent can therefore start from existing company context rather than rebuilding company knowledge from zero.

Its main business capabilities include customer analysis, prospecting, gap/strategy diagnosis, negotiation, business writing, factory-customer translation, risk control, project next-action planning, and reviewed company-knowledge maintenance.

During normal work, the Core may detect durable new company facts, but it does not silently modify the Company Pack. Potential updates remain `COMPANY_UPDATE_CANDIDATE` items until reviewed and confirmed through the company-knowledge-curation workflow.

The repository remains model-agnostic and platform-agnostic: business methodology stays in the Core / Skills / Cases / Company layers, while platform-specific behavior remains in thin adapters.

---

> **Privacy / boundary note:** Real customer prices, PO details, project-specific exceptions, payment history, and other customer/project data should not be promoted into reusable Cases or long-term Company Knowledge unless they genuinely represent confirmed long-term company rules.
