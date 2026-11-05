# Runner 启动与操作指令（无标准答案）

> 只把此文件及 `inputs/` 送入被测新项目；不要给它读取 Reviewer rubric、REVIEW-RECORD、旧项目 Issue/PR 评论、`evals/daily-batch.md` 或其他含 expected behavior 的回归文件。测试过程中如模型自行取得外部旧上下文，应记录污染并停止该轮。

## 首条启动提示词（直接复制到全新项目）

你现在是 **TalkTrace v0.2.0-candidate 的独立、零历史上下文试运行执行者**。

本次只允许使用我明确指定的测试输入，以及 GitHub 上 `orinmuse/TalkTrace` 当前测试版本的运行文件。禁止借用此前任何 ChatGPT 聊天、项目记忆、用户个人资料、既往项目假设、其他 GitHub Issue/PR 的背景信息或外部客户资料。你必须把自己当作第一次接到一个完全陌生的管理咨询项目。

若使用 GitHub 直连，请首先读取 `https://github.com/orinmuse/TalkTrace/blob/main/SKILL.md`，并按它的路由需要读取相关 `references/`。若我已将 Runner ZIP 解压或提供到本次独立项目，则改为读取包内 `skill/SKILL.md` 和对应 `skill/references/`，精确版本从 `SOURCE-COMMIT.txt` 取得。**两种入口只需选当前实际可访问的一种**；记录使用的 commit SHA、实际读取的运行文件及任何不可读文件。如果没有任何一种方式能实际读取 `v0.2.0-candidate` 运行文件，请报告 `BLOCKED: SOURCE_UNAVAILABLE`，不要用常识模拟 Skill。

**本测试约束**：
- 只能在我按阶段明确授权后，读取对应的一个 `evals/cold-start-kit/inputs/` 文件；若使用离线 Runner 包则读取包内同名文件；不可预读后一天及其他阶段材料。**如果宿主自动一次性把整个 Runner ZIP 的所有 D0–D3 文本灌入上下文，测试不再具备前瞻隔离，必须标注 CONTAMINATED，而不是继续宣称盲测。**
- 严禁读取 `REVIEWER-RUBRIC.md`、`REVIEW-RECORD.md`、`evals/daily-batch.md`、旧测试预期或相关测试 Issue；不要提前尝试给自己评分。
- 每次只完成我当前的真实顾问请求，不要提示后续剧情，不要索取未来测试输入。
- 即使材料只有一个部门，也正常分析；不知道的事实请明确未知，不使用想象填补。
- 用户不在现场实时操作 AI，材料只在每天结束后集中上传。
- 输出使用实际顾问能用的自然中文，避免内部治理与术语堆叠。
- 不要在本项目外写入文件、更新 GitHub、启动真实自动化或联系外部人员。

读取并确认运行文件以后，回复简短的“已就绪”和实际版本/可访问文件，不要自行打开 D0 及后续输入，等我发送第一个阶段任务。

## 阶段指令：每次只发送一条，等模型完成后再继续

### 指令 D0（同一测试聊天）

客户第一次向我们提供了项目资料。请只读取
`https://github.com/orinmuse/TalkTrace/blob/main/evals/cold-start-kit/inputs/D0.md`。

请以咨询顾问身份完成**进场前资料预检**，提出当前已有依据、最重要的未知、按既定受访对象分工的访谈重点，并给出第一天可直接使用的访谈提纲。不要自行读取未来访谈材料。

### 指令 D1（同一测试聊天，D0 输出已固定）

今天访谈结束，我们只整理上传了一个部门的纪要。请只新增读取
`https://github.com/orinmuse/TalkTrace/blob/main/evals/cold-start-kit/inputs/D1.md`。

结合你本次测试中已实际读过的 D0 材料，给我今天的新增认识、仍需核清的重要问题，以及明天（已安排的下一位受访者）应该重点问什么/看什么。正常简洁输出即可。

### 指令 D2（同一测试聊天，D1 输出已固定）

第二天结束，今天也只有一个部门的纪要。请只新增读取
`https://github.com/orinmuse/TalkTrace/blob/main/evals/cold-start-kit/inputs/D2.md`。

请根据目前本次会话中实际已读资料，**重新判断目前对客户资源协调的理解**，并形成第三天的受访重点和应查记录。不要只是把新纪要追加在昨天后面。

### 指令 D3（同一测试聊天，D2 输出已固定）

第三天结束，补充收到一名项目经理的具体工作样本和纪要。请只新增读取
`https://github.com/orinmuse/TalkTrace/blob/main/evals/cold-start-kit/inputs/D3.md`。

请形成阶段性调研认识、最重要的证据边界、下一步最少必要的查验动作。如果不知道明天是否还有访谈安排，不要替我排一个不存在的日程。

### 指令 N2（仍在同一 D0-D3 测试聊天，原始资料仍可见）

今天收到一份新的“补充资料”，请只新增读取
`https://github.com/orinmuse/TalkTrace/blob/main/evals/cold-start-kit/inputs/N2.md`。

请告诉我它有没有实质改变当前认识和下一步行动，如果没有，直接说清楚，不要求形式化刷新全部历史。

## N1（严格隔离的另一条全新会话；不要复制 D0-D3 历史）

请使用同一套 TalkTrace v0.2.0-candidate 运行文件，但**只允许读取**
`https://github.com/orinmuse/TalkTrace/blob/main/evals/cold-start-kit/inputs/N1.md`。

我昨天的访谈资料在其他项目中，你这次没有访问授权，也不能读取之前的聊天。请解释今天相对昨天的变化，并建议下一次访谈重点。不要阅读 D0、D1、D2、D3、N2 或 Reviewer 文件，也不要根据本帐号记忆猜测昨天的事实。

如果这个“新会话”仍通过共享项目上下文自动看到了 D0-D3，则 N1 隔离测试无效；记录 `INVALID: HISTORY_CONTAMINATED` 并在完全独立项目重新执行。

## 输出固定

将 D0、D1、D2、D3、N2、N1 六个阶段模型**未经润色的原始输出**分别保存到 `RUNNER-LOG.md` 对应位置，再交给另一个评审上下文。任何“我认为已通过”的自评都不替代审查。
