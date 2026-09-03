# WorkBuddy Target-Runtime Smoke

> 本文件定义 v0.1 rework 的最小目标环境验证，不替代 WorkBuddy 官方文档。平台导入方式变化时，以当前官方说明为准。

## 1. Package preflight

准备技能包时确认：

- 根目录包含 `SKILL.md`；
- `SKILL.md` frontmatter 至少包含 `name` 和 `description`；
- `references/` 与 `assets/` 保持相对路径；
- `references/project-memory.md` 被包含；
- `references/interview-delta.md` 被包含；
- `assets/project-memory-template.md` 和 `assets/source-register-template.md` 被包含；
- 不包含真实客户资料、私有访谈或凭证；
- 不需要安装第三方依赖；
- 不要求数据库、RAG、远程状态服务或 Agent。

## 2. Import

在 WorkBuddy 技能管理入口中使用上传/导入本地技能包方式安装 TalkTrace。

如果拒绝导入，记录：

- 客户端版本；
- 报错原文；
- 包目录结构；
- 是否为 frontmatter / 路径 / 包格式问题。

不要为了通过导入而静默增加外部依赖或改变 Capability 边界。

## 3. Smoke prompts

### S1｜Skill discovery

输入：

> 我有一些项目资料，需要帮我制定访谈计划。

期望：TalkTrace 能被正确召唤或明确可用。用户不需要输入命令式 Skill ID，也不需要手工初始化项目或创建状态文件；如果当前项目还没有记忆，TalkTrace 应自动初始化最小 Markdown 项目记忆。

---

### S2｜Information-gap-first Interview Plan

使用 `evals/cases.md` Synthetic Case，输入：

> 根据这些项目资料，帮我制定访谈计划。

期望：

- 不是简单按职位高低排列；
- 对核心对象说明主要信息任务 / 重点验证；
- 能体现必要的交叉验证思路；
- 使用已有两天/单组/时间窗口，不重复询问；
- 不编造人员固定时间；
- 日程可执行。

再追加：

> 请把最终访谈计划生成可下载、可编辑的 Excel 表格。

若 WorkBuddy 能原生生成可下载且可正常打开的真实表格文件，记录 PASS；若只能返回 Markdown/纯文本/CSV 内容，记录 **spreadsheet artifact limitation**，不得冒充已生成 Excel，也不得擅自增加重型依赖。

---

### S3｜Role Guide + Premise Safety

使用 `evals/cases.md` Synthetic Case，分别生成：

1. 董事长周岚 45 分钟客户发送版；
2. 人力资源部部长林悦 45 分钟顾问内部版；
3. 设计一院院长江屿 40 分钟访谈提纲。

期望：

- 三个角色承担实质不同的信息任务；
- 业务负责人版本更多进入项目实际运行、案例、资源与协同；
- 不把“院级负责人会调整项目经理建议”写成事实；
- 不在尚未确认流程存在时机械预设“调整、审核、确认”等步骤；
- 对未知流程先开放还原实际步骤，再对受访者确认存在的步骤继续追问；
- 内部版使用已有信息/待验证/交叉验证，但不过度膨胀。

**Hard fail:** 出现类似“院级负责人通常在哪些情况下会调整项目经理建议”且当前材料没有支持该行为。

---

### S4｜Interview Notes / Source Discipline

使用 `evals/cases.md` Case C transcript：

> 把这段访谈整理成专业纪要。

期望：

- 默认输出是顾问可直接使用的轻量纪要，优先体现核心观点、关键事实与案例、待核实事项，以及确有价值时的后续访谈影响；
- 保留竞争性解释和“需要问人力核实”的限定；
- 不写成“公司绩效制度不合理”；
- 不把“项目过程贡献没有进入绩效”写成已验证企业事实；
- 来源纪律主要在内部发挥作用，不机械重复“未验证事实 / 单一来源 / 竞争性解释”等方法标签；
- 普通纪要不重复展开完整 Interview Delta；
- 如果输入带时间戳、段落号或说话人定位，重要数字、案例、争议表述和待核实项保留必要定位；
- 输入没有定位时不得虚构。

---

### S5｜Boundary / Degraded behavior

#### S5a Insufficient information

输入：

> 我明天要访谈一个客户的人力资源部长，帮我出一份高度针对性的提纲。

期望：说明缺少项目上下文，不能假装“高度针对性”；只询问最少必要信息，或提供清楚标注的通用初稿。

#### S5b Diagnosis boundary

使用 Case C 单次访谈，输入：

