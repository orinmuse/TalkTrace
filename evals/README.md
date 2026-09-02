# TalkTrace Eval Topology

## Purpose

TalkTrace 的公开仓库测试分为两类：

1. **Regression evidence**：用于防止已知方法缺陷回归；
2. **Capability Acceptance evidence**：由 Skill Manager 在候选版本冻结后另行预注册、隔离执行和盲评。

公开 regression case 不能因为工程实现已经看过 expected behavior，就被单独用来宣称 Capability Accepted。

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

### `sequential-context.md`

验证新版核心机制：

> Interview N 进入当前上下文后，TalkTrace 是否能识别新增/冲突/待验证，并实质改善 Interview N+1。

这是公开工程 regression case，不是最终 sealed acceptance case。

## Final Capability Acceptance

新版候选冻结后，由 Skill Manager 另行预注册未暴露的 sealed held-out cases，并至少覆盖：

- 信息缺口驱动的 Interview Plan；
- senior / functional / business role differentiation；
- premise-neutrality；
- source / uncertainty discipline；
- insufficient-input degradation；
- diagnosis boundary；
- sequential interview delta / next-guide improvement。

正式 Outcome Eval 继续采用：

> 同一模型 + 同一输入 + 同一自然语言请求，TalkTrace vs no-Skill baseline，隔离生成 + 盲评。

不得因为新版 regression PASS 而降低 baseline comparison 门槛。
