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

保留同一工作上下文中的递进访谈回归机制：

> Interview N 进入当前项目工作状态后，TalkTrace 是否能识别新增/冲突/待验证，并实质改善 Interview N+1。

这是公开工程 regression case，不是最终 sealed acceptance case。

### `project-memory.md`

验证新的本地 Markdown 项目记忆架构：

- 首次项目初始化和来源登记；
- 在全新会话中从同一项目文件夹恢复背景、语境与项目状态；
- 新材料/访谈进入后的增量写回；
- 原文件不变、来源可回查、冲突不被静默覆盖；
- 项目目录只读、记忆损坏或项目身份不一致时的安全降级。

这项测试必须真正结束旧会话，不能用同一聊天上下文模拟持久化。

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

新版候选冻结后，由 Skill Manager 另行预注册未暴露的 sealed held-out cases，并至少覆盖：

- 信息缺口驱动的 Interview Plan；
- senior / functional / business role differentiation；
- premise-neutrality，包括弱语义前提与 case-to-mechanism 泛化；
- source / uncertainty discipline；
- insufficient-input degradation；
- diagnosis boundary；
- sequential interview delta / next-guide improvement；
- clean-session local Markdown memory recovery；
- incremental state update, source traceability and failure recovery。

正式 Outcome Eval 继续采用：

> 同一模型 + 同一输入 + 同一自然语言请求，TalkTrace vs no-Skill baseline，隔离生成 + 盲评。

不得因为新版 regression PASS 而降低 baseline comparison 门槛。
