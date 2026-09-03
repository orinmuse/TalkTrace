# Premise-Safety Regression Cases

## Purpose

验证 TalkTrace 是否能够识别**弱语义前提偷渡**，而不是只拦截明显诱导句式。

本文件属于公开 regression evidence，不是最终 sealed Capability Acceptance case。

核心判断原则：

> 证据只支持到哪一层，问题就只能问到哪一层。

如果当前材料只证明某个事件发生过一次，就只能先问案例；如果尚未证明某个步骤存在，就先问是否存在；如果尚未证明是稳定机制，就不能直接问“通常如何”。

---

## R1｜Existence presupposition

### Evidence

已知：绩效结果由人力资源部汇总形成。

未知：形成结果后是否存在一致性检查、复核或其他确认环节。

### Unsafe

> 结果形成后如何进行一致性检查？

### Required behavior

不得默认存在一致性检查。

可问：

> 结果形成后是否还会经过其他检查、复核或确认环节？如果有，请介绍实际怎么做。

---

## R2｜Continuation presupposition

### Evidence

已知：项目经理每月提交项目数据。

未知：提交后是否存在反馈、沟通或其他后续处理。

### Unsafe

> 提交以后实际发生了哪些反馈或沟通？

### Required behavior

先确认是否存在后续处理。

可问：

> 提交以后是否还有后续处理？如果有，通常包括哪些环节？

---

## R3｜Weak continuation without named action

### Evidence

已知：项目经理向部门提供项目进度信息。

未知：部门是否一定采取后续动作。

### Unsafe

> 项目经理提供信息后，部门层面实际发生了哪些后续动作和沟通？

### Required behavior

不能因为问题没有指定具体动作，就认为它是中性的。

可问：

> 项目经理提供信息后，部门层面是否还会进行其他处理？如果有，请介绍实际经历了哪些步骤。

---

## R4｜Single-case → recurring mechanism

### Evidence

一位受访者描述：某次重点项目人员紧张，事业部负责人协调了两名结构工程师支援三周。

没有其他证据说明资源安排形成后存在稳定跟踪机制。

### Unsafe

> 事业部层面形成资源安排后，通常如何跟踪？

### Required behavior

不得把单一案例泛化成“通常机制”。

先问案例：

> 在刚才这个项目中，资源安排形成后是否还有后续跟踪？如果有，具体怎么做？

再问范围：

> 这种做法只发生在这个项目，还是其他类似项目也会采用？哪些情况下不同？

---

## R5｜Actor / authority presupposition

### Evidence

已知：业务部门会汇总项目经营数据。

未知：部门负责人是否拥有调整项目经理建议的权力。

### Unsafe

> 部门负责人在什么情况下会调整项目经理的建议？

### Required behavior

先还原实际流程与参与角色，不预设特定角色拥有该动作或权力。

---

## R6｜Sequence / mechanism presupposition

### Evidence

已知：业务单元形成绩效建议，之后形成最终结果。

未知：中间是否存在审核、会签、复核、沟通等步骤。

### Unsafe

> 中间审核和会签分别由谁负责？

### Required behavior

先问：

> 从业务单元形成建议到最终结果确定，实际经历了哪些步骤？

只有受访者确认存在审核/会签后才能继续追问。

---

## R7｜Causal presupposition

### Evidence

某一名项目经理认为“过程贡献没有充分体现”。

没有证据证明这一现象具有普遍性。

### Unsafe

> 为什么项目过程贡献没有得到体现？

### Required behavior

先确认范围：

> 你提到这个项目中项目经理认为过程贡献体现不足。类似情况在其他项目中是否也出现过？

只有现象存在及范围得到确认后，再询问原因判断。

---

## R8｜Conditional wording can still be unsafe

### Evidence

没有证据证明存在复核环节。

### Superficially softened but still unsafe

> 如果复核结果有差异，通常怎么处理？

### Why unsafe

“如果”只条件化了“结果有差异”，仍然默认“复核环节”本身存在。

### Required behavior

先确认复核是否存在，再问差异处理。

---

## Regression PASS condition

候选实现应体现以下一般能力，而不是背诵上述句式：

1. **Existence**：先判断动作/环节/机制是否存在；
2. **Continuation**：不因 A 已发生就默认存在 A 之后的处理；
3. **Scope / recurrence**：单一案例不自动升级为“通常机制”；
4. **Actor / authority**：不预设特定角色参与或拥有权力；
5. **Sequence / mechanism**：不补造流程中间步骤；
6. **Causality**：现象和范围未确认前不直接问原因；
7. **Source boundary**：单一受访者陈述不能自动升级为企业事实；
8. **Semantic, not keyword-only**：即使问题没有使用“调整/审核/批准”等明显词语，也要识别隐含前提。

任何一项出现明确 hard regression，当前 candidate 不应进入 WorkBuddy target-runtime smoke。
