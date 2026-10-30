# ATIL-Skills

AgroTech Innovation Lab 统一维护的 AI Agent Skills 集合

本仓库按独立 Skill 目录组织可复用的工作流程与专业知识，供协会成员在日常管理、项目推进、科研和工程任务中按需安装与使用

目前收录 `agrotech-notices`（通知与回复）和 `report-briefing`（工作汇报与现场安排）；后续新增 Skills 时继续放入 `skills/`，不改变已有 Skill 的名称和调用入口

> [!IMPORTANT]
> ## 参与本仓库开发
>
> **Issue → Branch → Commit → Push → Pull Request → 项目负责人 Merge**
>
> - 开始开发前，原则上先创建或认领 Issue
> - 优先从 Issue 右侧 `Development` 创建任务分支，也可从最新 `main` 手动创建分支并关联 Issue
> - 推荐分支名为 `feat/xxx`、`fix/xxx`、`refactor/xxx`、`docs/xxx`，一个分支只处理一个主题
> - 修改后按主题小步 Commit，再 Push 自己的任务分支
> - 通过 Pull Request 说明修改内容、关联 Issue 和验证方式
> - 项目负责人检查 PR 后合并到 `main`，普通成员不要直接合并
> - **请勿直接在 `main` 开发或 Push，更不要 Force Push**
> - 如果误在 `main` 上产生了有用 Commit，先创建新分支保存提交，不要先执行 `reset --hard`
>
> 详细协作流程、角色权限和误操作处理见 [CONTRIBUTING.md](.github/CONTRIBUTING.md)

## 1. Skills 目录

| Skill | 功能 | 入口 |
| --- | --- | --- |
| [agrotech-notices](skills/agrotech-notices/README.md) | 20 类纯文本通知与回复，覆盖成员管理、日常协作、物资订购和活动招募；所有成稿均不加粗 | [SKILL.md](skills/agrotech-notices/SKILL.md) · [成员与项目模板](skills/agrotech-notices/references/templates.md) · [日常组织模板](skills/agrotech-notices/references/daily-notices.md) |
| [report-briefing](skills/report-briefing/README.md) | 将零散信息整理为工作计划、进展或结果汇报；现场安排中保持目标、分工、执行和成果逐项对应，缺项保留占位 | [SKILL.md](skills/report-briefing/SKILL.md) · [现场安排模板](skills/report-briefing/references/field-plan-template.md) · [会议依据](skills/report-briefing/references/meeting-basis.md) |

每个 Skill 都使用自己的 `SKILL.md`、参考材料与必要配置，新增 Skill 不应把文件直接散放在仓库根目录

需要面向成员发布通知或私聊回复时使用 `agrotech-notices`；需要向负责人说明目标、人员、任务、进展和结果时使用 `report-briefing`

## 2. 安装与使用

本仓库当前提供文档型 Skills，不需要编译或专用硬件

以下以 Codex 和 `report-briefing` 为例；将技能名称改为 `agrotech-notices` 即可安装通知写作 Skill

### Windows PowerShell

```powershell
git clone https://github.com/AgroTech-SCAU/ATIL-Skills.git ATIL-Skills
$skillName = "report-briefing"
$codexRoot = if ($env:CODEX_HOME) { $env:CODEX_HOME } else { Join-Path $env:USERPROFILE ".codex" }
$skillsRoot = Join-Path $codexRoot "skills"
New-Item -ItemType Directory -Force $skillsRoot | Out-Null
Copy-Item -Recurse ".\ATIL-Skills\skills\$skillName" (Join-Path $skillsRoot $skillName)
```

### Linux / macOS

```sh
git clone https://github.com/AgroTech-SCAU/ATIL-Skills.git ATIL-Skills
skill_name=report-briefing
codex_root=${CODEX_HOME:-"$HOME/.codex"}
mkdir -p "$codex_root/skills"
cp -R "ATIL-Skills/skills/$skill_name" "$codex_root/skills/"
```

仓库只需 clone 一次；需要两项 Skill 时，更换技能名称后再次执行复制命令即可

上述命令用于首次安装；更新已有 Skill 时，先备份并移出旧的同名目录，再复制新目录，避免形成多层嵌套或残留旧文件

如设置了 `CODEX_HOME`，示例会使用其下的 `skills` 目录；安装完成后，目标应为 `<技能目录>/<skill-name>/SKILL.md`，并保留该 Skill 的 `references/` 等附属文件

安装后可在新对话中调用

工作汇报与现场安排：

```text
用 $report-briefing 帮我把下面的信息整理成可复制到微信的现场安排
目标、分工、执行和成果按同一任务顺序对应，缺项留具体占位，不补造事实
【粘贴本次时间、地点、人员、设备和任务信息】
```

通知与回复：

```text
用 $agrotech-notices 帮我写一份新成员通知
说明加入飞书、阅读成员须知与向组长提交邮箱的安排
```

`agrotech-notices` 所有通知和回复均不加粗，包括标题、金额、日期和正文。默认生成可直接发送到微信的纯文本，不使用 Markdown 标题或其他富文本标记

`report-briefing` 默认生成纯文本分点汇报；事前计划、进展和结果采用各自的重点，未确认信息保留具体占位，不将计划写成已完成事项；用户另有格式要求时按要求输出

## 3. 仓库结构

```text
ATIL-Skills/
├── README.md
├── docs/
│   └── plan.md
├── skills/
│   ├── agrotech-notices/
│   │   ├── SKILL.md
│   │   ├── README.md
│   │   ├── agents/openai.yaml
│   │   └── references/
│   │       ├── templates.md
│   │       └── daily-notices.md
│   └── report-briefing/
│       ├── SKILL.md
│       ├── README.md
│       └── references/
│           ├── field-plan-template.md
│           └── meeting-basis.md
├── .github/
│   ├── CONTRIBUTING.md
│   ├── ISSUE_TEMPLATE/
│   ├── pull_request_template.md
│   └── rulesets/
├── .githooks/
└── setup-scripts/
```

## 4. 仓库维护与安全设置

- [项目规划](docs/plan.md) 记录已完成内容、当前工作和后续方向
- [贡献指南](.github/CONTRIBUTING.md) 说明 Issue、分支、提交和 PR 的完整操作
- [Issue Forms](.github/ISSUE_TEMPLATE/) 提供问题、功能和一般任务入口
- [Pull Request 模板](.github/pull_request_template.md) 用于提交前检查改动
- [分支保护说明](.github/rulesets/README.md) 解释 `main` 的远端保护规则

本地可选开启防误操作提醒

```sh
bash setup-scripts/setup-git.sh
```

Windows PowerShell 使用 `.\setup-scripts\setup-git.ps1` 对应脚本

公开仓库管理员还需要在 GitHub 的 `Settings → Rules → Rulesets` 中，手动导入 `.github/rulesets/main-protection.json` 并启用规则

规则文件位于仓库内并不代表远端规则已经生效，本地 Git Hook 也不能代替 GitHub Ruleset

正式稳定成果按照仓库规范使用 Git Tag 与 GitHub Release 发布

## 5. 维护者

[AgroTech Innovation Lab](https://github.com/AgroTech-SCAU)
