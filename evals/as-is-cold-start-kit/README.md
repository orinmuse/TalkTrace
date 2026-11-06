# As-Is Mapping Independent Runner Kit

本测试包用于在**全新、无 TalkTrace 项目历史记忆的独立会话/项目**中验证 CR-05 的候选方法。

## Runner / Reviewer 隔离

- Runner 只读取 `RUNNER-START.md`、指定输入文件，以及 TalkTrace 候选运行文件。
- Runner 不得读取 `REVIEWER-RUBRIC.md`、`evals/as-is-mapping.md` 或其他阶段输入。
- 每个输入按指定顺序在同一独立测试会话中执行；跨日批次用例需要保留同一测试会话。
- 完成后，将每轮完整原始回答、实际读取文件、运行版本、文件 SHA 和任何环境限制交给 Reviewer。
- Reviewer 在原始回答冻结后才读取对应 Rubric。As-Is 用 `REVIEWER-RUBRIC.md`；实践穿透回归用 `REVIEWER-PRACTICE-RUBRIC.md`。不得事后润色或重构 Runner 输出。

## 推荐测试顺序

1. `RUNNER-START.md`：初始化与运行约束。
2. `inputs/D0.md`：薪酬绩效体系现状调查进场准备。
3. `inputs/D1.md`：HR 单部门日终批次。
4. `inputs/D2.md`：财务部门补充信息，更新主题地图与下一场访谈。
5. `inputs/ORG-GRADE.md`：在另一个全新会话中测试方法迁移。

## 边界

这是针对性独立行为测试，不等于正式验收，不证明 WorkBuddy 目标运行时通过，也不证明真实客户项目成效。测试输入均为合成材料。