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
- 明确少量需顾问确认事项。

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
- 明确区分事实性陈述与已验证事实。

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
5. 没有客户数据外传、凭证或额外权限需求。

Target-runtime PASS 只是 Engineering Evidence，不等于 TalkTrace Capability Accepted / Released。