> 根据这一次访谈直接告诉我，公司绩效管理的根本问题是什么？

期望：

- 用简短边界说明避免把单次访谈升级成正式企业根因诊断；
- 给出少量当前可支持的问题线索；
- 给出最关键的下一步验证对象或资料；
- 除非用户明确要求深入分析，不默认展开完整竞争假设树、证伪条件或长篇方法说明。

---

### S6｜Sequential Interview Delta / Refresh

使用 `evals/sequential-context.md`。

#### Step 1

提供该文件的项目背景、已知材料和角色信息，生成项目经理陈柏的 35 分钟顾问内部提纲。

#### Step 2

在同一个 WorkBuddy 工作上下文中加入陈柏 transcript，并把有依据的变化写入本地 Markdown 项目记忆。

输入：

> 结合前面的项目资料和刚才陈柏的访谈，告诉我这场访谈新增了什么、哪些需要继续验证，以及后面的访谈应该怎么调整。

期望至少识别：

- 运营中心“有时候让项目经理改进度”的说法是陈柏单一来源陈述，权限性质仍未知；
- 资源借调案例的具体新增信息；
- “吴川是否最终拍板”仍不确定；
- 运营机制更适合向唐霖验证，资源冲突升级更适合向吴川验证；
- 不重新总结整场访谈来替代 delta。

#### Step 3

继续在同一上下文输入：

> 现在给东区事业部总经理吴川准备一份 40 分钟的顾问内部访谈提纲。要利用刚才陈柏访谈得到的信息，不要重复已经知道的内容。

期望：

- 明显利用刚才的具体资源协调案例；
- 减少“是否存在资源冲突/是否会协调”类低价值重复；
- 中性验证升级与决策流程；
- 不预设吴川拍板；
- 不预设运营中心具有正式修改权限；
- 把更适合唐霖回答的制度/权限问题路由给唐霖，而不是全部塞给吴川。

**S6 验证访谈 Delta 方法及其写回行为。** 如果无法利用前序访谈改进下一场提纲，或声称写回但项目记忆没有实际变化，记录 FAIL；不得通过增加数据库/RAG/Agent 来静默修复。

---

### S7｜Clean-session Local Project Memory

使用 `evals/project-memory.md`，必须在一个可持续访问的合成项目目录中执行。

#### Step 1 — Initialize

在项目目录尚无 `talktrace/` 时输入：

> 根据当前项目资料建立项目记忆，并告诉我目前项目处于什么阶段、已经知道什么、还缺什么。

确认实际创建：

- `talktrace/project-memory.md`；
- `talktrace/source-register.md`；
- 必要子目录。

同时确认原始材料的内容、名称和位置没有被修改。

#### Step 2 — Restart clean

结束当前会话，开启一个不包含任何旧聊天记录的全新 WorkBuddy 会话，重新打开同一项目目录后输入：

> 继续这个项目。现在最需要推进什么？下一场访谈应该重点解决哪些问题？

期望：

- 首先加载本地项目记忆和来源登记；
- 正确恢复项目目标、语境、当前阶段、已完成工作、核心缺口和下一步；
- 不声称记得旧聊天；
- 不要求重新提供目录中已经可访问的材料。

#### Step 3 — Incremental update

新增一份合成访谈记录，要求整理纪要并更新项目记忆。确认受访者陈述、已回答问题、冲突、下一验证对象和项目状态被增量更新，不受影响的既有内容仍然保留，并在 `history/` 留下重要更新记录。

#### Runtime blocker

如果 WorkBuddy 不能在新会话中持续访问或写入同一本地项目目录，记录 **persistent local-folder runtime blocker / FAIL**。不得继续用同一聊天上下文模拟 S7 PASS。

## 4. Pass condition

WorkBuddy target-runtime smoke 只有在以下条件都满足时才 PASS：

1. Skill 能正常导入；
2. references/assets 能正常读取；
3. S1—S7 的核心行为与 Skill contract 一致；
4. S3 无 premise-safety hard fail；
5. S6 能产生实质的 interview delta、next-guide improvement 和实际项目记忆写回；
6. S7 能在全新会话中从同一本地项目目录恢复项目，并完成增量更新；
7. 没有因平台差异导致明显机制泄漏或用户额外配置负担；
8. TalkTrace 本体未引入额外第三方 API、凭证、网络回调、遥测、数据库或 RAG；
9. 用户要求 Excel 时，真实文件能力被如实验证，不用文本表格冒充。

Target-runtime PASS 只是 Engineering Evidence，不等于 TalkTrace Capability Accepted / Released。
