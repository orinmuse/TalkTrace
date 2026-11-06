# RUNNER-PRACTICE-START｜v0.3.0 Practice-Tracing Regression

本轮用于检查 CR-05 将源—点—线—面—果—环降级为条件性方法后，TalkTrace 是否仍能正确处理具体业务实践调查。该测试必须在**全新、无项目记忆**的独立会话中运行。

## 被测运行版本

TalkTrace 运行文件固定为：

`orinmuse/TalkTrace@722af25592962d462486a0e9ad0340067b7c33c7`

从该 commit 读取 `SKILL.md`，并按路由读取 `references/interview-plan.md`、`references/interview-guide.md`、`references/interview-delta.md`。不得用 main 或其他版本替代。

## 输入版本

使用原始合成测试材料固定版本：

`orinmuse/TalkTrace@d4b0cd4a28b12277932911a50f025e16da4181dc`

只按阶段逐个读取：
- D0：`evals/cold-start-kit/inputs/D0.md`
- D1：`evals/cold-start-kit/inputs/D1.md`
- D2：`evals/cold-start-kit/inputs/D2.md`
- D3：`evals/cold-start-kit/inputs/D3.md`
- N2：`evals/cold-start-kit/inputs/N2.md`
- N1：`evals/cold-start-kit/inputs/N1.md`（另一个真正隔离的新会话）

## 隔离规则

- 不调用其他项目历史、用户记忆、此前测试输出或客户资料。
- 不读取 `evals/cold-start-kit/RUNNER-START.md`（它是 v0.2.0 旧 Runner 指令）、`REVIEWER-RUBRIC.md`、`REVIEW-RECORD.md` 或任何 expected behavior。
- D0→D1→D2→D3→N2 在同一测试会话内逐批执行；每次只读当前阶段输入。
- N1 在另一条真正隔离的新会话中运行，不能看到 D0—D3/N2 历史。
- 如果测试环境无法读取指定版本或无法保证未来阶段输入隔离，记录 BLOCKED/CONTAMINATED，不模拟通过。

## 每阶段任务

- **D0**：进行跨专业资源协调的进场前资料预检，准备第一场经营计划部访谈。
- **D1**：处理一个部门的日终纪要，更新认识并调整 D2 设计院访谈。
- **D2**：处理业务部门反向信息，修正对 OA 与实际协调的理解，调整 D3 项目经理访谈。
- **D3**：分析具体项目工作样本，区分申请、审批、人员安排、实际到岗和投入。
- **N2**：判断重复制度材料是否产生实质增量。
- **N1**：在无历史资料时诚实降级，不虚构跨日比较。

完成后保留所有原始回答和实际文件读取记录，交给独立 Reviewer。不得自行评分或写回 GitHub。