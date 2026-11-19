# gemini-codex

[简体中文](README.md) | **English**

An Antigravity skill for T3 Code. Gemini reads the project, discusses the plan with you, and reports the results in Chinese. You choose which models review the plan, implement it, and independently verify the changes.

## Installation

In T3 Code, open **Settings → Providers** and enable and sign in to Antigravity and the provider you want to delegate to, such as Codex. Clone this repository into Antigravity's global skills directory on the machine running T3 Code.

On Windows, run the following in PowerShell.

```powershell
git clone https://github.com/DefenceShin/gemini-codex.git "$env:USERPROFILE\.gemini\config\skills\gemini-codex"
```

On macOS or Linux, run the following in your shell.

```bash
git clone https://github.com/DefenceShin/gemini-codex.git ~/.gemini/config/skills/gemini-codex
```

You can also place [SKILL.md](SKILL.md) in the `gemini-codex` directory shown above. In a new Antigravity thread, type `$` in the message box and select `gemini-codex`. To reload the skill in an existing thread, choose **Restart agent session** from the command palette. [T3 Code skill directories](https://github.com/pingdotgg/t3code/blob/v0.1.10/docs/user/providers-antigravity.md#skills-and-attachments) · [Using skills in the composer](https://github.com/pingdotgg/t3code/blob/v0.1.10/docs/user/composer.md#commands-and-skills)

## Usage

1. **Discuss the plan.** Tell Gemini what you want to accomplish. It reads the project and proposes a plan, then asks you to choose a model to review the plan's feasibility.
2. **Implement the plan.** Once you approve the plan and authorize implementation, Gemini delegates the changes and checks to the model you chose.
3. **Verify the changes independently.** Gemini starts a separate review thread so the model you chose can inspect the actual changes and check the evidence against your acceptance criteria. Gemini reports the outcome with links to the delegated threads.

You can choose all three models up front or choose one at each stage. If you want a particular reasoning effort, specify it alongside the model. Available levels depend on the model and its provider.

> Investigate the export flow and propose a plan. Use Astra High to review the plan, Sol Medium to implement it, and Astra High for independent verification. Wait for my approval before implementing.

## Resuming across threads

For work that spans multiple threads or commits, keep one handoff record per feature with the approved plan, actual changes, verification results, and where to pick up. Use the project's existing location for task notes, or use `docs/handoffs/<feature-name>.md`. In a new thread, invoke the skill again and name the feature you want to resume. Gemini reads its handoff record and checks the current revision and diff before continuing. For small changes completed in a single thread, keep the handoff in the conversation.

Cross-provider delegation and skill loading were verified on Windows with T3 Code 0.1.10.
