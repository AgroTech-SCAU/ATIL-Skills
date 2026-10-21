# ATIL-Skills

AgroTech Innovation Lab 统一维护的 AI Agent Skills 集合

本仓库按独立 Skill 目录组织可复用的工作流程与专业知识，供协会成员在日常管理、项目推进、科研和工程任务中按需安装与使用

目前收录 `agrotech-notices`，后续新增 Skills 时继续放入 `skills/`，不改变已有 Skill 的名称和调用入口

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

每个 Skill 都使用自己的 `SKILL.md`、参考材料与必要配置，新增 Skill 不应把文件直接散放在仓库根目录

## 2. 安装与使用

本仓库当前提供文档型 Skills，不需要编译或专用硬件

以下以 Codex 和 `agrotech-notices` 为例，其他 Skill 可将路径中的名称替换为对应目录名

### Windows PowerShell

```powershell
git clone https://github.com/AgroTech-SCAU/ATIL-Skills.git ATIL-Skills
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
Copy-Item -Recurse ".\ATIL-Skills\skills\agrotech-notices" "$env:USERPROFILE\.codex\skills\agrotech-notices"
```

### Linux / macOS

```sh
git clone https://github.com/AgroTech-SCAU/ATIL-Skills.git ATIL-Skills
mkdir -p "$HOME/.codex/skills"
cp -R ATIL-Skills/skills/agrotech-notices "$HOME/.codex/skills/"
```

上述命令用于首次安装，更新已有 Skill 前请先备份原目录

如设置了 `CODEX_HOME`，请使用其下的 `skills` 目录，安装完成后应能直接找到 `skills/agrotech-notices/SKILL.md`

安装后可在新对话中调用

```text
用 $agrotech-notices 帮我写一份新成员通知
说明加入飞书、阅读成员须知与向组长提交邮箱的安排
```

`agrotech-notices` 所有通知和回复均不加粗，包括标题、金额、日期和正文。默认生成可直接发送到微信的纯文本，不使用 Markdown 标题或其他富文本标记

## 3. 仓库结构

```text
ATIL-Skills/
├── README.md
├── docs/
│   └── plan.md
├── skills/
│   └── agrotech-notices/
│       ├── SKILL.md
│       ├── README.md
│       ├── agents/openai.yaml
│       └── references/
│           ├── templates.md
│           └── daily-notices.md
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
