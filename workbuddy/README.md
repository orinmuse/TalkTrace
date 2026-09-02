# WorkBuddy packaging

TalkTrace v0.1 保持标准、可移植的 Skill 结构。

面向 WorkBuddy 安装时，技能包至少保留：

```text
TalkTrace/
├── SKILL.md
├── references/
│   ├── interview-plan.md
│   ├── interview-guide.md
│   └── interview-notes.md
└── assets/
    ├── interview-plan-template.csv
    ├── interview-guide-client.md
    ├── interview-guide-internal.md
    └── interview-notes-template.md
```

`README.md`、`evals/`、`.github/`、`workbuddy/` 属于仓库维护与验收资产，不要求作为运行时 Skill 的必要内容。

TalkTrace 本体不增加额外第三方 API、网络回调、凭证或遥测；WorkBuddy 中实际模型调用、文件处理与数据传输仍受 WorkBuddy / 企业运行环境的数据与权限政策约束。

实际导入与验证步骤见 [SMOKE.md](SMOKE.md)。
