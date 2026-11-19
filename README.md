# gemini-codex

一个用于 T3 Code 的 Antigravity 技能。Gemini 负责理解项目、讨论方案和汇报结果，方案评审、实施和独立验收分别交给你选定的模型。

## 安装

先在 T3 Code 的 **Settings → Providers** 启用并登录 Antigravity 和要用于委派的 Provider（例如 Codex）。在运行 T3 Code 的环境中，将本仓库克隆到 Antigravity 的全局技能目录：

```powershell
git clone https://github.com/DefenceShin/gemini-codex.git "$env:USERPROFILE\.gemini\config\skills\gemini-codex"
```

macOS 或 Linux：

```bash
git clone https://github.com/DefenceShin/gemini-codex.git ~/.gemini/config/skills/gemini-codex
```

也可以把 [SKILL.md](SKILL.md) 放到上述 `gemini-codex` 目录。新开 Antigravity 会话后，在输入框输入 `$`，选中 `gemini-codex`。使用已有会话时，可从命令面板运行 **Restart agent session** 重新加载技能。 [T3 Code 技能目录](https://github.com/pingdotgg/t3code/blob/v0.1.10/docs/user/providers-antigravity.md#skills-and-attachments) · [技能调用说明](https://github.com/pingdotgg/t3code/blob/v0.1.10/docs/user/composer.md#commands-and-skills)

## 使用

1. **讨论方案。** 告诉 Gemini 你要解决的问题。它先查看项目并提出方案，再请你选定模型做可行性评审。
2. **执行。** 确认方案并授权实施后，Gemini 派你选定的模型修改并运行检查。
3. **独立验收。** 另起一个审核会话，由你选定的模型检查实际改动和验收证据。Gemini 汇报结论并附子会话链接。

你可以一次选好三个阶段的模型，也可以逐次选择。需要特定思考强度时，在选模型时一并指定。支持的档位由当前模型和 Provider 决定。

> 先调查导出流程并给我方案。方案评审用 Astra High，实施用 Sol Medium，独立验收用 Astra High。等我确认方案后再执行。

## 跨会话接续

跨会话或跨多次提交的任务按功能维护一份交接记录，写清已确认方案、实际改动、验收结果和接续点。优先使用项目已有的任务文档位置，否则放在 `docs/handoffs/<功能名>.md`。新会话重新调用技能并指定要继续的功能，Gemini 会先读取记录、核对当前版本和实际差异。单会话内的小改动在会话中交接。

在 Windows 上的 T3 Code 0.1.10 验证过跨 Provider 委派和技能加载。
