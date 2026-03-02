# 46 个 Claude Code 技巧：从入门到精通

这是我总结的 Claude Code 使用技巧：自定义状态栏脚本、精简系统提示词、用 Gemini CLI 当助手、让 Claude Code 在容器中运行自己，还有 [dx 插件](#技巧-44安装-dx-插件)。

📺 [快速演示](https://www.youtube.com/watch?v=hiISl558JGE) - 观看多 Claude 协作工作流和语音输入的实际效果：

[![演示视频缩略图](assets/demo-thumbnail.png)](https://www.youtube.com/watch?v=hiISl558JGE)

<!-- TOC -->
## 目录

- [技巧 0：自定义状态栏](#技巧-0自定义状态栏)
- [技巧 1：掌握几个常用的斜杠命令](#技巧-1掌握几个常用的斜杠命令)
- [技巧 2：用语音与 Claude Code 交流](#技巧-2用语音与-claude-code-交流)
- [技巧 3：把大问题拆成小问题](#技巧-3把大问题拆成小问题)
- [技巧 4：像高手一样使用 Git 和 GitHub CLI](#技巧-4像高手一样使用-git-和-github-cli)
- [技巧 5：AI 上下文就像牛奶，新鲜浓缩才最好！](#技巧-5ai-上下文就像牛奶新鲜浓缩才最好)
- [技巧 6：从终端获取输出](#技巧-6从终端获取输出)
- [技巧 7：设置终端别名快速启动](#技巧-7设置终端别名快速启动)
- [技巧 8：主动压缩上下文](#技巧-8主动压缩上下文)
- [技巧 9：完成自主任务的「编写-测试」循环](#技巧-9完成自主任务的编写-测试循环)
- [技巧 10：Cmd+A 和 Ctrl+A 是你的好朋友](#技巧-10cmda-和-ctrla-是你的好朋友)
- [技巧 11：用 Gemini CLI 访问受限网站](#技巧-11用-gemini-cli-访问受限网站)
- [技巧 12：打造自己的工作流](#技巧-12打造自己的工作流)
- [技巧 13：搜索对话历史](#技巧-13搜索对话历史)
- [技巧 14：用终端标签页多任务处理](#技巧-14用终端标签页多任务处理)
- [技巧 15：精简系统提示词](#技巧-15精简系统提示词)
- [技巧 16：用 Git Worktree 并行处理分支](#技巧-16用-git-worktree-并行处理分支)
- [技巧 17：长时间任务的手动指数退避](#技巧-17长时间任务的手动指数退避)
- [技巧 18：把 Claude Code 当写作助手](#技巧-18把-claude-code-当写作助手)
- [技巧 19：Markdown 太棒了](#技巧-19markdown-太棒了)
- [技巧 20：用 Notion 保留粘贴时的链接](#技巧-20用-notion-保留粘贴时的链接)
- [技巧 21：用容器处理长时间高风险任务](#技巧-21用容器处理长时间高风险任务)
- [技巧 22：提升 Claude Code 技能的最好方法就是多用](#技巧-22提升-claude-code-技能的最好方法就是多用)
- [技巧 23：克隆/复刻和半克隆对话](#技巧-23克隆复刻和半克隆对话)
- [技巧 24：用 realpath 获取绝对路径](#技巧-24用-realpath-获取绝对路径)
- [技巧 25：理解 CLAUDE.md、技能、斜杠命令和插件的区别](#技巧-25理解-claudemd技能斜杠命令和插件的区别)
- [技巧 26：交互式 PR 审查](#技巧-26交互式-pr-审查)
- [技巧 27：把 Claude Code 当研究工具](#技巧-27把-claude-code-当研究工具)
- [技巧 28：掌握多种验证输出的方法](#技巧-28掌握多种验证输出的方法)
- [技巧 29：把 Claude Code 当 DevOps 工程师](#技巧-29把-claude-code-当-devops-工程师)
- [技巧 30：保持 CLAUDE.md 简洁并定期检查](#技巧-30保持-claudemd-简洁并定期检查)
- [技巧 31：Claude Code 是通用接口](#技巧-31claude-code-是通用接口)
- [技巧 32：选择正确的抽象层级](#技巧-32选择正确的抽象层级)
- [技巧 33：审查你批准的命令](#技巧-33审查你批准的命令)
- [技巧 34：多写测试（使用 TDD）](#技巧-34多写测试使用-tdd)
- [技巧 35：在未知领域更勇敢些，迭代解决问题](#技巧-35在未知领域更勇敢些迭代解决问题)
- [技巧 36：在后台运行 bash 命令和子代理](#技巧-36在后台运行-bash-命令和子代理)
- [技巧 37：个性化软件时代已来](#技巧-37个性化软件时代已来)
- [技巧 38：导航和编辑输入框](#技巧-38导航和编辑输入框)
- [技巧 39：花点时间规划，但也要快速原型验证](#技巧-39花点时间规划但也要快速原型验证)
- [技巧 40：简化过度复杂的代码](#技巧-40简化过度复杂的代码)
- [技巧 41：自动化的自动化](#技巧-41自动化的自动化)
- [技巧 42：分享知识，贡献力量](#技巧-42分享知识贡献力量)
- [技巧 43：持续学习！](#技巧-43持续学习)
- [技巧 44：安装 dx 插件](#技巧-44安装-dx-插件)
- [技巧 45：快速设置脚本](#技巧-45快速设置脚本)
- [技巧 46：组建团队](#技巧-46组建团队)

<!-- /TOC -->

## 技巧 0：自定义状态栏

你可以自定义 Claude Code 底部的状态栏，显示有用的信息。我把状态栏设置为显示模型名称、当前目录、git 分支（如果有）、未提交文件数、与远程仓库的同步状态，以及 token 使用量的可视化进度条。它还会显示第二行，展示我最后发送的消息，这样我就能知道对话的主题：

```
Opus 4.5 | 📁claude-code-tips | 🔀main (scripts/context-bar.sh uncommitted, synced 12m ago) | ██░░░░░░░░ 18% of 200k tokens
💬 This is good. I don't think we need to change the documentation as long as we don't say that the default color is orange el...
```

这个功能对监控上下文使用量、回忆正在处理的内容很有帮助。脚本支持 10 种颜色主题：橙色、蓝色、青色、绿色、薰衣草色、玫瑰色、金色、石板灰、青绿色或灰色。

![颜色预览选项](scripts/color-preview.png)

设置方法：使用[这个示例脚本](scripts/context-bar.sh)，查看[设置说明](scripts/README.md)。

## 技巧 1：掌握几个常用的斜杠命令

有很多内置的斜杠命令（输入 `/` 查看全部）。以下是一些值得掌握的：

### /usage

检查你的速率限制：

```
 Current session
 █████████▌                                         19% used
 Resets 12:59am (America/Vancouver)

 Current week (all models)
 █████████████████████▌                             43% used
 Resets Feb 3 at 1:59pm (America/Vancouver)

 Current week (Sonnet only)
 ███████████████████▌                               39% used
 Resets 8:59am (America/Vancouver)
```

如果你想密切关注使用量，可以在一个标签页中保持打开，用 Tab 然后 Shift+Tab 或 ← 然后 → 来刷新。

### /chrome

切换 Claude 的原生浏览器集成：

```
> /chrome
Chrome integration enabled
```

### /mcp

管理 MCP（模型上下文协议）服务器：

```
 Manage MCP servers
 1 server

 ❯ 1. playwright  ✔ connected · Enter to view details

 MCP Config locations (by scope):
  • User config (available in all your projects):
    • /Users/yk/.claude.json
```

### /stats

查看使用统计，带有 GitHub 风格的活动图：

```
      Feb Mar Apr May Jun Jul Aug Sep Oct Nov Dec Jan
      ··········································▒█░▓░█░▓▒▒
  Mon ·········································▒▒██▓░█▓█░█
      ·········································░▒█▒▓░█▒█▒█
  Wed ········································░▓▒█▓▓░▒▓▒██
      ········································░▓░█▓▓▓▓█░▒█
  Fri ········································▒░░▓▒▒█▓▓▓█
      ········································▒▒░▓░░▓▒▒░░

      Less ░ ▒ ▓ █ More

  Favorite model: Opus 4.5        Total tokens: 17.6m

  Sessions: 4.1k                  Longest session: 20h 40m 45s
  Active days: 79/80              Longest streak: 75 days
  Most active day: Jan 26         Current streak: 74 days

  You've used ~24x more tokens than War and Peace
```

### /clear

清除对话，重新开始。

## 技巧 2：用语音与 Claude Code 交流

我发现用语音沟通比打字快得多。在本地机器上使用语音转录系统对此非常有帮助。

在 Mac 上，我尝试过几个不同的选项：
- [superwhisper](https://superwhisper.com/)
- [MacWhisper](https://goodsnooze.gumroad.com/l/macwhisper)
- [Super Voice Assistant](https://github.com/ykdojo/super-voice-assistant)（开源，支持 Parakeet v2/v3）

使用托管服务准确率更高，但本地模型已经够用了。即使转录有错字，Claude 也能理解你想表达的意思。有时要把某些话说得更清楚，但总体没问题。

例如，在这个截图中你可以看到 Claude 能够正确理解转录错误的词，如 "ExcelElanishMark" 和 "advast"，正确理解为 "exclamation mark" 和 "Advanced"：

![语音转录错误被正确理解](assets/voice-transcription-mistakes.png)

我认为最好的理解方式是把它想象成和朋友交流。当然，你可以通过短信沟通。对某些人来说这可能更简单，或者发邮件，对吧？这完全没问题。这似乎是大多数人与 Claude Code 交流的方式。但如果你想更快地沟通，为什么不直接打个电话呢？你可以直接发语音消息。你不需要真的和 Claude Code 通电话，只需发送一堆语音消息。对我来说这更快，因为我过去几年练习了很多说话的技巧。但我认为对大多数人来说，这也会更快。

一个常见的反对意见是「如果我和其他人在一个房间里怎么办？」我就戴着耳机小声说——我个人喜欢 Apple EarPods（不是 AirPods）。便宜、质量够用，轻声对着说就行。我在其他人面前这样做过，效果很好。办公室里本来就在交谈，你不是在和同事说话，而是在轻声和语音转录系统说话。这没什么问题，甚至在飞机上也能用。周围够吵，别人听不到你，但离麦克风够近的话，本地模型还是能听懂。（我正在航班上用这个方法写这一段。）

## 技巧 3：把大问题拆成小问题

这是最重要的概念之一，和传统软件工程完全一样——优秀的软件工程师已经知道怎么做，这也适用于 Claude Code。

如果 Claude Code 无法一次性解决一个困难的问题，请它分解成多个小问题。看它能否解决其中一部分。还是太难？那就更小的子问题。持续下去，直到所有问题都可以解决。

本质上，不是从 A 直接到 B：

![直接方法](assets/breakdown-direct.png)

而是从 A 到 A1 到 A2 到 A3，再到 B：

![逐步方法](assets/breakdown-steps.png)

一个很好的例子是我构建自己的语音转录系统时。我需要构建一个系统，让用户可以选择和下载模型、接受键盘快捷键、开始转录、将转录文本放到用户光标位置，并把所有这些包装在一个漂亮的 UI 中。这很复杂。所以我把它分解成更小的任务。首先，我创建了一个只会下载模型的可执行文件，不做其他事情。然后我创建了另一个只会录制语音的可执行文件。然后是另一个只会转录预录制音频的。我这样一个接一个地完成，最后再把它们组合起来。

与此相关：你的问题解决能力和软件工程能力在代理编程中仍然很重要。Claude Code 可以自己解决很多问题，但加上你的通用问题解决和软件工程能力，它会变得更强大。

## 技巧 4：像高手一样使用 Git 和 GitHub CLI

直接让 Claude 处理你的 Git 和 GitHub CLI 任务。包括提交（不用手动写提交信息）、分支、拉取和推送。

我个人允许自动拉取但不允许自动推送，因为推送风险更大——拉取出问题不会污染远程仓库。

使用 Claude Code 后，我开始更多地创建草稿 PR。这让 Claude Code 可以低风险地处理 PR 创建过程——标记为准备好审查之前，你可以审查所有内容。

事实证明，`gh` 相当强大。你甚至可以通过它发送任意 GraphQL 查询。例如，你甚至可以找到 GitHub PR 描述被编辑的确切时间：

```
⏺ Bash(gh api graphql -f query='
      query {
        repository(owner: "...", name: "...") {
          pullRequest(number: ...) {
            userContentEdits(first: 100) {
              nodes { editedAt editor { login } }
            }
          }
        }
      }')

⏺ Here's the full edit history for your PR description:

  | #  | Edited At (UTC)     | Editor |
  |----|---------------------|--------|
  | 1  | 2025-12-01 00:08:34 | ykdojo |
  | 2  | 2025-12-01 15:57:21 | ykdojo |
  | 3  | 2025-12-01 16:24:33 | ykdojo |
  | 4  | 2025-12-01 16:27:00 | ykdojo |
  | 5  | 2025-12-04 00:40:02 | ykdojo |
  ...
```

### 禁用提交/PR 署名

默认情况下，Claude Code 会在提交中添加 `Co-Authored-By` 尾部，在 PR 中添加署名页脚。你可以在 `~/.claude/settings.json` 中添加以下内容来禁用两者：

```json
{
  "attribution": {
    "commit": "",
    "pr": ""
  }
}
```

将两者设置为空字符串可完全移除署名。这取代了旧的 `includeCoAuthoredBy` 设置，该设置现已弃用。

## 技巧 5：AI 上下文就像牛奶，新鲜浓缩才最好！

当你和 Claude Code 开始新对话时，它表现最好，因为不需要处理先前的上下文。但随着对话越来越长，性能往往会下降。

所以最好为每个新主题开始新对话，或者性能下降就重新开始。

## 技巧 6：从终端获取输出

有时你想复制粘贴 Claude Code 的输出，但直接从终端复制不太方便。以下是几个更容易获取内容的方法：

- **`/copy` 命令**：最简单的选项——只需输入 `/copy` 将 Claude 的最后一条响应作为 markdown 复制到剪贴板
- **直接使用剪贴板**：在 Mac 或 Linux 上，让 Claude 使用 `pbcopy` 将输出直接发送到剪贴板
- **写入文件**：让 Claude 把内容放在文件中，然后让它在 VS Code（或你喜欢的编辑器）中打开，这样你可以从那里复制。你也可以指定行号，这样可以让 Claude 打开它刚编辑的特定行。对于 markdown 文件，一旦在 VS Code 中打开，你可以使用 Cmd+Shift+P（或 Linux/Windows 上的 Ctrl+Shift+P）选择「Markdown: Open Preview」查看渲染版本
- **打开 URL**：如果有你想自己查看的 URL，让 Claude 在浏览器中打开它。在 Mac 上，你可以让它使用 `open` 命令，但一般来说，让它在你喜欢的浏览器中打开应该在任何平台上都能工作
- **GitHub Desktop**：你可以让 Claude 在 GitHub Desktop 中打开当前仓库。当它在非根目录工作时特别有用——例如，如果你让它在不同目录创建 git worktree，而你还没有从那里打开 Claude Code

你也可以组合使用这些方法。例如，如果你想编辑 GitHub PR 描述，与其让 Claude 直接编辑（它可能会搞砸），不如让它先把内容复制到本地文件。让它编辑那个，自己检查结果，一旦看起来不错，让它复制粘贴回 GitHub PR。这非常有效。或者如果你想自己做，可以只是让它在 VS Code 中打开或通过 pbcopy 给你，这样你可以手动复制粘贴。

当然你可以自己运行这些命令，但如果你发现自己重复这样做，让 Claude 来跑会有帮助。

## 技巧 7：设置终端别名快速启动

因为使用 Claude Code 我更多地使用终端，我发现设置短别名很有帮助，这样可以快速启动。以下是我使用的：

- `c` 代表 Claude Code（这是我用得最多的）
- `ch` 代表带 Chrome 集成的 Claude Code
- `gb` 代表 GitHub Desktop
- `co` 代表 VS Code
- `q` 代表进入我大多数项目的项目目录。从那里我可以手动 cd 进入单独的文件夹来处理该项目，或者我可以用 `c` 启动 Claude Code，让它基本上访问任何需要访问的项目。

设置方法：在你的 shell 配置文件（`~/.zshrc` 或 `~/.bashrc`）中添加这样的行：

```bash
alias c='claude'
alias ch='claude --chrome'
alias gb='github'
alias co='code'
alias q='cd ~/Desktop/projects'
```

一旦有了这些别名，你可以将它们与标志组合使用：`c -c` 继续上一次对话，`c -r` 显示最近对话列表以恢复。这些也适用于 `ch`（`ch -c`、`ch -r`）用于 Chrome 会话。

## 技巧 8：主动压缩上下文

Claude Code 中有一个 `/compact` 命令，可以总结你的对话以释放上下文空间。当完整的可用上下文被填满时，也会发生自动压缩。Opus 4.5 的总可用上下文窗口目前是 200k，其中 45k 保留给自动压缩。总 200k 的大约 10% 自动被系统提示词、工具、内存和动态上下文填满。我用 `/config` 关闭了自动压缩，这样我有更多上下文可用于主对话，对何时压缩也有更多控制。

我的做法是在重新开始之前让 Claude 写一份交接文档。像这样：

> 把剩余的计划放在 system-prompt-extraction 文件夹中，命名为 HANDOFF.md。解释你尝试了什么，什么有效，什么无效，这样下一个有新鲜上下文的代理就能只加载那个文件，不需要其他东西就能开始这个任务并完成它。

Claude 会创建一个总结当前工作状态的文件：

```
⏺ Write(experiments/system-prompt-extraction/HANDOFF.md)
  ⎿  Wrote 129 lines to experiments/system-prompt-extraction/HANDOFF.md
     # System Prompt Slimming - Handoff Document
     ## Goal
     Reduce Claude Code's system prompt by ~45% (currently at 11%, need ~34% more).
     ## Current Progress
     ### What's Been Done
     - **Backup/restore system**: `backup-cli.sh` and `restore-cli.sh` with SHA256 verification
     - **Patch system**: `patch-cli.js` that restores from backup then applies patches
     ...
```

Claude 写完后，快速审查一下。如果缺东西，要求编辑：

> 你有没有添加关于迭代测试而不是一次性做所有事情的说明？

然后开始新对话。新代理只需要文件的路径就能开始工作：

```
> experiments/system-prompt-extraction/HANDOFF.md
```

在后续对话中，你可以让代理为下一个代理更新文档。

我还创建了一个 `/handoff` 斜杠命令来自动化这个过程——它检查现有的 HANDOFF.md，如果存在就读取它，然后创建或更新它，包含目标、进度、什么有效、什么无效以及下一步。你可以在 [skills 文件夹](skills/handoff/SKILL.md)中找到它，或通过 [dx 插件](#技巧-44安装-dx-插件)安装。

**替代方案：使用计划模式**

另一个选择是使用计划模式。用 `/plan` 或 Shift+Tab 进入。让 Claude 收集所有相关的上下文并为下一个代理创建一个全面的计划：

> 我刚启用了计划模式。把你需要的所有上下文带给下一个代理。下一个代理不会有任何其他上下文，所以你需要相当全面。

Claude 会探索代码库、收集上下文并编写详细的计划。完成后，你会看到这样的选项：

```
Would you like to proceed?

❯ 1. Yes, clear context and auto-accept edits (shift+tab)
  2. Yes, auto-accept edits
  3. Yes, manually approve edits
  4. Type here to tell Claude what to change
```

选项 1 清除先前的上下文并以计划重新开始。新的 Claude 实例只看到计划，因此它可以专注于工作，不受旧对话的负担。它还会获得旧转录文件的链接，以防需要查找特定细节。

## 技巧 9：完成自主任务的「编写-测试」循环

如果你想让 Claude Code 自主运行某些东西，比如 `git bisect`，你需要给它一种验证结果的方法。关键是完成编写-测试循环：编写代码、运行、检查输出，然后重复。

例如，假设你在处理 Claude Code 本身，注意到 `/compact` 停止工作并开始抛出 400 错误。找到导致此问题的确切提交的经典工具是 `git bisect`。好消息是你可以让 Claude Code 自己运行 bisect，但它需要一种测试每个提交的方法。

对于涉及交互式终端（如 Claude Code）的任务，你可以使用 tmux。模式是：

1. 启动一个 tmux 会话
2. 向它发送命令
3. 捕获输出
4. 验证是否符合预期

这是测试 `/context` 是否工作的简单示例：

```bash
tmux kill-session -t test-session 2>/dev/null
tmux new-session -d -s test-session
tmux send-keys -t test-session 'claude' Enter
sleep 2
tmux send-keys -t test-session '/context' Enter
sleep 1
tmux capture-pane -t test-session -p
```

一旦你有了这样的测试，Claude Code 就可以运行 `git bisect` 并自动测试每个提交，直到找到破坏东西的那个。

这也是为什么你的软件工程技能仍然重要的一个例子。如果你是软件工程师，你可能知道 `git bisect` 这样的工具。这些知识在与 AI 合作时仍然有用——只是以新的方式应用。

另一个例子就是写测试。让 Claude Code 写完代码后，你想测试的话，可以让它自己写测试。让它自己跑、自己修问题。当然，它不总是朝着正确方向走，有时你需要监督，但它能独立完成相当多的编码任务。

### 创造性测试策略

有时你需要在如何完成编写-测试循环方面发挥创造力。比如构建 Web 应用时，你可以用 Playwright MCP、Chrome DevTools MCP 或 Claude 的原生浏览器集成（通过 `/chrome`）。我还没试过 Chrome DevTools，试过 Playwright 和 Claude 的原生集成。总的来说 Playwright 通常效果更好。它确实用大量上下文，但 200k 的上下文窗口对单个任务或几个小任务够用了。

这两者的主要区别是 Playwright 专注于可访问性树（关于页面元素的结构化数据），而不是截图。它确实能截图，但通常不用截图来采取行动。而 Claude 的原生浏览器集成更专注于截图和通过特定坐标点击元素。有时会点随机的东西，整个过程可能很慢。

这可能会随时间改进，但默认情况下，大多数非视觉密集型任务我会选 Playwright。只有需要用登录状态而不提供凭据时（因为它在你自己的浏览器配置文件中运行），或特别需要通过坐标视觉点击东西时，我才会用 Claude 的原生浏览器集成。

这就是为什么我默认禁用 Claude 的原生浏览器集成，通过我之前定义的 `ch` 快捷方式使用它。这样 Playwright 处理大多数浏览器任务，我只在特别需要时才启用 Claude 的原生集成。

此外，你可以让它使用可访问性树引用而不是坐标。这是我在 CLAUDE.md 中添加的内容：

```markdown
# Claude for Chrome

- Use `read_page` to get element refs from the accessibility tree
- Use `find` to locate elements by description
- Click/interact using `ref`, not coordinates
- NEVER take screenshots unless explicitly requested by the user
```

根据我的个人经验，我还遇到过这样的情况：我在处理一个 Python 库（[Daft](https://github.com/Eventual-Inc/Daft)），需要在 Google Colab 上测试本地构建的版本。麻烦的是在有 Rust 后端的 Python 库在 Google Colab 上构建不太顺利——似乎不太管用。所以我需要在本地构建一个 wheel，然后手动上传，这样我就可以在 Google Colab 上运行它。我还尝试了 monkey patching，在本地构建整个 wheel 之前的短期内效果很好。我想出了这些测试策略，通过与 Claude Code 反复交流来执行它们。

我遇到的另一个情况是我需要在 Windows 上测试某些东西，但我没有运行 Windows 机器。我在同一仓库的 CI 测试失败了，因为我们在 Windows 上的 Rust 有一些问题，而我无法在本地测试。所以我需要创建一个包含所有更改的草稿 PR，以及另一个具有相同更改但在非主分支上启用 Windows CI 运行的草稿 PR。我指导 Claude Code 完成所有这些，然后直接在那个新分支中测试 CI。

## 技巧 10：Cmd+A 和 Ctrl+A 是你的好朋友

这几年我一直在说：Cmd+A 和 Ctrl+A 在 AI 世界里是好朋友，也适用于 Claude Code。

有时你想给 Claude Code 一个 URL，但它无法直接访问。可能是私有页面（不是敏感数据，只是不公开），或者是 Reddit 帖子之类的东西。这时你可以选择看到的所有内容（Mac 用 Cmd+A，其他平台 Ctrl+A），复制，然后直接粘贴到 Claude Code 中。这招挺管用。

这对终端输出也很有效。当我从 Claude Code 本身或任何其他 CLI 应用程序获得输出时，我可以使用同样的技巧：全选、复制、粘贴回 CC。非常有帮助。

有些页面默认不适合全选——但有些技巧能让它们先进入更好的状态。比如 Gmail 线程，点击「全部打印」获得打印预览（但取消实际打印）。那个页面显示线程中所有展开的邮件，可以干净地 Cmd+A 整个对话。

这适用于任何 AI，不限于 Claude Code。

## 技巧 11：用 Gemini CLI 访问受限网站

Claude Code 的 WebFetch 工具无法访问某些网站，如 Reddit。但你可以通过创建一个技能来解决这个问题，告诉 Claude 使用 Gemini CLI 作为后备。Gemini 有网络访问能力，可以获取 Claude 无法直接访问的网站内容。

这使用与技巧 9 相同的 tmux 模式——启动会话、发送命令、捕获输出。技能文件放在 `~/.claude/skills/reddit-fetch/SKILL.md`。完整内容见 [skills/reddit-fetch/SKILL.md](skills/reddit-fetch/SKILL.md)。

技能更节省 token，因为 Claude Code 只在需要时加载它们。如果你想要更简单的东西，可以把精简版放在 `~/.claude/CLAUDE.md` 中，但那会在每个对话中加载，不管你是否需要。

我通过让 Claude Code 检查 Reddit 上对 Claude Code 技能的评价来测试这个——有点元。它和 Gemini 来回通信一段时间，所以不快，但报告质量出奇地好。显然，你需要安装 Gemini CLI 才能使用这个。你也可以通过 [dx 插件](#技巧-44安装-dx-插件)安装这个技能。

## 技巧 12：打造自己的工作流

我用 Swift 从头做了自己的语音转录应用。用 Claude Code 从头做了自定义状态栏，这个用 bash。还做了套系统来简化 Claude Code 压缩 JavaScript 文件中的系统提示词。

但你不必像我这么过分。只需要照顾好自己的 CLAUDE.md，让它尽可能简洁，同时能帮你实现目标——这就够了。当然还要学这些技巧，学这些工具，还有一些重要功能。

所有这些都是对工具的投资，用来构建你想构建的东西。我觉得至少花点时间在这上面很重要。

## 技巧 13：搜索对话历史

你可以询问 Claude Code 关于你过去的对话，它会帮助你查找和搜索它们。你的对话历史本地存储在 `~/.claude/projects/` 中，文件夹名称基于项目路径（斜杠变成破折号）。

例如，位于 `/Users/yk/Desktop/projects/claude-code-tips` 的项目的对话将存储在：

```
~/.claude/projects/-Users-yk-Desktop-projects-claude-code-tips/
```

每个对话是一个 `.jsonl` 文件。你可以用基本的 bash 命令搜索它们：

```bash
# 查找所有提及 "Reddit" 的对话
grep -l -i "reddit" ~/.claude/projects/-Users-yk-Desktop-projects-*/*.jsonl

# 查找今天关于某主题的对话
find ~/.claude/projects/-Users-yk-Desktop-projects-*/*.jsonl -mtime 0 -exec grep -l -i "keyword" {} \;

# 从对话中仅提取用户消息（需要 jq）
cat ~/.claude/projects/.../conversation-id.jsonl | jq -r 'select(.type=="user") | .message.content'
```

或者直接问 Claude Code：「我们今天关于 X 谈了什么？」它会在历史中为你搜索。

## 技巧 14：用终端标签页多任务处理

在运行多个 Claude Code 实例时，保持组织有序比任何特定的技术设置更重要。我建议一次最多专注于三到四个任务。

我的方法是「级联」——每当开始新任务，就在右边开新标签页。然后从左到右扫描，从最旧的任务到最新的。方向保持一致，除非需要检查某些任务、获得通知等。

这是我的设置通常的样子：

![显示多任务处理工作流的终端标签页](assets/multitasking-terminal-tabs.png)

在这个例子中：
1. **最左边的标签页** - 一个运行我语音转录系统的持久标签页（总是保持在这里）
2. **第二个标签页** - 设置 Docker 容器
3. **第三个标签页** - 检查本地机器的磁盘使用情况
4. **第四个标签页** - 处理一个工程项目
5. **第五个标签页（当前）** - 编写这个技巧

## 技巧 15：精简系统提示词

Claude Code 的系统提示词和工具定义在你开始工作之前就占用了约 19k token（约 200k 上下文的 10%）。我创建了一个补丁系统，将其减少到约 9k token——节省约 10,000 token（约 50% 的开销）。

| 组件 | 之前 | 之后 | 节省 |
|------|------|------|------|
| 系统提示词 | 3.0k | 1.8k | 1,200 token |
| 系统工具 | 15.6k | 7.4k | 8,200 token |
| **总计** | **约 19k** | **约 9k** | **约 10k token（约 50%）** |

这是补丁前后 `/context` 的样子：

**未补丁（约 20k，10%）**

![未补丁的上下文](assets/context-unpatched.png)

**补丁后（约 10k，5%）**

![补丁后的上下文](assets/context-patched.png)

补丁通过从压缩的 CLI 包中删减冗长的示例和冗余文本来工作，同时保留所有必要的指令。

我已对此进行了大量测试，效果很好。感觉更原始——更强大，但可能没那么规范，这合理，因为系统指令更短。用起来更像专业工具。我最喜欢的是以较低的上下文开始，因为你有更多空间在填满之前继续对话，这是这个策略最好的部分。

查看 [system-prompt 文件夹](system-prompt/)获取补丁脚本和关于删减内容的完整详情。

**为什么要补丁？** Claude Code 有标志让你从文件提供简化的系统提示词（`--system-prompt` 或 `--system-prompt-file`），所以那是另一种方法。但对于工具描述，没有官方选项来自定义它们。补丁 CLI 包是唯一的方法。因为我的补丁系统用统一的方法处理所有这些，我现在保持这种方式。我可能在未来使用标志重新实现系统提示词部分。

**支持的安装方式：** npm 和原生二进制（macOS 和 Linux）。

**重要**：如果你想保留补丁后的系统提示词，请通过在 `~/.claude/settings.json` 中添加以下内容来禁用自动更新：

```json
{
  "env": {
    "DISABLE_AUTOUPDATER": "1"
  }
}
```

这适用于所有 Claude Code 会话，无论 shell 类型如何（交互式、非交互式、tmux）。当你准备好将补丁重新应用到新版本时，可以手动更新。

### 延迟加载 MCP 工具

如果你使用 MCP 服务器，它们的工具定义默认加载到每个对话中——即使你不使用它们。这会增加相当大的开销，特别是配置了多个服务器时。

启用延迟加载，使 MCP 工具只在需要时加载：

```json
{
  "env": {
    "ENABLE_TOOL_SEARCH": "true"
  }
}
```

将此添加到 `~/.claude/settings.json`。Claude 将按需搜索和加载 MCP 工具，而不是一开始就全部加载。从版本 2.1.7 开始，当 MCP 工具描述超过上下文窗口的 10% 时，这会自动发生。

## 技巧 16：用 Git Worktree 并行处理分支

如果你同时在同一项目上处理多件事，不想让它们冲突，Git worktree 是个好办法。让 Claude Code 创建一个 git worktree 并在那里开始工作——你不必担心具体的语法。

基本思想是不同目录处理不同分支。本质上是一个分支 + 一个目录。

你可以在我之前多任务处理技巧中讨论的级联方法之上添加 Git worktree 这一层。

### 什么是 git worktree？

git worktree 就像任何其他 git 分支，但有专门分配给它的新目录。

所以如果你在处理，比如说，main 分支和 feature-branch-1，那么没有 git worktree，你一次只能处理它们中的一个，因为你的项目文件夹一次只能设置为一个分支。

然而，使用 git worktree，你可以在原始项目文件夹中继续处理 main 分支（或任何其他分支），同时在另一个新文件夹中处理 feature-branch-1。

![显示在不同目录中并行分支工作的 Git worktree 图解](assets/git-worktrees.png)

## 技巧 17：长时间任务的手动指数退避

在等待长时间运行的任务（如 Docker 构建或 GitHub CI）时，你可以让 Claude Code 执行手动指数退避。指数退避是软件工程中的常见技术，但这里也可以用。让 Claude Code 以递增的睡眠间隔检查状态——一分钟，然后两分钟，然后四分钟，以此类推。这不是传统意义上的程序化执行——AI 在手动执行——但效果很好。

这样代理可以持续检查状态，完成后通知你。

（对于 GitHub CI，`gh run watch` 存在但会持续输出许多行，浪费 token。用 `gh run view <run-id> | grep <job-name>` 的手动指数退避实际上更节省 token。这也是个通用技术，即使没有专门的等待命令也能很好地工作。）

例如，如果你有一个 Docker 构建在后台运行：

![手动指数退避检查 Docker 构建进度](assets/manual-exponential-backoff.png)

它会一直持续到任务完成。

## 技巧 18：把 Claude Code 当写作助手

Claude Code 是个不错的写作助手和伙伴。我的用法是先给它所有关于想写什么的上下文，然后通过语音给详细指令。这给我初稿。不够好就试几次。

然后我基本上逐行检查。说好吧，一起看看。我喜欢这一行是因为这些原因。这一行需要移到那边。这一行需要以这种方式改。我也可能会问参考资料。

所以这是这种来回的过程，可能左边是终端，右边是代码编辑器：

![与 Claude Code 并排写作工作流](assets/writing-assistant-side-by-side.png)

这种来回的过程往往很有效。

## 技巧 19：Markdown 太棒了

通常人们写新文档时，可能会用 Google Docs 或 Notion 之类的东西。但现在老实说，最高效的方式是 markdown。

Markdown 在 AI 之前就很好了，但特别是对 Claude Code，因为它的效率——如我之前关于写作所说的——我认为 markdown 的价值更高了。每当想写博客文章甚至 LinkedIn 帖子，和 Claude Code 对话，让它保存为 markdown，然后从那里开始。

一个小技巧：如果把 markdown 内容粘贴到不容易接受的平台，先粘贴到一个新的 Notion 文件中，然后从 Notion 复制到其他平台。Notion 会将其转换为其他平台可以接受的格式。如果常规粘贴不行，试试 Command + Shift + V 不带格式粘贴。

## 技巧 20：用 Notion 保留粘贴时的链接

事实证明反向操作也有效。如果有来自其他地方带链接的文本，比如 Slack，复制它。直接粘贴到 Claude Code，不显示链接。但先放在 Notion 文档中，然后从那里复制，你会得到 markdown 格式，Claude Code 可以读取。

## 技巧 21：用容器处理长时间高风险任务

常规会话更适合有条理的工作，需要控制给予的权限并仔细审查输出。容器化环境适合 `--dangerously-skip-permissions` 会话，不必为每件小事授予权限。可以让它自己跑一段时间。

对于研究或实验、需要长时间且可能有风险的事情很有用。一个很好的例子是技巧 11 中的 Reddit 研究工作流，reddit-fetch 技能通过 tmux 与 Gemini CLI 来回通信。在主系统上无人值守运行有风险，但在容器中，出问题也是隔离的。

另一个例子是我如何创建这个仓库中的[系统提示词补丁脚本](system-prompt/)。当 Claude Code 新版本发布时，我需要更新压缩 CLI 包的补丁。与其在主机上用 `--dangerously-skip-permissions` 运行（可以访问所有东西），我在容器中运行。Claude Code 可以探索压缩的 JavaScript，找到变量映射，创建新的补丁文件，不需要我批准每件小事。

它基本上能够自己完成迁移。尝试应用补丁，发现有些在新版本中不起作用，迭代修复它们，甚至根据学到的东西改进了供未来实例使用的[说明文档](system-prompt/UPGRADING.md)。

我甚至创建了 [SafeClaw](https://github.com/ykdojo/safeclaw) 让运行容器化 Claude Code 会话变得容易。可以启动多个隔离会话，每个都有一个 Web 终端，并从仪表板管理它们。它用了这个仓库中的几个自定义配置，包括优化的系统提示词、[DX 插件](#技巧-44安装-dx-插件)和[状态栏](#技巧-0自定义状态栏)。

### 进阶：在容器中编排工作 Claude Code

可以通过让本地 Claude Code 控制另一个在容器中运行的 Claude Code 实例来进一步。技巧是用 tmux 作为控制层：

1. 本地 Claude Code 启动一个 tmux 会话
2. 在那个 tmux 会话中，运行或连接到容器
3. 在容器内部，Claude Code 用 `--dangerously-skip-permissions` 运行
4. 外部 Claude Code 用 `tmux send-keys` 发送提示词，用 `capture-pane` 读取输出

这样你有一个完全自主的「工作」Claude Code，可以运行实验或长时间任务，无需批准每个操作。完成后，本地 Claude Code 可以把结果拉回来。出问题的话，所有都被沙箱化在容器中。

### 进阶：多模型编排

除了 Claude Code，还可以在容器中运行不同的 AI CLI——Codex、Gemini CLI 或其他。我试过用 OpenAI Codex 进行代码审查，效果不错。重点不是不能在主机上直接运行这些 CLI——显然可以。价值在于 Claude Code 的 UI/UX 够流畅，可以直接和它对话，让它处理编排：启动不同的模型，在容器和主机之间发送数据。Claude Code 成为协调一切的中心接口，而不是手动切换终端和复制粘贴。

## 技巧 22：提升 Claude Code 技能的最好方法就是多用

最近我看到一位世界级攀岩运动员接受采访。她被问到：「你如何提升攀岩技能？」她简单地说：「通过攀岩。」

我有同样的感觉。当然，可以做一些补充的事情，比如看视频、读书、学技巧。但使用 Claude Code 是学习如何用它的最好方法。使用 AI 总体上是学习如何用 AI 的最好方法。

我喜欢把它想象成十亿 token 规则，而不是 10,000 小时规则。想在 AI 方面变得更好，真正对它如何工作有良好的直觉，最好的方法是消耗大量 token。现在这成为可能。特别是 Opus 4.5，够强大也够实惠，可以同时运行多个会话。不必那么担心 token 使用量，自由很多。

## 技巧 23：克隆/复刻和半克隆对话

有时你想从对话中的特定点尝试不同的方法，不想丢失原始线程。[clone-conversation 脚本](scripts/clone-conversation.sh)让你用新的 UUID 复制对话，这样可以分支出去。

**内置替代方案（最新版本）：** Claude Code 现在有原生分支功能：
- `/fork` - 在对话中复刻当前会话
- `--fork-session` - 与 `--resume` 或 `--continue` 一起使用（例如 `claude -c --fork-session`）

由于 `--fork-session` 没有短格式，你可以在 `~/.zshrc` 或 `~/.bashrc` 中添加这个函数，使用 `--fs` 作为快捷方式：

```bash
claude() {
  local args=()
  for arg in "$@"; do
    if [[ "$arg" == "--fs" ]]; then
      args+=("--fork-session")
    else
      args+=("$arg")
    fi
  done
  command claude "${args[@]}"
}
```

这会拦截所有 `claude` 命令，将 `--fs` 展开为 `--fork-session`，其他不变。也适用于别名（见[技巧 7](#技巧-7设置终端别名快速启动)）：`c -c --fs`、`ch -c --fs` 等。

下面的克隆脚本早于这些内置选项，但半克隆脚本对于减少上下文仍然是独特的。

第一条消息被标记为 `[CLONED <timestamp>]`（例如 `[CLONED Jan 7 14:30]`），这会出现在 `claude -r` 列表和对话内部。

手动设置方法：符号链接两个文件：
```bash
ln -s /path/to/this/repo/scripts/clone-conversation.sh ~/.claude/scripts/clone-conversation.sh
ln -s /path/to/this/repo/skills/clone ~/.claude/skills/clone
```

或通过 [dx 插件](#技巧-44安装-dx-插件)安装——不需要符号链接。

然后在任何对话中输入 `/clone`（如果使用插件则是 `/dx:clone`），Claude 会处理查找会话 ID 和运行脚本。

我已对此进行了广泛测试，克隆效果非常好。

### 半克隆以减少上下文

当对话变得太长时，[half-clone-conversation 脚本](scripts/half-clone-conversation.sh)只保留后半部分。这减少了 token 使用量，同时保留你最近的工作。第一条消息被标记为 `[HALF-CLONE <timestamp>]`（例如 `[HALF-CLONE Jan 7 14:30]`）。

手动设置方法：符号链接两个文件：
```bash
ln -s /path/to/this/repo/scripts/half-clone-conversation.sh ~/.claude/scripts/half-clone-conversation.sh
ln -s /path/to/this/repo/skills/half-clone ~/.claude/skills/half-clone
```

或通过 [dx 插件](#技巧-44安装-dx-插件)安装——不需要符号链接。

### 用 hook 自动建议半克隆

可选地，你可以使用 [hook](https://docs.anthropic.com/en/docs/claude-code/hooks) 在上下文太长时自动触发 `/half-clone`。[check-context 脚本](scripts/check-context.sh)在每次 Claude 响应后运行并检查上下文使用量。如果超过 85%，它会告诉 Claude 运行 `/half-clone`，这会创建一个只包含后半部分的新对话，这样新代理可以在那里继续。

设置方法：首先复制脚本：
```bash
cp /path/to/this/repo/scripts/check-context.sh ~/.claude/scripts/check-context.sh
chmod +x ~/.claude/scripts/check-context.sh
```

然后将 hook 添加到你的 `~/.claude/settings.json`：
```json
{
  "hooks": {
    "Stop": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "~/.claude/scripts/check-context.sh"
          }
        ]
      }
    ]
  }
}
```

这需要禁用自动压缩（`/config` > Auto-compact > false），否则 Claude Code 可能会在 hook 有机会触发之前压缩上下文。当触发时，hook 会阻止 Claude 停止并告诉它运行 `/half-clone`。相比自动压缩的优势是半克隆是确定性的且快速——它保持你的实际消息完整，而不是总结它们。

### 克隆脚本的推荐权限

两个克隆脚本都需要读取 `~/.claude`（用于对话文件和历史）。为了避免来自任何项目的权限提示，把这个加到全局设置（`~/.claude/settings.json`）：
```json
{
  "permissions": {
    "allow": ["Read(~/.claude)"]
  }
}
```

## 技巧 24：用 realpath 获取绝对路径

当你需要告诉 Claude Code 关于不同文件夹中的文件时，用 `realpath` 获取完整绝对路径：

```bash
realpath some/relative/path
```

## 技巧 25：理解 CLAUDE.md、技能、斜杠命令和插件的区别

这些是有些相似的功能，我最初觉得很困惑。一直在解构它们，尽可能理解，所以分享学到的东西。

**CLAUDE.md** 是最简单的一个。一堆被视为默认提示词的文件，无论什么都加载到每个对话的开头。好处是简单。可以在特定项目（`./CLAUDE.md`）或全局（`~/.claude/CLAUDE.md`）中解释项目是什么。

**技能**就像结构更好的 CLAUDE.md 文件。可以在相关时被 Claude 自动调用，或由用户手动用斜杠调用（例如 `/my-skill`）。比如可以有个技能，当你问某个语言的单词如何发音时，打开一个格式正确的 Google Translate 链接。如果这些指令在技能中，只在需要时加载。如果在 CLAUDE.md 中，已经存在并占用空间。所以理论上技能更节省 token。

**斜杠命令**与技能相似，都是将指令单独打包。可以由用户手动调用，或由 Claude 自己调用。如果需要更精确的东西，按自己的节奏在正确的时间调用，斜杠命令是要用的工具。

技能和斜杠命令在功能方式上非常相似。区别在于设计的意图——技能主要设计给 Claude 用，斜杠命令主要设计给用户用。不过，它们最终[合并了它们](https://www.reddit.com/r/ClaudeAI/comments/1q92wwv/merged_commands_and_skills_in_213_update/)，正如我曾[建议这个改变](https://github.com/anthropics/claude-code/issues/13115)。

**插件**是将技能、斜杠命令、代理、hook 和 MCP 服务器打包在一起的方式。但插件不必使用所有这些。Anthropic 官方的 `frontend-design` 插件本质上只是一个技能，没别的。它可以作为独立技能分发，但插件格式使安装更容易。

比如，我构建了一个名为 `dx` 的插件，将这个仓库中的斜杠命令和技能打包在一起。可以在[安装 dx 插件](#技巧-44安装-dx-插件)部分看到它是如何工作的。

## 技巧 26：交互式 PR 审查

Claude Code 很适合 PR 审查。过程很简单：让它用 `gh` 命令检索 PR 信息，然后按你想要的方式审查。

可以做一般性审查，或逐文件、逐步进行。你控制节奏。控制想看多少细节和在什么复杂度级别工作。也许只想了解一般结构，或者想让它也跑测试。

关键区别是 Claude Code 充当交互式 PR 审查者，而不只是一次性机器。一些 AI 工具擅长一次性审查（包括最新的 GPT 模型），但用 Claude Code 你可以对话。

## 技巧 27：把 Claude Code 当研究工具

Claude Code 对于研究很棒。本质上是个 Google 替代品或深度研究替代品，但在几个方面更先进。无论研究为什么某些 GitHub Actions 失败（我最近做很多）、在 Reddit 上做情感或市场分析、探索代码库，还是探索公共信息找东西——都能做到。

关键是给它正确的信息和关于如何访问这些信息的指令。可能是 `gh` 终端命令访问，或容器方法（技巧 21），或通过 Gemini CLI 的 Reddit（技巧 11），或通过 MCP 如 Slack MCP 的私人信息，或 Cmd+A / Ctrl+A 方法（技巧 10）——无论什么。如果 Claude Code 无法加载某些 URL，可以试试 Playwright MCP 或 Claude 的原生浏览器集成（见技巧 9）。

事实上，我甚至能够[用 Claude Code 做研究省了 10,000 美元](content/how-i-saved-10k-with-claude-code.md)。

## 技巧 28：掌握多种验证输出的方法

如果输出是代码，一种验证方法是让它写测试，确保测试总体看起来没问题。这是一种方法，但当然可以在 Claude Code UI 上随着进展检查它生成的代码。另一件事是可以用可视化 Git 客户端如 GitHub Desktop。我用它。不是完美的产品，但够用，可以快速检查更改。让它生成 PR（如我之前提到的）也是个好方式。让它创建一个草稿 PR，在变成真正的 PR 之前检查内容。

另一个是让它检查自己的工作。如果给你某种输出，比如来自某些研究，你可以说「你确定吗？能再检查一遍吗？」我最喜欢的提示词之一是「仔细检查所有东西，产生的每一条主张，最后制作一个能验证的内容表格」——这很有效。

## 技巧 29：把 Claude Code 当 DevOps 工程师

我想专门为此创建一个单独的技巧，因为对我来说效果很好。每当有 GitHub Actions CI 失败，就交给 Claude Code，说「深入调查这个问题，尝试找到根本原因。」有时给表面层面的答案，但如果继续问——是由特定提交、特定 PR 引起的，还是不稳定的问题？——它真的帮你深入挖掘那些难以手动挖掘的棘手问题。需要翻阅一堆日志，手动做超痛苦，但 Claude Code 能处理很多那样的事情。

我把这个工作流打包成一个 `/gha` 斜杠命令——只需运行 `/gha <url>` 加上任何 GitHub Actions URL，它会自动调查失败、检查不稳定性、识别破坏性提交并建议修复。你可以在 [skills 文件夹](skills/gha/SKILL.md)中找到它，或通过 [dx 插件](#技巧-44安装-dx-插件)安装。

一旦确定了具体问题，可以创建一个草稿 PR 并经历我之前提到的一些技巧——检查输出，确保看起来不错，让它验证自己的输出，然后变成真正的 PR 来修复问题。对我个人来说效果不错。

## 技巧 30：保持 CLAUDE.md 简洁并定期检查

保持 CLAUDE.md 简洁并尽可能精简很重要。可以完全从没有 CLAUDE.md 开始。如果发现自己一遍遍告诉 Claude Code 同样的事情，那就把它添加到 CLAUDE.md。我知道有个选项可以通过 `#` 符号来做，但我更喜欢直接让 Claude Code 添加到项目级 CLAUDE.md 或全局 CLAUDE.md，它会知道确切编辑什么。

![保持简单梗图](assets/keep-it-simple-meme.jpg)

定期审查 CLAUDE.md 文件也很重要，因为它们可能随时间过时。一段时间前有意义的指令可能不再相关，或者有了应该记录的新模式。我为此创建了一个名为 [`review-claudemd`](skills/review-claudemd/SKILL.md) 的技能，分析最近的对话并为 CLAUDE.md 文件建议改进。

## 技巧 31：Claude Code 是通用接口

我曾经认为使用 Claude Code，CLI 就像是新的 IDE，在某种程度上仍然如此。我觉得这是个很好的首选地方，每当想快速编辑项目之类的时候打开项目。但根据项目的严重程度，要更仔细地检查输出，而不是停留在氛围编程层面。

但同样成立的是，更一般的情况是，Claude Code 真的是计算机、数字世界、任何数字问题的通用接口。很多情况下可以让它自己解决。比如需要快速编辑视频，直接让它做——它可能会通过 ffmpeg 或类似的东西来解决。想转录一堆本地音频或视频文件，直接让它做——它可能会建议通过 Python 用 Whisper。想分析 CSV 文件中的一些数据，它可能会建议用 Python 或 JavaScript 来可视化。当然有了网络访问——Reddit、GitHub、MCP——可能性无限。

它也非常适合想在本地计算机上执行的任何操作。比如存储空间不足，直接让它给一些如何清理的建议。它会查看本地文件夹和文件，尝试找到占用大量空间的东西，然后给如何清理的建议——也许删除特别大的文件。我的情况，有一些非常大的 Final Cut Pro 文件应该清理。Claude Code 告诉了我。也许它会告诉你用 `docker system prune` 清理未使用的 Docker 镜像和容器。或者也许会告诉你清理一些从未意识到还在那里的缓存。无论想在计算机上做什么，Claude Code 是我现在首选的地方。

我觉得这有点有趣，因为计算机是从文本界面开始的。而在某种程度上，我们正在回到这种文本界面，可以一次打开三四个标签页，如我之前提到的。对我来说，真的很令人兴奋。感觉有第二个大脑，在某种意义上。但因为结构化的方式，因为只是一个终端标签页，可以打开第三个大脑、第四个大脑、第五个大脑、第六个大脑。随着模型变得更强大，可以委托给这些东西思考的比例——不是重要的事情，而是不想做或觉得无聊或太乏味的事情——可以让它们处理。如我提到的，一个很好的例子是调查 GitHub Actions。谁想做那个？但事实证明这些代理真的擅长那些无聊的任务。

## 技巧 32：选择正确的抽象层级

如我之前提到的，有时停留在氛围编程级别是可以的。如果在处理一次性项目或代码库的非关键部分，不一定需要担心每一行代码。但其他时候，想深入一点——查看文件结构和函数、单独的代码行，甚至检查依赖项。

![氛围编程光谱](assets/vibe-coding-spectrum.png)

关键是不是非黑即白的。有些人说氛围编程不好，因为不知道自己在做什么，但有时完全没问题。但其他时候，深入挖掘、用软件工程技能、在粒度级别理解代码，或复制粘贴代码库的部分或特定错误日志来问 Claude Code 关于它们的具体问题是有帮助的。

这有点像在探索一座巨大的冰山。如果想停留在氛围编程级别，可以从上面飞过，从远处检查它。然后可以靠近一点。可以进入潜水模式。可以越来越深入，Claude Code 作为向导。

## 技巧 33：审查你批准的命令

我最近看到[这篇帖子](https://www.reddit.com/r/ClaudeAI/comments/1pgxckk/claude_cli_deleted_my_entire_home_directory_wiped/)，某人的 Claude Code 运行了 `rm -rf tests/ patches/ plan/ ~/` 并删除了主目录。很容易把它当作氛围编程者的错误而忽略，但这种错误可能发生在任何人身上。所以定期审查批准的命令很重要。为了更容易，我构建了 **cc-safe**——一个扫描 `.claude/settings.json` 文件中危险批准命令的 CLI。

它检测这样的模式：
- `sudo`、`rm -rf`、`Bash`、`chmod 777`、`curl | sh`
- `git reset --hard`、`npm publish`、`docker run --privileged`
- 还有更多——对容器有感知，所以 `docker exec` 命令会被跳过

它递归扫描所有子目录，所以可以把它指向项目文件夹一次检查所有东西。可以手动运行或让 Claude Code 来跑：

```bash
npm install -g cc-safe
cc-safe ~/projects
```

或直接用 npx 运行：

```bash
npx cc-safe .
```

GitHub: [cc-safe](https://github.com/ykdojo/cc-safe)

## 技巧 34：多写测试（使用 TDD）

随着用 Claude Code 写更多代码，更容易犯错误。PR 审查和可视化 Git 客户端帮助发现问题（如我之前提到的），但随着代码库变大，写测试至关重要。

可以让 Claude Code 为自己的代码写测试。有人说 AI 不能测试自己的工作，但事实证明可以——类似于人脑的工作方式。写测试时，你在以不同的方式思考同一个问题。这同样适用于 AI。

我发现 TDD（测试驱动开发）与 Claude Code 配合得不错：

1. 先写测试
2. 确保它们失败
3. 提交测试
4. 编写让它们通过的代码

这实际上是我构建 [cc-safe](https://github.com/ykdojo/cc-safe) 的方式。通过先写失败的测试并在实现之前提交，为代码应该做什么创建了清晰的契约。Claude Code 然后有个具体的目标要达到，可以通过运行测试来验证实现是否正确。

如果想更加确定，自己审查测试，确保不会做愚蠢的事情比如只返回 true。

## 技巧 35：在未知领域更勇敢些，迭代解决问题

自从开始更密集地使用 Claude Code，我注意到在未知领域变得越来越勇敢。

比如开始在 [Daft](https://github.com/Eventual-Inc/Daft) 工作时，注意到前端代码有问题。我不是 React 专家，但还是决定深入研究。开始问关于代码库和问题的相关问题。最终解决了它，因为我知道怎么用 Claude Code 迭代解决问题。

最近发生了类似的事。在为 Daft 用户构建指南，遇到了一些非常具体的问题：cloudpickle 不适用于带 Pydantic 的 Google Colab，还有另一个涉及 Python 和一点 Rust 的问题，在 JupyterLab 中东西没有正确打印，尽管在终端中正常。我以前从未处理过 Rust。

本可以只创建一个 issue 让其他工程师处理。但想，让我深入研究代码库。Claude Code 提出了初步解决方案，但不太好。所以我放慢了。一位同事建议我们就禁用那部分，但我不想要任何回归。能找到更好的解决方案吗？

接下来是协作和迭代的过程。Claude Code 建议了潜在的根本原因和解决方案。我实验了那些。一些是死胡同，所以换了方向。在此过程中，我控制节奏。有时走得更快，比如让它探索不同的解决方案空间或代码库的不同部分。有时走得更慢，问「这行到底是什么意思？」控制抽象级别，控制速度。

最终找到了一个非常优雅的解决方案。教训是：即使在未知的世界，可以用 Claude Code 做比想象的多得多的事情。

## 技巧 36：在后台运行 bash 命令和子代理

当有一个长时间运行的 bash 命令在 Claude Code 中，可以按 Ctrl+B 将它移到后台运行。Claude Code 知道如何管理后台进程——它可以稍后使用 BashOutput 工具检查它们。

当意识到一个命令比预期花更长时间，想让 Claude 在此期间做其他事情时，这很有用。然后可以让它使用我在技巧 17 中提到的指数退避方法检查进度，或者就让它在进程运行时完全做其他事情。

Claude Code 也能够在后台运行子代理。如果需要做长时间运行的研究或让代理定期检查某些东西，不必让它在后台运行。只需让 Claude Code 在后台运行代理或任务，它会处理，而你继续其他工作。

### 策略性使用子代理

除了只是在后台运行东西，当有一个大任务要分解时，子代理也很有用。比如有一个需要分析的巨大代码库，可以让子代理以不同方式分析或并行查看代码库的不同部分。只需让 Claude 启动多个子代理来处理不同的部分。

可以通过直接询问来自定义子代理：
- **多少个**——让 Claude 启动想要的数量
- **后台还是前台**——要求在后台运行，或按 Ctrl+B
- **哪个模型**——根据每个任务的复杂度要求 Opus、Sonnet 或 Haiku（子代理默认为 Sonnet）

## 技巧 37：个性化软件时代已来

我们正在进入个性化、定制软件的时代。自从 AI 出现——ChatGPT 总体上，但特别是 Claude Code——我注意到能够创建更多软件，有时只为自己，有时为小项目。

如我之前在这份文档中提到的，我创建了一个每天用来和 Claude Code 对话的自定义转录工具。创建了自定义 Claude Code 本身的方式。还用 Python 更快地完成了一堆数据可视化和数据分析任务。

这是另一个例子：[korotovsky/slack-mcp-server](https://github.com/korotovsky/slack-mcp-server)，一个有近 1,000 星的流行 Slack MCP，设计为作为 Docker 容器运行。我在自己的 Docker 容器内部顺畅使用它时遇到麻烦（Docker-in-Docker 的复杂性）。与其纠结于那个设置，我直接让 Claude Code 用 Slack 的 Node SDK 写了一个 CLI。效果很好。

这是个激动人心的时代。无论想完成什么，可以让 Claude Code 去做。如果够小，一两个小时就能构建。我甚至创建了一个[幻灯片模板](https://ykdojo.github.io/claude-code-tips/content/spectrum-slides.html)——一个带 CSS 和 JavaScript 的单个 HTML 文件，让你嵌入一个交互式、持久的终端进程。

## 技巧 38：导航和编辑输入框

Claude Code 的输入框设计为模拟常见的终端/readline 快捷键，如果习惯在终端工作，感觉会很自然。以下是几个有用的：

**导航：**
- `Ctrl+A` - 跳转到行首
- `Ctrl+E` - 跳转到行尾
- `Option+Left/Right`（Mac）或 `Alt+Left/Right` - 按词向后/向前跳转

**编辑：**
- `Ctrl+W` - 删除前一个词
- `Ctrl+U` - 从光标删除到行首
- `Ctrl+K` - 从光标删除到行尾
- `Ctrl+C` / `Ctrl+L` - 清除当前输入
- `Ctrl+G` - 在外部编辑器中打开提示词（对于粘贴长文本有用，因为直接粘贴到终端可能很慢）

如果熟悉 bash、zsh 或其他 shell，会感觉像在家一样。

对于 `Ctrl+G`，编辑器由你的 `EDITOR` 环境变量决定。你可以在 shell 配置（`~/.zshrc` 或 `~/.bashrc`）中设置：

```bash
export EDITOR=vim      # 或 nano, code, nvim 等
```

或在 `~/.claude/settings.json` 中（需要重启）：

```json
{
  "env": {
    "EDITOR": "vim"
  }
}
```

**输入换行（多行输入）：**

最快的方法无需任何设置在任何地方都有效：输入 `\` 然后按 Enter 创建新行。对于键盘快捷键，在 Claude Code 中运行 `/terminal-setup`。在 Mac Terminal.app 上，我使用 Option+Enter。

**粘贴图片：**
- `Ctrl+V`（Mac/Linux）或 `Alt+V`（Windows）- 从剪贴板粘贴图片

注意：在 Mac 上，是 `Ctrl+V`，不是 `Cmd+V`。

## 技巧 39：花点时间规划，但也要快速原型验证

你想花足够的时间规划，这样 Claude Code 就知道要构建什么以及如何构建。这意味着尽早做出高层决策：用什么技术、项目应该如何结构化、每个功能放哪里、东西放哪些文件里。尽早做出好的决定很重要。

有时原型验证对此有帮助。只需快速做一个简单的原型，可能就能说「好的，这个技术适合这个特定目的」或「另一个技术更好」。

比如，我最近在实验创建一个 diff 查看器。先试了一个简单的 bash 原型，用 tmux 和 lazygit，然后试了用 Ink 和 Node 做自己的 git 查看器。在不同的事情上遇到了很多麻烦，最终没有发布这些结果中的任何一个。但通过这个项目我重新认识到的是规划和原型验证的重要性。我发现只需在让它写代码之前在开始时规划得更好一点，就能够更好地指导它。仍然需要在编码过程中指导它，但先让它规划一点真的很有帮助。

可以通过按 Shift+Tab 切换到计划模式。或者可以直接让 Claude Code 在写任何代码之前制定一个计划。

## 技巧 40：简化过度复杂的代码

我发现 Claude Code 有时会把事情过度复杂化，写太多代码。做出没要求的更改。似乎有写更多代码的倾向。如果遵循了本指南中的其他技巧，代码可能工作正确，但会很难维护，很难检查。如果不够审查，可能有点像噩梦。

所以有时想检查代码并让它简化东西。可以自己修，但也可以直接让它简化。可以问这样的问题「为什么要做这个特定的更改？」或「为什么要加这一行？」

有些人说如果只通过 AI 写代码，永远不会理解它。但只有当没有问足够的问题时才是真的。如果确保理解每一个东西，实际上可以比其他方式更快地理解代码，因为可以问 AI 关于它。特别是处理大项目时。

注意这同样适用于散文。Claude Code 经常尝试在最后一段总结前面的段落，或在最后一句总结前面的句子。可能变得相当重复。有时这有帮助，但大多数时候需要让它删除或简化。

## 技巧 41：自动化的自动化

归根结底，这都是关于自动化的自动化。我的意思是，我发现这是不仅变得更高效，而且让过程更有趣的最好方式。至少对我来说，这整个自动化的自动化过程真的很有趣。

我从 ChatGPT 开始，想自动化复制粘贴和运行 ChatGPT 在终端中给我的命令的过程。我通过构建一个名为 [Kaguya](https://github.com/ykdojo/kaguya) 的 ChatGPT 插件自动化了整个过程。从那时起，我一直朝着越来越多的自动化努力。

如今，幸运的是，我们甚至不必构建像那样的工具，因为像 Claude Code 这样的工具存在并且工作得不错。随着越来越多地使用它，我发现自己想，好吧，如果能自动化打字的过程呢？所以我用 Claude Code 本身构建了语音转录应用，如我之前提到的。

然后我开始想，发现自己有时重复自己。所以把那些东西放在 CLAUDE.md 中。然后会想，好吧，有时一遍遍运行同一个命令。怎么自动化那个？也许可以让 Claude Code 去做。或者可以放在技能中。或者甚至可以让它创建一个脚本，这样就不必一遍遍重复同样的过程。

我认为最终这就是我们前进的方向。每当发现自己一遍遍重复同样的任务或命令，几次没问题，但如果一遍遍重复，那就想办法自动化整个过程。

## 技巧 42：分享知识，贡献力量

这个技巧与其他技巧有点不同。我发现通过尽可能多地学习，能够与周围的人分享知识。也许通过像这样的帖子，也许甚至书籍、课程、视频。我最近还为我在 Daft 的同事举办了一次[内部会议](https://www.daft.ai/blog/how-we-use-ai-coding-agents)。非常有回报。

每当我分享技巧时，经常获得回馈。比如分享缩短系统提示词和工具描述的技巧（技巧 15）时，一些人告诉我可以用作替代的 `--system-prompt` 标志。另一次，分享了斜杠命令和技能之间的区别（技巧 25），我从那篇 Reddit 帖子的评论中学到了新东西。

所以分享你的知识不仅是建立品牌或巩固学习，也是通过这个过程学习新东西。并不总是单行道。

在贡献方面，我一直在向 Claude Code 仓库发 issue。想，好吧，如果他们听了，很酷。如果没听，那也完全没问题。我没有任何期望。但在版本 2.0.67 中，我注意到他们采纳了我报告中的多个建议：

- 修复了在 `/permissions` 中删除权限规则后滚动位置重置的问题
- 在 `/permissions` 命令中添加了搜索功能

团队对功能请求和错误报告的反应有多快是相当惊人的。但这有道理，因为他们正在用 Claude Code 构建 Claude Code 本身。

## 技巧 43：持续学习！

有几种有效的学习 Claude Code 的方式：

**问 Claude Code 本身** - 如果有关于 Claude Code 的问题，直接问。Claude Code 有个专门的子代理来回答关于自身功能、斜杠命令、设置、hook、MCP 服务器等的问题。

**查看发布说明** - 输入 `/release-notes` 看当前版本的新功能。这是了解最新功能的最好方式。

**向社区学习** - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/) subreddit 是向其他用户学习、看看人们在使用什么工作流的好地方。

**关注 Ado 的技巧** - Ado（[@adocomplete](https://x.com/adocomplete)）是 Anthropic 的 DevRel，在 2025 年 12 月整个月发布了每日 Claude Code 技巧，在他的「Advent of Claude」系列中。虽然这个特定系列已经结束，他继续在 X 上分享有用的技巧。

- [Twitter/X: Advent of Claude 帖子](https://x.com/search?q=from%3Aadocomplete%20advent%20of%20claude&src=typed_query&f=live)
- [LinkedIn: Advent of Claude 帖子](https://www.linkedin.com/search/results/content/?fromMember=%5B%22ACoAAAFdD3IBYHwKSh6FsyGqOh1SpbrZ9ZHTjnI%22%5D&keywords=advent%20of%20claude&origin=FACETED_SEARCH&sid=zDV&sortBy=%22date_posted%22)

## 技巧 44：安装 dx 插件

这个仓库也是一个名为 `dx`（开发者体验）的 Claude Code 插件。它把上面技巧中的几个工具打包成一个安装：

| 技能 | 描述 |
|------|------|
| `/dx:gha <url>` | 分析 GitHub Actions 失败（技巧 29） |
| `/dx:handoff` | 为上下文连续性创建交接文档（技巧 8） |
| `/dx:clone` | 克隆对话以分支出去（技巧 23） |
| `/dx:half-clone` | 半克隆以减少上下文（技巧 23） |
| `/dx:reddit-fetch` | 通过 Gemini CLI 获取 Reddit 内容（技巧 11） |
| `/dx:review-claudemd` | 审查对话以改进 CLAUDE.md 文件（技巧 30） |

**两条命令安装：**

```bash
claude plugin marketplace add ykdojo/claude-code-tips
claude plugin install dx@ykdojo
```

安装后，命令可用为 `/dx:clone`、`/dx:half-clone`、`/dx:handoff` 和 `/dx:gha`。`reddit-fetch` 技能在问 Reddit URL 时自动调用。`review-claudemd` 技能分析最近的对话并为 CLAUDE.md 文件建议改进。对于克隆命令，见[推荐的权限](#克隆脚本的推荐权限)。

**推荐伴侣：** [Playwright MCP](https://github.com/microsoft/playwright-mcp) 用于浏览器自动化 - 用 `claude mcp add -s user playwright npx @playwright/mcp@latest` 添加

## 技巧 45：快速设置脚本

如果想一次性设置这个仓库中的多个推荐，有个设置脚本处理其中的许多：

```bash
bash <(curl -s https://raw.githubusercontent.com/ykdojo/claude-code-tips/main/scripts/setup.sh)
```

脚本会显示它将配置的所有内容，让你跳过任何项目：

```
INSTALLS:
  1. DX plugin - slash commands (/dx:gha, /dx:clone, /dx:handoff) and skills (reddit-fetch)
  2. cc-safe - scans your settings for risky approved commands like 'rm -rf' or 'sudo'

SETTINGS (~/.claude/settings.json):
  3. Status line - shows model, git branch, uncommitted files, token usage at bottom of screen
  4. Disable auto-updates - prevents Claude Code from auto-updating (useful for system prompt patches)
  5. Lazy-load MCP tools - only loads MCP tool definitions when needed, saves context
  6. Read(~/.claude) permission - allows clone/half-clone commands to read conversation history
  7. Read(//tmp/**) permission - allows reading temporary files without prompts
  8. Disable attribution - removes Co-Authored-By from commits and attribution from PRs

SHELL CONFIG (~/.zshrc or ~/.bashrc):
  9. Aliases: c=claude, ch=claude --chrome, cs=claude --dangerously-skip-permissions
  10. Fork shortcut: --fs expands to --fork-session (e.g., claude -c --fs)

Skip any? [e.g., 1 4 7 or Enter for all]:
```

---

📺 **相关演讲**：[Claude Code 大师课](https://youtu.be/9UdZhTnMrTA) - 来自 31 个月代理编程的经验教训和项目示例

📝 **故事**：[我如何用 Claude Code 找到全职工作](content/how-i-got-a-job-with-claude-code.md)

📰 **通讯**：[有纪律和技巧的代理编程](https://agenticcoding.substack.com/) - 将代理编程实践提升到更高水平

## 技巧 46：组建团队

Claude Code 有一个内置的团队功能，可以让你生成多个专业代理（队友）协同处理复杂任务。每个队友都有自己的对话上下文，可以给你或其他队友发送消息。

### 何时使用团队

在处理复杂、多步骤任务并受益于并行工作时使用团队：
- **全栈功能** - 前端工作 + 后端工作同时进行
- **大型重构** - 在跨多个文件进行更改时保持测试通过
- **多阶段项目** - 研究 → 规划 → 实施
- **探索 + 实施** - 一个代理探索，另一个实施

### 工作原理

1. **创建团队**并给出名称和描述
2. **生成队友**——每个队友都加入团队并共享任务列表
3. **分配任务**使用 TaskUpdate 给特定队友分配工作
4. **队友工作**——每轮结束后进入空闲状态（这是正常的）
5. **协调**——直接给队友发送消息以检查进度或解除阻塞
6. **关闭**——完成后优雅地终止队友

### 创建团队

直接让 Claude Code 操作：

> 创建一个名为 "my-project" 的团队来构建全栈功能

或者更具体：

> 生成两个队友——一个负责前端 React 工作，一个负责后端 API 工作。团队命名为 "web-app-team"

### 选择代理类型

生成队友时，将代理类型与工作匹配：

- **Explore** - 用于代码库探索、查找文件、理解架构（只读）
- **Plan** - 在编码前设计实施策略（只读）
- **General-purpose** - 用于实际编码任务（包括编辑/写入的完整功能）

示例：
> 生成一个名为 "frontend-dev" 的通用代理和另一个名为 "backend-dev" 的代理

### 任务管理

团队共享一个所有队友都可以访问的任务列表。生成队友后：

1. **创建任务**使用 TaskCreate 或让 Claude 分解工作
2. **分配任务**通过名称使用 TaskUpdate 给队友
3. **跟踪进度**——使用 TaskList 查看可用的内容

工作流示例：
> 为全栈功能创建任务。将前端任务分配给 "frontend-dev"，后端任务分配给 "backend-dev"

### 与队友通信

你可以随时给队友发送消息：

> 告诉 "frontend-dev" 使用新的 API 端点格式

队友在以下情况下也会给你发送消息：
- 完成任务
- 需要澄清
- 被某事阻塞
- 有问题

这种消息传递是自动的——你会看到他们的消息作为新的对话轮次。

### 重要注意事项

- **空闲是正常的**——队友在每轮后进入空闲状态。这并不意味着他们完成了，只是在等待输入
- **按名称引用**——在发送消息或分配任务时，始终使用队友的名称（而不是 ID）
- **耐心**——给队友时间来完成工作，然后再检查
- **优雅关闭**——完成后使用类型为 "shutdown_request" 的 SendMessage

### 清理工作

工作完成后：

> 关闭 "web-app-team" 上的所有队友

这会删除团队和任务目录。你也可以在所有队友关闭后直接用 TeamDelete 删除团队。

团队是并行化复杂工作的强大方式——就像有多个工程师在项目的不同部分一起工作。
