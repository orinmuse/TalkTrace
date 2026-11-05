# TalkTrace v0.2.0｜零项目记忆独立测试包

**用途：** 将 TalkTrace 当前 v0.2.0-candidate 放到一个完全不同、没有此前项目历史的 ChatGPT 项目/会话中，独立检验“资料预检→每天一批访谈纪要→跨日判断修正→次日行动”。这是一套可直接运行、可复核的测试输入，而非前一会话的结论拷贝。

**权限与证据等级：** 所有企业、项目、人员均为虚构。Runner 只读指定 Skill 和输入材料，不能从本帐号其他会话、既有用户记忆或私人项目补事实；原始输出先冻结，再向独立 Reviewer 暴露评分标准。公开测试包能帮助检查行为，但未运行时一律 `NOT TESTED`。不应将测试成功自动解释为真实客户现场效果通过。

## 你只需要做这些

1. 在一个新的、**没有原项目记忆**的 ChatGPT 项目开一个全新聊天。复制 [RUNNER-START.md](./RUNNER-START.md) 中的“首条启动提示词”，发送给测试模型。
2. 同一聊天严格按 D0 → D1 → D2 → D3 → N2 **逐批提交**，每批都让模型先完成结果，再发送下一批；测试模型不能预读未来批次。按 [RUNNER-LOG.md](./RUNNER-LOG.md) 保存原始回答。
3. **N1 必须在另一条真正隔离的全新会话/项目中运行**，该会话在首次回答前不得看到 D0/D1/D3、之前的回答或 Reviewer 文件。单纯“另开同项目聊天”如果仍可访问项目历史或共享文件，并不足以保证隔离。
4. 所有响应冻结后，再由**独立评审会话/模型**读取 [REVIEWER-RUBRIC.md](./REVIEWER-RUBRIC.md) 与 [REVIEW-RECORD.md](./REVIEW-RECORD.md) 评分。测试执行模型不要提前读取评审文件。
5. 将评测结果反馈给 Skill Manager 再决定正式接受、修复或保持候选。不要把开发 CI 通过等同于实际访谈效果。

## 两种使用方式

**A. GitHub 直接读取（推荐）**：新项目按 Runner 首条提示词读取 `main` 中的 `SKILL.md` 和 `references/`，再按阶段打开本目录单个输入文件。没有 GitHub 权限/文件读取工具时必须报告 `BLOCKED: SOURCE_UNAVAILABLE`，不能假装加载成功。

**B. 整包上传到新项目**：GitHub Actions `cold-start-test-kit` workflow 会生成可下载的 `TalkTrace-cold-start-runner-<sha>.zip`，其中只有 **11 个正式运行文件 + Runner 指南 + 分天虚构测试输入 + 记录模板**。不包含 Reviewer rubric、开发历史或测试期待答案。将整个 Runner 包作为新项目材料后，按 Runner 的本地文件路径分批运行；必须约束每一步不预读未来输入。

## 版本与边界

- 被测：`v0.2.0-candidate`，**不是正式发布**。
- 当前正式同事分发版仍是 `v0.1.1`。
- 仓库独立运行包：`packaging/runtime-files.txt` 定义的 **11** 文件；本测试文件不改变 Skill 运行包。
- 具体测试版本以运行时记录的 **GitHub commit SHA** 或 zip 包中的 `SOURCE-COMMIT.txt` 为准。请勿只写“最新 main”；后续变更会影响可重复性。
- 所有测试都是虚构证据，仅能测行为和防回归；要证明改善顾问工作仍需要授权真实项目观察。
- **只上传经过确认可公开的信息**。如果后来换成真实客户材料，不要上传到公开 GitHub，且独立测试授权范围必须明确。

## 测试材料目录

- `RUNNER-START.md`：新项目复制的启动提示词与逐批指令，**不含答案**。
- `inputs/D0.md`—`inputs/D3.md`：同一虚构项目的逐日事实。
- `inputs/N1.md`：真正隔离的缺历史负例。
- `inputs/N2.md`：原会话里的同源重复负例。
- `RUNNER-LOG.md`：原始输出记录模板。
- `REVIEWER-RUBRIC.md`：独立评审端使用，**不能提前给测试执行模型**。
- `REVIEW-RECORD.md`：评审结论填写模板。

## 项目收尾状态

开发成果与测试包集成到 GitHub 并不意味着独立行为验收完成。开发 Issue / PR 可以按 Skill Manager 的候选集成裁决收口；正式 v0.2.0 发布、版本晋级和实际用户价值结论必须待独立验证回传后另行裁决。
