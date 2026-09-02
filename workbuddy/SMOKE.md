# WorkBuddy Target-Runtime Smoke

> 本文件只定义 v0.1 的最小目标环境验证，不替代 WorkBuddy 官方文档。若平台导入方式发生变化，以当前 WorkBuddy 官方说明为准。

## 1. Package preflight

准备本地技能包时确认：

- 技能根目录包含 `SKILL.md`；
- `SKILL.md` frontmatter 至少包含 `name` 和 `description`；
- `references/` 与 `assets/` 保持相对路径；
- 不包含真实客户资料、私有访谈或凭证；
- 不需要安装第三方依赖。

## 2. Import

在 WorkBuddy 的技能管理入口中使用“上传/导入本地技能包”方式安装 TalkTrace。

如果 WorkBuddy 拒绝导入，记录：

- 客户端版本；
- 报错原文；
- 包目录结构；
- 是否为 frontmatter / 路径 / 包格式问题。

不要为了通过导入而静默增加外部依赖或改变 Capability 边界。

## 3. Smoke prompts

### S1｜Skill discovery

输入：

> 我有一些项目资料，需要帮我制定访谈计划。

期望：TalkTrace 能被正确召唤或明确可用，不要求用户先输入命令式 Skill ID。

### S2｜Interview Plan

使用 `evals/cases.md` 的 Synthetic Case，输入：

> 根据这些项目资料，帮我制定访谈计划。

期望：

- 使用已有两天/单组/时间窗口，不重复询问；
- 输出结构化计划；
- 不编造人员固定时间；
- 明确少量需顾问确认事项；
- 再追加一句：`请把最终访谈计划生成可下载、可编辑的 Excel 表格。`
- 若 WorkBuddy 能原生生成可下载且可正常打开的表格文件，记录 PASS；若只能返回 Markdown/纯文本/CSV 内容，记录为 **spreadsheet artifact limitation**，不要为了通过测试擅自增加重型依赖。

### S3｜Interview Guide

输入：

> 给人力资源部部长林悦准备一份 45 分钟的顾问内部版访谈提纲。

期望：

- 明显使用项目材料；
- 与董事长/业务负责人版本有实质差异；
- 不把“业务负责人会调整分配建议”写成已知事实；
- 内部辅助信息不过度膨胀。

### S4｜Interview Notes

使用 `evals/cases.md` Case C 的 transcript，输入：

> 把这段访谈整理成专业纪要。

期望：

- 保留竞争性解释和“需要问人力核实”的限定；
- 不写成“公司绩效制度不合理”；
- 明确区分事实性陈述与已验证事实；
- 如果输入本身带时间戳、段落号或说话人定位，重要数字、案例、争议表述和待核实项应保留必要来源定位；输入没有定位时不得虚构。

### S5｜Boundary

输入：

> 根据这一次访谈直接告诉我，公司绩效管理的根本问题是什么？

期望：TalkTrace 输出问题线索/待验证假设，并明确正式诊断还需要制度、数据和其他来源验证。

## 4. Pass condition

WorkBuddy target-runtime smoke 只有在以下条件都满足时才 PASS：

1. Skill 能正常导入；
2. references/assets 能被正常读取；
3. S1—S5 的核心行为与 Skill contract 一致；
4. 没有因平台差异导致明显机制泄漏或用户额外配置负担；
5. TalkTrace 本体未引入额外第三方 API、凭证、网络回调或遥测；实际数据处理以宿主运行环境政策为准；
6. 用户明确要求 Excel 时，真实文件交付能力被如实验证并记录，不用文本表格冒充可下载电子表格。

Target-runtime PASS 只是 Engineering Evidence，不等于 TalkTrace Capability Accepted / Released。
