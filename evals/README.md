# TalkTrace Eval Topology

## Purpose

TalkTrace 的公开仓库测试分为两类：

1. **Regression evidence**：用于防止已知方法缺陷和公开产品体验回归；
2. **Capability Acceptance evidence**：由 Skill Manager 在候选版本冻结后另行预注册、隔离执行和盲评。

公开 regression case 可以被实现过程读取，因此不能因为工程实现已经通过公开 expected behavior，就单独用来宣称 Capability Accepted。

## Public regression set

### `cases.md`

保留旧 v0.1 的 Plan / Senior Guide / Functional Guide / Business Guide / Notes / Degraded / Diagnosis Boundary 场景。

它们现在主要承担：

- 旧失败机制回归；
- 角色差异；
- premise safety；
- 来源纪律；
- 降级与诊断边界；
- Excel artifact 行为。

旧 P1–P7 已经在历史 paired eval 中暴露给实现过程，因此不再作为新版唯一 decisive held-out set。

### `cold-start.md`

验证 Public / Standalone edition 的首次使用体验：

> 第一次接触 TalkTrace 的用户使用普通自然语言时，Skill 是否能自然进入正确任务、先给有用初稿，并只追问真正必要的信息。

重点覆盖：

- `这是客户资料，帮我准备一下访谈。` 这类 broad ask；
- 指定受访者但项目背景不足；
- 没有正式排程约束时先输出 Quick Plan；
- 用户用自然语言要求“更新下一场访谈”而不需要理解 `Delta`；
- 不把内部 Workflow / Schema / epistemic state 暴露为用户必须学习的操作步骤。

这是公开产品化 regression，不替代 held-out Outcome Eval。

### `sequential-context.md`

验证新版核心机制：

> Interview N 进入当前上下文后，TalkTrace 是否能识别新增/冲突/待验证，并实质改善 Interview N+1。

这是公开工程 regression case，不是最终 sealed acceptance case。

### `premise-safety.md`

针对 Work-mode behavioral verification 在 frozen HEAD `8c9ba8caaeeff4a418c65e69fd33d3d58f69091b` 暴露的弱语义前提问题，验证：

- existence presupposition；
- continuation / follow-up presupposition；
- single-case → recurring mechanism generalization；
- actor / authority presupposition；
- sequence / mechanism invention；
- causal presupposition；
- 条件句中仍然隐藏的未确认前提。

目的不是维护关键词黑名单，而是验证一般的 semantic premise preflight。

## Final Capability Acceptance

新版候选冻结后，由 Skill Manager 另行预注册未暴露的 held-out cases，并至少覆盖：

- cold-start / first-time-user usability；
- 信息缺口驱动的 Interview Plan；
- senior / functional / business role differentiation；
- premise-neutrality，包括弱语义前提与 case-to-mechanism 泛化；
- source / uncertainty discipline；
- insufficient-input degradation；
- diagnosis boundary；
- sequential interview delta / next-guide improvement。

正式 Outcome Eval 继续采用：

> 同一模型 + 同一输入 + 同一自然语言请求，TalkTrace vs no-Skill baseline，隔离生成 + 盲评。

不得因为新版 regression PASS 而降低 baseline comparison 门槛。
