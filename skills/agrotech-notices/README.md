# AgroTech Innovation Lab 通知写作 Skill

用于 AgroTech Innovation Lab 的中文通知起草、润色和私聊回复，提供可直接改写的文案骨架，并保留已确认的组织沟通口径。

技能名：agrotech-notices

## 包含的模板

| 编号 | 场景 |
| --- | --- |
| 01 | 未参与成员反馈通知 |
| 02 | 成员名单更新说明 |
| 03 | 二次复查结果公示 |
| 04 | 个人情况说明与后续安排 |
| 05 | 协会组织项目的统一调整通知 |
| 06 | 个人项目参与资格调整通知 |
| 07 | 比赛统一招募与队长选拔 |
| 08 | 接受任务后恢复身份的私聊回复 |
| 09 | 会服或物资自愿订购 |
| 10 | 活动报名与人员招募 |
| 11 | 会议或组会安排 |
| 12 | 新成员欢迎与入群引导 |
| 13 | 培训或工作坊安排 |
| 14 | 任务分工与开放认领 |
| 15 | 项目进度反馈与节点提醒 |
| 16 | 材料征集、提交与补交 |
| 17 | 物资借用与归还 |
| 18 | 工作或项目交接 |
| 19 | 时间、地点变更及延期、取消 |
| 20 | 成果展示与贡献致谢 |

现有 20 类模板分为 [成员与项目通知（01—08）](references/templates.md) 和 [日常组织通知（09—20）](references/daily-notices.md)。不使用技能时也可直接改写模板，替换【】中的信息并删去不适用段落。

## 在 Codex 中使用

本 Skill 位于协会 Skills 集合的 `skills/agrotech-notices/` 目录中，安装时仅复制这个 Skill 子目录，并确保目标文件夹中直接包含 `SKILL.md`

默认个人技能目录为 ~/.codex/skills；如果设置了 CODEX_HOME，则使用其下的 skills 目录。

Windows PowerShell 安装示例：

~~~powershell
git clone https://github.com/AgroTech-SCAU/ATIL-Skills.git ATIL-Skills
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
Copy-Item -Recurse ".\ATIL-Skills\skills\agrotech-notices" "$env:USERPROFILE\.codex\skills\agrotech-notices"
~~~

macOS / Linux 安装示例：

~~~sh
git clone https://github.com/AgroTech-SCAU/ATIL-Skills.git ATIL-Skills
mkdir -p "$HOME/.codex/skills"
cp -R ATIL-Skills/skills/agrotech-notices "$HOME/.codex/skills/"
~~~

以上命令用于首次安装，已经安装时请先备份原有同名目录再更新

安装后，在下一轮消息中调用：

~~~text
用 $agrotech-notices，帮我写一份可发微信群的成员二次复查结果公示。
名单另附，联系人写我，语气正式但委婉。
~~~

也可以提供原稿后要求润色：

~~~text
用 $agrotech-notices 润色下面的比赛招募通知。
保留我给出的队伍、人数、队长候选范围和优先级依据，不增加新的报名条件。
【在这里粘贴原稿】
~~~

会服订购等日常通知也可以直接调用：

~~~text
用 $agrotech-notices 写会服订购通知：所有成员自愿购买对应组别的款式，每件 55 元。
有意订购者在随附表格登记，标题、价格、时间和正文都不要加粗。
~~~

## 提供哪些信息

按实际情况提供通知对象、已确认的事实、本次安排、时间、联系人与希望的语气即可。已有原稿时直接粘贴；没有的细节可留作占位符。

涉及成员调整时，区分“拟调整”“已共同确认”与“已执行”。涉及协会组织的比赛、软著等项目参与资格时，沿用对应项目负责人与协会全体管理层共同讨论决定的口径。

## 文案约定

- 所有通知与回复均不加粗，标题、金额、姓名和时间也不例外；导出为其他格式时保持同样要求。
- 默认用于微信，输出纯文本，不使用 Markdown 标题、列表、代码块、格式化链接或 HTML、富文本样式。
- 重点内容通过换行、自然语言和中文序号区分，复制到微信后不应出现格式标记。
- 正式、直接、尊重；群通知突出具体安排，私聊回复保持自然简短。
- 正常退任、暂缓参与、误判后恢复和重新入会分别表述。
- 成员身份调整不否定既有实际贡献，成果署名与贡献认定以实际贡献为依据。
- 不将“尚未看到进展”扩大成“完全没有工作”，不虚构核查、投票或已完成的操作。
- 新任务的明确要求优先于历史范文。历史比赛的队伍、人数、选拔方式和日期不自动用于下一轮。
- 模板用于起草文稿；发布消息、调整成员与权限等实际操作按当次授权执行。

完整说明见 [SKILL.md](SKILL.md)。

## Skill 目录结构

~~~text
skills/agrotech-notices/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── templates.md
    └── daily-notices.md
~~~
