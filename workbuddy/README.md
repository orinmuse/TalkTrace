# WorkBuddy packaging

TalkTrace v0.1 保持标准、可移植的轻量 Skill 结构。

面向 WorkBuddy 安装时，技能包至少保留：

```text
TalkTrace/
├── SKILL.md
├── references/
│   ├── project-memory.md
│   ├── interview-plan.md
│   ├── interview-guide.md
│   ├── interview-notes.md
│   └── interview-delta.md
└── assets/
    ├── project-memory-template.md
    ├── source-register-template.md
    ├── interview-plan-template.csv
    ├── interview-guide-client.md
    ├── interview-guide-internal.md
    └── interview-notes-template.md
```

`README.md`、`evals/`、`.github/`、`workbuddy/` 属于仓库维护与验收资产，不要求作为运行时 Skill 的必要内容。

## Runtime assumptions

TalkTrace 只依赖：

- WorkBuddy / 宿主模型能够读取用户当前提供的项目资料；
- WorkBuddy / 宿主环境能够持续访问并写入用户明确授权的本地项目文件夹；
- 新会话能够重新打开同一项目文件夹并读取 `talktrace/project-memory.md`；
- 宿主能够按用户要求输出其支持的文档/表格 artifact。

TalkTrace 不要求：

- 项目数据库或远程状态服务；
- RAG / 数据库；
- Agent；
- 专用文档转换服务；
- 用户私有知识库；
- 额外第三方 API、网络回调、凭证或遥测。

如果 WorkBuddy 无法持续读写同一个本地项目文件夹，应记录为 `persistent local-folder runtime blocker`；同一会话上下文不能替代跨会话持久化验证。如果某类文件读取或 artifact 生成超出当前能力，也应记录为 runtime limitation，不静默声称能力已经实现。

实际导入与验证步骤见 [SMOKE.md](SMOKE.md)。
