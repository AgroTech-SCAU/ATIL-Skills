# AgroTech Innovation Lab · 通知写作 Skills

本仓库维护 AgroTech Innovation Lab 的通知写作 Skill，为成员管理、项目协作、比赛组织等场景提供中文通知与私聊回复的写作支持

目前包含 `agrotech-notices`，可用于起草新通知、润色已有文稿，以及参考已整理的八类常用模板

## 快速开始

本仓库是 Skill 文档集合，不需要编译、ROS 或专用硬件

### Windows PowerShell

```powershell
git clone https://github.com/AgroTech-SCAU/agrotech-notices.git
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
Copy-Item -Recurse ".\agrotech-notices\agrotech-notices" "$env:USERPROFILE\.codex\skills\agrotech-notices"
```

### Linux / macOS

```sh
git clone https://github.com/AgroTech-SCAU/agrotech-notices.git
mkdir -p "$HOME/.codex/skills"
cp -R agrotech-notices/agrotech-notices "$HOME/.codex/skills/"
```

上述命令适用于首次安装至 Codex 的默认个人技能目录，已经安装时可在备份旧目录后更新同名 Skill

如设置了 `CODEX_HOME`，应将 Skill 放在其 `skills/agrotech-notices` 下，确保该文件夹内直接存在 `SKILL.md`

安装后可在新对话中输入

```text
用 $agrotech-notices 帮我写一份新成员须知通知
说明加入飞书、阅读成员须知与联系组长的安排
```

预期会得到一份可直接复制到微信的纯文本中文通知，不包含 Markdown 加粗、标题或列表标记；缺少具体时间、联系人等信息时保留必要占位符

## 包含的内容

| Skill | 用途 | 说明 |
| --- | --- | --- |
| [agrotech-notices](agrotech-notices/README.md) | 群通知、名单公示、项目安排、比赛招募与私聊回复 | [Skill 规则](agrotech-notices/SKILL.md) · [常用模板](agrotech-notices/references/templates.md) |

## 目录

```text
.
├── README.md
├── docs/
│   └── plan.md
├── .github/
│   ├── CONTRIBUTING.md
│   ├── ISSUE_TEMPLATE/
│   ├── pull_request_template.md
│   └── rulesets/
├── .githooks/
├── setup-scripts/
└── agrotech-notices/
    ├── README.md
    ├── SKILL.md
    ├── agents/openai.yaml
    └── references/templates.md
```

## 参与维护

建议使用 `Issue → Branch → Pull Request → 负责人合并` 的协作流程，不直接修改 `main`

- [当前规划](docs/plan.md)
- [贡献指南](.github/CONTRIBUTING.md)
- [分支保护规则说明](.github/rulesets/README.md)

仓库包含可选的本地 Git 防误操作提醒，首次克隆后可运行 `bash setup-scripts/setup-git.sh` 或 `.\setup-scripts\setup-git.ps1`

仓库管理员如需启用远端分支保护，应按 [规则说明](.github/rulesets/README.md) 在 GitHub 设置中手动导入，文件存在不代表规则已经生效

## 维护组织

[AgroTech Innovation Lab](https://github.com/AgroTech-SCAU)
