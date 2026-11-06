# RUNNER-START｜As-Is Mapping Independent Test

你正在执行 TalkTrace v0.3.0-candidate 的独立方法测试。当前测试项目没有客户历史资料，也不应调用其他项目的记忆或历史上下文。

## 运行版本

TalkTrace 候选方法代码固定为：

`orinmuse/TalkTrace@722af25592962d462486a0e9ad0340067b7c33c7`

请从该 commit 读取：
- `SKILL.md`
- 本轮任务实际需要的 `references/interview-plan.md`
- `references/interview-guide.md`
- 后续日终批次需要时读取 `references/interview-delta.md`

如该 commit 无法读取，不得静默改用 main 或其他版本；说明阻断。

## 独立性要求

- 不调用其他项目历史、用户记忆或此前测试输出补充客户事实。
- 不读取 `REVIEWER-RUBRIC.md`、`evals/as-is-mapping.md`、其他阶段输入或任何 expected behavior。
- 每次只读取用户本轮指定的输入文件，以及运行当前任务必需的 Skill/Reference。
- 保留自然语言工作方式；不要要求用户填写额外表单或维护主题台账。
- D0、D1、D2 必须在同一测试会话内按顺序执行，以观察跨日更新；ORG-GRADE 必须在另一全新会话中执行。
- 不读取评分材料，不自评通过/失败，不修改 GitHub 文件。

## 输出要求

每轮完成后：
1. 给出本轮可直接用于咨询工作的成果；
2. 说明实际读取的运行文件和输入文件；
3. 保留已知、未知、来源范围和重要限定；
4. 不把正式制度直接当作实际执行证据；
5. 不把“了解现状”擅自升级为根因诊断或改革方案；
6. 不把源—点—线—面—果—环强加给管理体系现状摸底；
7. 不声称环境实现了无法审计的物理隔离。

完成每轮后等待下一份输入，不自行读取未来阶段文件。