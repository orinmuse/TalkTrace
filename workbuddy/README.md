# WorkBuddy packaging

TalkTrace v0.1.1 保持标准、可移植的轻量 Skill 结构。

面向 WorkBuddy 安装时，技能包至少保留：

```text
TalkTrace/
├── SKILL.md
├── references/
│   ├── interview-plan.md
│   ├── interview-guide.md
│   ├── interview-notes.md
│   ├── interview-delta.md
│   └── company-interview-guide.md
└── assets/
    ├── interview-plan-template.csv
    ├── interview-guide-client.md
    ├── interview-guide-internal.md
    ├── interview-notes-template.md
    └── interview-guide-company-client.md
```

`README.md`、`evals/`、`.github/`、`workbuddy/` 属于仓库维护与验收资产，不要求作为运行时 Skill 的必要内容。

## Runtime assumptions

TalkTrace 只依赖：

- WorkBuddy / 宿主模型能够读取用户当前提供的项目资料；
- 当前对话/工作上下文能够保留本轮需要使用的前序资料和访谈信息；
- 宿主能够按用户要求输出其支持的文档/表格 artifact。

TalkTrace 不要求：

- 持久项目状态文件；
- RAG / 数据库；
- Agent；
- 专用文档转换服务；
- 用户私有知识库；
- 额外第三方 API、网络回调、凭证或遥测。

如果某类文件读取、上下文长度或 artifact 生成超出 WorkBuddy 当前能力，应记录为 runtime limitation，不静默扩展 Capability 架构。

实际导入与验证步骤见 [SMOKE.md](SMOKE.md)。

## v0.1.1 distribution

使用 `TalkTrace-v0.1.1-WorkBuddy.zip`。在技能管理入口导入；若入口要求目录，则解压后选择含有 SKILL.md 的 TalkTrace 文件夹。已有同名技能时先备份，再升级；避免重复安装两个同名版本。首次开启新会话，确认可读取公司 profile 后再试用。此包已验证文件与引用完整，不将其等同于 WorkBuddy 目标环境实测通过。
