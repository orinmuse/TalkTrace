# WorkBuddy Target-Runtime Smoke

> 本文件定义 v0.1 rework 的最小目标环境验证，不替代 WorkBuddy 官方文档。平台导入方式变化时，以当前官方说明为准。

## 1. Package preflight

准备技能包时确认：

- 根目录包含 `SKILL.md`；
- `SKILL.md` frontmatter 至少包含 `name` 和 `description`；
- `references/` 与 `assets/` 保持相对路径；
- `references/interview-delta.md` 被包含；
- 不包含真实客户资料、私有访谈或凭证；
- 不需要安装第三方依赖；
- 不要求项目状态文件、数据库、RAG 或 Agent。

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

期望：TalkTrace 能被正确召唤或明确可用，不要求用户先输入命令式 Skill ID、初始化项目或创建状态文件。

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

- 保留竞争性解释和“需要问人力核实”的限定；
- 不写成“公司绩效制度不合理”；
- 不把“项目过程贡献没有进入绩效”写成已验证企业事实；
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

期望：输出问题线索、竞争性解释、待验证假设和验证路径，不升级成正式企业根因诊断。

---

### S6｜Sequential Interview Delta / Refresh

使用 `evals/sequential-context.md`。

#### Step 1

提供该文件的项目背景、已知材料和角色信息，生成项目经理陈柏的 35 分钟顾问内部提纲。

#### Step 2

在**同一个 WorkBuddy 工作上下文**中加入陈柏 transcript。

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

**S6 是新版 v0.1 的核心 smoke。** 如果无法在同一当前上下文中利用前序访谈改进下一场提纲，记录 FAIL 或明确 runtime context limitation；不得通过增加持久数据库/RAG/Agent 来静默修复。

## 4. Pass condition

WorkBuddy target-runtime smoke 只有在以下条件都满足时才 PASS：

1. Skill 能正常导入；
2. references/assets 能正常读取；
3. S1—S6 的核心行为与 Skill contract 一致；
4. S3 无 premise-safety hard fail；
5. S6 能使用当前上下文产生实质的 interview delta 和 next-guide improvement；
6. 没有因平台差异导致明显机制泄漏或用户额外配置负担；
7. TalkTrace 本体未引入额外第三方 API、凭证、网络回调、遥测、持久状态或 RAG；
8. 用户要求 Excel 时，真实文件能力被如实验证，不用文本表格冒充。

Target-runtime PASS 只是 Engineering Evidence，不等于 TalkTrace Capability Accepted / Released。
