# UI 规范与配套 Skills 安装包

将同一套 UI 规范、选型流程和本地检索能力装到另一台电脑的 Codex。UI 路由与本地适配更新：2026-10-29；各第三方快照的来源与版本边界见 [第三方说明](../THIRD-PARTY-NOTICES.md)。

## 包含内容

| Skill | 职责 | 运行依赖 |
|---|---|---|
| [ui-design-standards](../skills/ui-design-standards/) | 共同入口、用户规范、专项导航；含视觉与动效补充参考 | 无脚本依赖 |
| [ui-ux-pro-max](../skills/ui-ux-pro-max/) | 按需检索配色、字体、风格、UX 和技术栈建议 | Python 3.10+；检索使用标准库 |
| [ui-feedback-patterns](../skills/ui-feedback-patterns/) | 提示、确认、浮层、引导与字段错误的选型和交互 | 无脚本依赖 |
| [ui-chat-desktop-interactions](../skills/ui-chat-desktop-interactions/) | 输入法、消息跟随、可调分栏与文件名展示 | 无脚本依赖 |
| [frontend-design](../skills/frontend-design/) | 需要新视觉方向时补充排版与构图判断 | 无脚本依赖 |

视觉与动效参考随 `ui-design-standards/references/visual-motion.md` 安装，不是第六个 Skill。Figma、Sites、Sleek 等为可选集成，需要在目标电脑另行安装与登录。

## 在另一台 Codex 中安装

复制下面整段给目标电脑上的 Codex。它会使用内置 `$skill-installer` 安装多个目录，无需把本机配置或账号凭据复制过去。

```text
使用 $skill-installer，从 GitHub 仓库 lawpowen/agent-skills 的 main 分支安装以下 5 个 skills：
codex/skills/ui-design-standards
codex/skills/ui-ux-pro-max
codex/skills/ui-feedback-patterns
codex/skills/ui-chat-desktop-interactions
codex/skills/frontend-design

保留每个目录的 agents、references、scripts、data 和许可证文件。
如果目标机器已有同名 skill，先比较差异并报告，不直接覆盖；按现有授权处理更新。
安装后读取 ui-design-standards，确认先遵循项目指令、已确认的设计与技术栈，再应用我们的规范，并按需使用 ui-ux-pro-max 和其他专项技能。
如 Python 可用，从实际安装目录运行 ui-ux-pro-max/scripts/search.py，以 query="keyboard focus modal"、--domain ux、--json 做一次检索检查；不要安装额外 Python 包或生成项目设计文件。
```

内置安装器的等价参数为：

```text
install-skill-from-github.py --repo lawpowen/agent-skills --ref main --path codex/skills/ui-design-standards codex/skills/ui-ux-pro-max codex/skills/ui-feedback-patterns codex/skills/ui-chat-desktop-interactions codex/skills/frontend-design
```

安装器脚本位于目标电脑的 `.system/skill-installer/scripts/`，让 Codex 从当前环境定位，不沿用另一台电脑的绝对路径。默认目标为 `$CODEX_HOME/skills`；未设置时为 `~/.codex/skills`，Windows 对应 `%USERPROFILE%\.codex\skills`。

安装完成后，技能会在下一轮对话可用；若列表仍未刷新，再重启 Codex。已有同名目录会使内置安装器中止，不会自动合并或更新，需先比较与备份。参考：[OpenAI 技能机制](https://developers.openai.com/plugins/concepts/skills)。

## 安装后的工作方式

UI 工作先遵循项目指定的入口和已有设计系统，再使用 `ui-design-standards` 补充这条原始偏好：**avoid unnecessary secondary labels and descriptions. Let the layout do the explaining**。保留任务必需的字段、单位、状态、错误和可访问名称。

需要通用设计建议时读取 `ui-ux-pro-max`；提示、确认和浮层读取 `ui-feedback-patterns`；聊天输入、滚动或桌面分栏读取 `ui-chat-desktop-interactions`；需要细化视觉动效时按导航读取补充参考。`frontend-design` 只在需要新的视觉方向时补充。用户当前要求与项目设计系统优先。

已有界面的审查、React Best Practices 和 shadcn/ui 按任务、实际技术栈及当前技能可用性选择；本包不包含这些可选技能，也不自动安装依赖或更换框架。设计和审查请求不自动授权实现或发布。

所有包内 skills 保留自动选用的默认策略，不要求每次手动写出技能名。选用依赖任务与描述匹配，不是无条件加载全部内容；若需要明确指定入口，可写 `$ui-design-standards`。

## 检查与边界

安装后确认 5 个目录各有 `SKILL.md`，导航和参考路径可读，并验证一次 UX 检索。也可让目标 Codex 说明“给删除按钮加确认时会读取哪些技能”，检查它是否先遵循项目入口，再按需应用我们的规范和反馈专项。

视频规则的核实日期、官方来源及适用范围随参考文件一并保留。500ms、82%、暗色字重减 40 等数值属于待调参数，不是默认规则；技能文档校验不代表已验证具体产品界面。

此包不包含本机 `config.toml`、`auth.json`、API key、浏览器登录状态或项目数据。第三方许可证与快照说明见 [THIRD-PARTY-NOTICES.md](../THIRD-PARTY-NOTICES.md)。

### 发布时验证

2026-10-24 的发布验证包括 5 个 Skill 的结构校验、引用路径和数据契约检查，以及技能目录外的 UX、WPF 和设计系统检索；原独立运行测试记录在当时的发布工作区。每次更新应重新验证涉及的技能和检索；技能文档校验不证明具体产品界面的视觉与交互。
