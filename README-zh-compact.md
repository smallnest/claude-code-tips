# Claude Code 实战技巧

这是一套 Claude Code 实用技巧集合：自定义状态栏、优化配置文档、访问受限网站、在容器中运行 Claude Code 等。包含 Claude Code 创建者 Boris Cherny 的独家实战经验。

## 目录

- [技巧 1：自定义状态栏](#技巧-1自定义状态栏)
- [技巧 2：常用斜杠命令](#技巧-2常用斜杠命令)
- [技巧 3：使用 Voice 模式](#技巧-3使用-voice-模式)
- [技巧 4：分解复杂问题](#技巧-4分解复杂问题)
- [技巧 5：从终端获取输出](#技巧-5从终端获取输出)
- [技巧 6：上下文管理与计划模式](#技巧-6上下文管理与计划模式)
- [技巧 7：复制页面内容](#技巧-7复制页面内容)
- [技巧 8：使用 Gemini CLI 访问受限网站](#技巧-8使用-gemini-cli-访问受限网站)
- [技巧 9：使用 Git Worktree 并行开发](#技巧-9使用-git-worktree-并行开发)
- [技巧 10：长时间任务处理策略](#技巧-10长时间任务处理策略)
- [技巧 11：恢复对话与倒带](#技巧-11恢复对话与倒带)
- [技巧 12：理解扩展机制](#技巧-12理解扩展机制)
- [技巧 13：将 Claude Code 作为通用 Agent](#技巧-13将-claude-code-作为通用-agent)
- [技巧 14：后台运行命令与子代理](#技巧-14后台运行命令与子代理)
- [技巧 15：输入框导航与编辑](#技巧-15输入框导航与编辑)
- [技巧 16：使用远程控制](#技巧-16使用远程控制)
- [技巧 17：有效沟通](#技巧-17有效沟通)
- [技巧 18：使用 Subagents](#技巧-18使用-subagents)
- [技巧 19：全程使用 Opus 4.5](#技巧-19全程使用-opus-45)
- [技巧 20：初始化 CLAUDE.md](#技巧-20初始化-claudemd)
- [技巧 21：团队共享与持续迭代](#技巧-21团队共享与持续迭代)
- [技巧 22：代码审查时自动更新规则](#技巧-22代码审查时自动更新规则)
- [技巧 23：使用权限预授权](#技巧-23使用权限预授权)
- [技巧 24：自动格式化钩子](#技巧-24自动格式化钩子)
- [技巧 25：快速设置脚本](#技巧-25快速设置脚本)
- [技巧 26：使用无头模式](#技巧-26使用无头模式)
- [技巧 27：组建 Agent 团队](#技巧-27组建-agent-团队)
- [技巧 28：使用 Task 系统管理任务](#技巧-28使用-task-系统管理任务)
- [技巧 29：避免常见反模式](#技巧-29避免常见反模式)

## 技巧 1：自定义状态栏

Claude Code 允许自定义底部状态栏，显示关键信息。以下配置显示模型名称、当前目录、Git 分支、未提交文件、远程同步状态以及 Token 使用量进度条：

```
Opus 4.5 | 📁claude-code-tips | 🔀main (scripts/context-bar.sh uncommitted, synced 12m ago) | ██░░░░░░░░ 18% of 200k tokens
💬 This is good. I don't think we need to change the documentation as long as we don't say that the default color is orange el...
```

这有助于监控上下文使用情况并跟踪当前工作。脚本支持 10 种颜色主题。

![颜色预览选项](scripts/color-preview.png)

设置方法：使用[示例脚本](scripts/context-bar.sh)，参考[设置说明](scripts/README.md)。

## 技巧 2：常用斜杠命令

Claude Code 提供丰富的内置斜杠命令（输入 `/` 查看全部）。

### /usage

查看速率限制使用情况：

```
 Current session
 █████████▌                                         19% used
 Resets 12:59am (America/Vancouver)

 Current week (all models)
 █████████████████████▌                             43% used
 Resets Feb 3 at 1:59pm (America/Vancouver)
```

### /chrome

启用或禁用 Chrome 浏览器集成：

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
```

### /permissions

预授权已知的安全命令，减少重复确认：

```
> /permissions
```

### /clear

清除对话历史，重新开始。

## 技巧 3：使用 Voice 模式

Claude 网页版（包括 claude.ai/code）提供内置 Voice 模式，支持完全通过语音与 Claude 交互。

### 启用方式

**网页端**：点击输入框旁的麦克风图标

**移动端（iOS/Android）**：点击麦克风图标

### 对话模式

**Hands-free 模式**（默认）：Claude 持续监听，自动识别说话结束后回复。适合安静环境。Claude 可处理自然停顿，按你的节奏说话。如果被打断，直接继续说话即可。

**Push-to-talk 模式**：在嘈杂环境或声音识别困难时使用。按住按钮说话，松开后发送。这提供了更多控制权，适合繁忙街道、拥挤房间等环境。

### 功能特点

- 文本与语音无缝切换，上下文完整保留
- 多种声音可选，首次使用时选择
- 语音对话文本记录保存于聊天历史
- 目前支持英语

详情：[官方 Voice 模式文档](https://support.claude.com/en/articles/11101966-using-voice-mode)

## 技巧 4：分解复杂问题

这是最重要的工作方式。当 Claude Code 无法一次性解决困难问题时，请它分解为多个子问题。查看能否解决部分内容。仍然困难？继续分解为更小的子问题，直到所有子问题都可解决。

## 技巧 5：从终端获取输出

直接从终端复制输出可能不便。以下是更高效的获取内容方法：

- **`/copy` 命令**：输入 `/copy` 将 Claude 的最后一条响应以 Markdown 格式复制到剪贴板
- **直接使用剪贴板**：在 Mac 或 Linux 上，让 Claude 使用 `pbcopy` 直接发送输出到剪贴板
- **写入文件**：让 Claude 将内容保存到文件，并在 VS Code 中打开
- **打开 URL**：让 Claude 在浏览器中打开需要查看的 URL
- **GitHub Desktop**：让 Claude 在 GitHub Desktop 中打开当前仓库

## 技巧 6：上下文管理与计划模式

### 主动压缩上下文

Claude Code 提供 `/compact` 命令总结对话，释放上下文空间。最佳实践是在重新开始前让 Claude 创建交接文档：

> 将剩余计划保存到 system-prompt-extraction 文件夹，命名为 HANDOFF.md。说明尝试过的方法、有效与无效的内容，以便拥有全新上下文的代理只需加载该文件即可完成此任务。

你也可以创建 `/handoff` 斜杠命令自动化此过程，示例见 [skills/handoff/SKILL.md](skills/handoff/SKILL.md)。

### 从计划模式开始（推荐）

Claude Code 创建者 Boris Cherny 建议：大多数会话应从计划模式开始（按两次 Shift+Tab）。

工作流程：先用计划模式讨论直到计划满意，然后切换到自动接受编辑模式，Claude 通常可一次性完成。

**良好的计划至关重要！** 直接让 Claude 开始工作，往往进行到一半发现方向错误。

### 替代方案：使用 `/plan`

另一个选择是使用 `/plan` 或 Shift+Tab 进入计划模式。让 Claude 收集所有相关上下文并为下一个代理创建全面计划：

> 我刚启用了计划模式。将所需的所有上下文带给下一个代理。下一个代理不会有其他上下文，因此你需要尽可能全面。

## 技巧 7：复制页面内容

当 Claude Code 无法直接访问某个 URL 时，你可以选择页面上的所有内容（Mac 用 Cmd+A，其他平台用 Ctrl+A），复制后直接粘贴到 Claude Code 中。这个方法非常有效。

## 技巧 8：使用 Gemini CLI 访问受限网站

Claude Code 的 WebFetch 工具无法访问某些网站（如 Reddit）。你可以通过创建技能来解决这个问题，让 Claude 使用 Gemini CLI 作为后备方案。

这使用了与技巧 10 相同的 tmux 模式——启动会话、发送命令、捕获输出。完整内容见 [skills/reddit-fetch/SKILL.md](skills/reddit-fetch/SKILL.md)。

## 技巧 9：使用 Git Worktree 并行开发

当需要同时处理同一项目的多个任务而避免冲突时，Git worktree 是理想选择。让 Claude Code 创建 git worktree 并在其中工作。

基本思路是：不同目录处理不同分支，实现一个分支对应一个工作目录的结构。

## 技巧 10：长时间任务处理策略

对于长时间运行的任务，有几种处理策略：

### 手动指数退避

在等待长时间运行的任务（如 Docker 构建或 GitHub CI）时，让 Claude Code 执行手动指数退避。让 Claude Code 以递增的间隔检查状态——1 分钟、2 分钟、4 分钟，以此类推。

这样代理可以持续检查状态，并在完成后通知你。

### 后台代理验证

提示 Claude 在完成后使用后台代理验证结果。

### Stop 钩子验证

使用 Agent Stop 钩子进行验证。

### Ralph Wiggum 插件

使用 ralph-wiggum 插件让 Claude 自动循环直到完成。这个名称来自《辛普森一家》角色，核心是让 Claude 在完成后自动继续，直到真正达到目标。

插件地址：`https://github.com/anthropics/claude-plugins-official/tree/main/plugins/ralph-wiggum`

## 技巧 11：恢复对话与倒带

对话是持久的和可逆的。充分利用这些功能可以显著提升效率。

### 恢复对话

Claude Code 在本地保存对话。当任务跨越多个会话时，无需重新解释上下文：

```bash
claude --continue    # 继续最近的对话
claude --resume      # 从最近对话列表中选择
```

使用 `/rename` 为会话设置描述性名称（如 `"oauth-migration"` 或 `"debugging-memory-leak"`），便于后续查找。将会话视为分支：不同工作流可以拥有独立的持久上下文。

### 使用检查点倒带

Claude 在更改前自动创建检查点。双击 `Escape` 或运行 `/rewind` 打开倒带菜单。你可以：
- 仅恢复对话
- 仅恢复代码
- 同时恢复两者
- 从选定消息总结

与其仔细规划每一步，不如让 Claude 尝试一些风险操作。如果不起作用，倒带并尝试不同方法。检查点在会话期间持久存在，即使关闭终端后仍然可以倒带。

### 尽早且频繁纠正方向

最佳结果来自紧密的反馈循环：

- **`Esc`**：在 Claude 执行中途停止，保留上下文以便重定向
- **`Esc + Esc` 或 `/rewind`**：打开倒带菜单，恢复之前的对话和代码状态
- **`"撤销那个"`**：让 Claude 恢复其更改
- **`/clear`**：在不相关任务之间重置上下文

如果在同一会话中对同一问题纠正 Claude 两次以上，上下文将被失败的方法污染。此时应运行 `/clear` 并使用更具体的提示重新开始，包含你学到的内容。具有更好提示的干净会话几乎总是优于累积更正的长会话。

## 技巧 12：理解扩展机制

了解各种扩展方式的区别有助于正确使用：

**CLAUDE.md** 是最简单的扩展方式。它被视为默认提示词，在每个对话开始时加载。

**Skills** 是结构化的 CLAUDE.md 文件。可以在相关时由 Claude 自动调用，或通过斜杠命令手动调用。

**斜杠命令** 与技能类似，都是将指令打包。可以由用户手动调用，或由 Claude 自己调用。

**插件** 是将技能、斜杠命令、代理、钩子和 MCP 服务器打包在一起的分发方式。

### 斜杠命令用于高频工作流

对于每天重复执行的"内循环"工作流，使用斜杠命令，放在 `.claude/commands/` 目录下。

关键是：这不仅节省输入，还能让 Claude 自己调用这些命令。例如，Claude 写代码时可以调用你定义的 `/review` 进行自我检查。

## 技巧 13：将 Claude Code 作为通用 Agent

Claude Code 不仅是"写代码的工具"，更是通用 Agent。

让 Claude Code 使用各种工具：
- 通过 MCP 服务器搜索并发送 Slack 消息
- 运行 BigQuery 查询回答分析问题
- 从 Sentry 获取错误日志
- 调查 GitHub Actions CI 失败

每当 GitHub Actions CI 失败时，交给 Claude Code，说「深入调查此问题，尝试找到根本原因。」

可以将此工作流打包为 `/gha` 斜杠命令——只需运行 `/gha <url>` 并提供任何 GitHub Actions URL，它会自动调查失败、检查不稳定性、识别破坏性提交并建议修复。

## 技巧 14：后台运行命令与子代理

当有长时间运行的 bash 命令时，按 Ctrl+B 将其移到后台运行。Claude Code 可以管理后台进程，稍后使用 BashOutput 工具检查它们。

### 策略性使用子代理

使用几个子代理自动化常见流程：
- **code-simplifier**：Claude 完成工作后简化代码
- **verify-app**：端到端测试的详细指令

将子代理视为自动化大多数 PR 所需的工作流。

**重要提示**：不要创建一堆"专家子代理"（Python 专家、前端专家），这会分割上下文，使主 Claude 无法进行整体推理。用子代理进行"流程自动化"是正确的，但不要用于"专家分工"。

当需要分解大任务时，子代理也很有用。例如，需要分析庞大的代码库时，可以让子代理以不同方式分析或并行查看代码库的不同部分。

可以通过直接请求自定义子代理：
- **数量**——让 Claude 启动所需数量
- **后台或前台**——要求后台运行，或按 Ctrl+B
- **模型**——根据每个任务的复杂度要求 Opus、Sonnet 或 Haiku

## 技巧 15：输入框导航与编辑

Claude Code 输入框设计为模拟常见的终端/readline 快捷键：

**导航：**
- `Ctrl+A` - 跳转到行首
- `Ctrl+E` - 跳转到行尾
- `Option+Left/Right`（Mac）或 `Alt+Left/Right` - 按词向前/向后跳转

**编辑：**
- `Ctrl+W` - 删除前一个词
- `Ctrl+U` - 从光标删除到行首
- `Ctrl+K` - 从光标删除到行尾
- `Ctrl+C` / `Ctrl+L` - 清除当前输入
- `Ctrl+G` - 在外部编辑器中打开提示词

**输入换行（多行输入）：**

最快捷的方法无需任何设置，在任何地方都有效：输入 `\` 然后按 Enter 创建新行。

**粘贴图片：**
- `Ctrl+V`（Mac/Linux）或 `Alt+V`（Windows）- 从剪贴板粘贴图片

**切换权限模式：**
- `Shift+Tab` 或 `Alt+M`（某些配置）- 在自动接受模式、计划模式和普通模式之间切换

### 三种权限模式

**Normal Mode（普通模式）** - 默认模式
- 每个 Bash、Write、Edit 等工具调用都需要手动批准
- 适用场景：不熟悉代码库、需要仔细审查输出
- 优点：最大安全性，完全控制每一步
- 缺点：需要频繁批准，影响速度

**Auto-Accept Mode（自动接受模式）**
- Claude 自动批准所有工具调用，无需手动确认
- 适用场景：熟悉代码库、信任 Claude 输出
- 优点：速度快，让 Claude 独立工作
- 缺点：风险较高，可能做出意外更改

**Plan Mode（计划模式）** - 推荐用于复杂任务
- Claude 先制定详细计划，不执行任何编辑操作
- 计划批准后，Claude 一次性执行所有更改
- 适用场景：复杂重构、新功能开发等需要仔细规划的任务
- 优点：可在执行前查看完整计划，避免方向错误
- 缺点：需要额外时间规划和审查计划

### 推荐工作流

1. **简单任务**（小改动、Bug 修复）→ Normal Mode
2. **熟悉项目的快速迭代** → Auto-Accept Mode
3. **复杂任务**（重构、新功能）→ 先用 Plan Mode，然后切换到 Auto-Accept 执行

## 技巧 16：使用远程控制

Remote Control 将 claude.ai/code 或 Claude 应用连接到你机器上运行的 Claude Code 会话。你可以在办公桌上启动任务，然后从沙发上的手机或另一台计算机继续。

### 如何使用

**启动远程控制会话：**

```bash
claude remote-control
```

该进程在终端中保持运行，显示会话 URL。按空格键显示 QR 码，用手机扫描快速连接。

**从现有会话继续：**

如果你已经在 Claude Code 会话中，使用 `/remote-control` 或 `/rc` 命令：

```
/remote-control
```

这将继承你当前的对话历史。

### 连接方式

- **打开会话 URL**：直接在浏览器中打开显示的 URL
- **扫描 QR 码**：用 Claude 应用扫描
- **在会话列表中查找**：Remote Control 会话显示计算机图标

### 主要优势

- **使用完整本地环境**：文件系统、MCP servers、工具和项目配置保持可用
- **多设备同步**：对话在所有连接的设备上保持同步
- **应对中断**：笔记本睡眠或网络断开后自动重新连接

### 重要区别

| Remote Control | Claude Code on the web |
|----------------|------------------------|
| 在你的机器上运行 | 在云端基础设施运行 |
| 保留本地 MCP servers 和配置 | 无需本地设置 |
| 适合继续本地工作 | 适合新任务或未克隆的仓库 |
| 一次一个会话 | 可并行运行多个任务 |

### 要求

- **订阅**：需要 Max 计划（Pro 计划即将推出）
- **登录**：使用 `/login` 通过 claude.ai 登录
- **工作区信任**：在项目目录至少运行一次 `claude`

### 自动启用 Remote Control

默认需要手动启动。要为每个会话自动启用，运行 `/config` 并将"为所有会话启用 Remote Control"设置为 `true`。

### 限制

- 一次一个远程会话
- 终端必须保持打开
- 网络中断超过 10 分钟会超时

详情：[官方 Remote Control 文档](https://code.claude.com/docs/zh-CN/remote-control)

## 技巧 17：有效沟通

与 Claude Code 的有效沟通可以显著提升工作效率。

### 提问来理解代码库

加入新代码库时，通过提问快速理解：
- "日志系统是如何工作的？"
- "如何创建新的 API 端点？"
- "认证流程是怎样的？"

### 让 Claude 面试你

使用 AskUserQuestion 工具让 Claude 询问关键细节，这对于技术实现、UI/UX 设计、边界情况和权衡决策特别有效。

**面试提示词示例：**

```
我想构建[简短描述]。使用 AskUserQuestion 工具详细面试我，帮我弄清楚技术实现方案、UI/UX 设计要求、边界情况和可能的权衡。
```

这种方式可以帮助你明确需求，让 Claude 生成更符合你期望的解决方案。

## 技巧 18：使用 Subagents

Subagents 在独立的上下文窗口中运行并报告摘要，是上下文管理的强大工具之一。

### 使用 Subagents 调查

当 Claude 研究代码库时，它会读取许多文件，消耗大量上下文。Subagents 可以在不污染主对话的情况下完成这项工作：

```
Use subagents to investigate how our authentication system handles token
refresh, and whether we have any existing OAuth utilities I should reuse.
```

Subagent 探索代码库、读取相关文件并报告发现，不会让主对话变得混乱。

### 使用 Subagents 验证

你也可以在 Claude 实现某些内容后使用 Subagents 进行验证：

```
use a subagent to review this code for edge cases
```

### 创建自定义 Subagents

你可以在 `.claude/agents/` 目录下创建配置文件来定义自定义 Subagents：

```markdown
---
name: security-reviewer
description: Reviews code for security vulnerabilities
tools: Read, Grep, Glob, Bash
model: opus
---
You are a senior security engineer. Review code for:
- Injection vulnerabilities (SQL, XSS, command injection)
- Authentication and authorization flaws
- Secrets or credentials in code
- Insecure data handling

Provide specific line references and suggested fixes.
```

然后明确告诉 Claude 使用它：`"使用 subagent 审查此代码以查找安全问题。"`

## 技巧 19：全程使用 Opus 4.5

Claude Code 创建者 Boris Cherny 建议：所有工作都使用 Opus 4.5。

虽然 Opus 比 Sonnet 更大更慢，但由于需要更少的引导，工具使用能力更强，最终几乎总是比使用小模型更快。

除了速度较慢和成本较高外，Opus 4.5 没有明显的缺点。

## 技巧 20：初始化 CLAUDE.md

CLAUDE.md 是 Claude 在每次对话开始时读取的特殊文件，包含 Bash 命令、代码风格和工作流规则，提供持久上下文。

### 使用 /init 快速初始化

`/init` 命令会分析你的代码库，检测构建系统、测试框架和代码模式，为你提供坚实的基础：

```
/init
```

### 编写有效的 CLAUDE.md

保持文件简洁易读：

```markdown
# Code style
- Use ES modules (import/export) syntax, not CommonJS (require)
- Destructure imports when possible (eg. import { foo } from 'bar')

# Workflow
- Be sure to typecheck when you're done making a series of code changes
- Prefer running single tests, and not the whole test suite, for performance
```

### 保持简洁

CLAUDE.md 在每个会话中加载，应只包括广泛适用的内容。对于每一行，问自己：**"删除这一行会导致 Claude 犯错吗？"** 如果不会，删除它。臃肿的 CLAUDE.md 会导致 Claude 忽略你的实际指令！

### 包含和排除的内容

✅ **包括：**
- Claude 无法猜测的 Bash 命令
- 与默认值不同的代码风格规则
- 测试指令和首选测试运行器
- 存储库约定（分支命名、PR 约定）
- 特定于你项目的架构决策
- 常见陷阱或非显而易见的行为

❌ **排除：**
- Claude 可以通过读取代码找出的任何内容
- Claude 已经知道的标准语言约定
- 详细的 API 文档（改为链接到文档）
- 经常变化的信息
- 开发者环境要求（必需的环境变量）
- 自明的实践，如"编写干净代码"
- 文件逐个描述代码库

### 文件位置

CLAUDE.md 文件可以放在多个位置：

- **主目录（`~/.claude/CLAUDE.md`）**：适用于所有 Claude 会话
- **项目根目录（`./CLAUDE.md`）**：检入 git 与团队共享，或命名为 `CLAUDE.local.md` 并 `.gitignore`
- **父目录**：对于 monorepos 有用，如 `root/CLAUDE.md` 和 `root/foo/CLAUDE.md` 都会自动加载
- **子目录**：处理这些目录中的文件时，Claude 按需加载子 CLAUDE.md 文件

### 导入其他文件

CLAUDE.md 可以使用 `@path/to/import` 语法导入其他文件：

```markdown
See @README.md for project overview and @package.json for available npm commands.

# Additional Instructions
- Git workflow: @docs/git-instructions.md
- Personal overrides: @~/.claude/my-project-instructions.md
```

### 持续迭代

像对待代码一样对待 CLAUDE.md：当事情出错时审查它，定期修剪它，并通过观察 Claude 的行为是否真正改变来测试更改。如果 Claude 继续做你不想要的事情，文件可能太长或规则措辞不明确。

## 技巧 21：团队共享与持续迭代

### 团队共享 CLAUDE.md

团队可以共享同一个 CLAUDE.md 文件，提交到 git，整个团队每周都会贡献多次。

**关键机制：每当看到 Claude 做错了什么，就加到 CLAUDE.md 里，这样 Claude 下次就知道不要这样做了。**

这形成了一个飞轮：Claude 犯错 → 记录 → Claude 学习 → 犯更少的错。

### 持续迭代 CLAUDE.md

CLAUDE.md 不是一次性文档，你应该持续更新它，使 Claude 的运行规则更符合你的要求。

定期审查 CLAUDE.md 文件，因为它们可能随时间过时。一段时间前有意义的指令可能不再相关，或者出现了应该记录的新模式。

## 技巧 22：代码审查时自动更新规则

在代码审查时，可以在同事的 PR 上 `@.claude`，让它把某条规则加到 CLAUDE.md 中。

这可以通过 Claude Code 的 GitHub Action 来实现。

设置：`/install-github-action`

这样可以在代码审查时发现 Claude 犯错，直接自动更新到团队的 CLAUDE.md 中。

## 技巧 23：使用权限预授权

不要使用 `--dangerously-skip-permissions`。

使用 `/permissions` 预先允许已知安全的 Bash 命令，大部分设置提交到 `.claude/settings.json` 并与团队共享。

这样可以在保持安全的同时减少不必要的确认。

设置示例：
```json
{
  "permissions": {
    "allow": ["Bash(*)"],
    "deny": ["Bash(rm -rf *)"]
  }
}
```

## 技巧 24：自动格式化钩子

使用 PostToolUse 钩子格式化 Claude 的代码。Claude 通常开箱就能生成格式良好的代码，钩子处理最后的 10%，避免后续 CI 中的格式错误。

这个思路可以推广：用钩子在关键检查点进行验证，而不是限制每一步操作。

设置示例：
```json
{
  "hooks": {
    "PostToolUse": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "npm run format"
          }
        ]
      }
    ]
  }
}
```

## 技巧 25：快速设置脚本

如果想一次性设置此仓库中的多个推荐项，可以使用设置脚本：

```bash
bash <(curl -s https://raw.githubusercontent.com/ykdojo/claude-code-tips/main/scripts/setup.sh)
```

脚本会显示将要配置的所有内容，让你可以跳过任何项目。

## 技巧 26：使用无头模式

无头模式（`-p` 参数）让你直接从命令行传递提示词，无需进入交互式会话。非常适合一次性任务。

```bash
claude -p "Analyze the authentication system and suggest improvements"
```

### 常用场景

**代码分析：**
```bash
claude -p "Review the auth.js file for security issues"
```

**生成文档：**
```bash
claude -p "Generate API documentation for the user module"
```

**测试后分析：**
```bash
npm test 2>&1 | claude -p "Analyze these test failures and suggest fixes"
```

**结合管道：**
```bash
cat error.log | claude -p "Summarize the errors and identify the root cause"
```

### 常用选项

- `-c` / `--continue` - 继续上一次对话
- `-r` / `--resume` - 显示最近对话列表以恢复
- `--dangerously-skip-permissions` - 跳过所有权限确认（谨慎使用）
- `--model opus` - 指定模型

### 组合使用

```bash
# 在特定项目中使用 Opus 模型分析
cd ~/my-project && claude -p "Review the codebase for performance issues" --model opus

# 跳过权限执行脚本（谨慎）
claude -p "Run tests and generate coverage report" --dangerously-skip-permissions
```

### 何时使用

**使用无头模式：**
- 一次性分析任务
- 生成文档或总结
- 自动化脚本中调用
- 不需要对话往复的场景

**使用交互模式：**
- 复杂的多步骤任务
- 需要反复调整的情况
- 需要 Claude 反复询问的场景

## 技巧 27：组建 Agent 团队

Claude Code 提供内置的团队功能，可以生成多个专业代理（队友）协同处理复杂任务。每个队友都有独立的对话上下文，可以给你或其他队友发送消息。

### 何时使用团队

在处理复杂、多步骤任务并受益于并行工作时使用团队：
- **全栈功能** - 前端工作 + 后端工作同时进行
- **大型重构** - 在跨多个文件进行更改时保持测试通过
- **多阶段项目** - 研究 → 规划 → 实施

### 工作原理

1. **创建团队**并给出名称和描述
2. **生成队友**——每个队友都加入团队并共享任务列表
3. **分配任务**使用 TaskUpdate 给特定队友分配工作
4. **队友工作**——每轮结束后进入空闲状态（这是正常的）
5. **协调**——直接给队友发送消息以检查进度或解除阻塞
6. **关闭**——完成后优雅地终止队友

### 选择代理类型

生成队友时，将代理类型与工作匹配：

- **Explore** - 用于代码库探索、查找文件、理解架构（只读）
- **Plan** - 在编码前设计实施策略（只读）
- **General-purpose** - 用于实际编码任务（包括编辑/写入的完整功能）

## 技巧 28：使用 Task 系统管理任务

Claude Code Tasks（原 To-dos）让 AI 通过将复杂项目分解为持久化的文件清单来管理，任务存储在 `~/.claude/tasks`，即使上下文被压缩也能存活。

### 如何使用

**自动跟踪**：对于复杂提示，Claude Code 会自动创建和跟踪分步清单。

**手动触发**：在提示中提到 "Todo" 或 "Tasks" 即可让 Claude 创建任务。

**协作**：任务存储在文件系统中，多个会话或子代理可以处理同一个任务列表。

**持久化**：与旧的待办列表不同，任务能在上下文压缩和长时间会话中存活。

**跨会话共享**：设置环境变量 `CLAUDE_CODE_TASK_LIST_ID` 来跨会话协作：

```bash
# 每次启动
CLAUDE_CODE_TASK_LIST_ID=project-name claude

# 或在 ~/.claude/settings.json 中设置
{
  "env": {
    "CLAUDE_CODE_TASK_LIST_ID": "my-project"
  }
}
```

### 主要优势

**克服上下文限制**：将大型项目分解为更小、可管理的单元。

**并行处理**：让子代理并行处理多个任务。

**实时可见**：可以看到任务被勾选完成的进度。

### 何时使用

- 复杂的多步骤项目
- 需要跨多个会话的工作
- 需要并行处理的任务

查看进度：按 `Ctrl+T` 切换任务视图，或问"任务状态如何？"

## 技巧 29：避免常见反模式

识别并避免这些常见的失败模式可以显著提升效率。

### 厨房水槽会话

你从一个任务开始，然后问 Claude 一些不相关的事情，然后回到第一个任务。上下文充满了无关的信息。

> **修复**：在不相关的任务之间使用 `/clear`。

### 重复纠正

Claude 做错了什么，你纠正它，它仍然是错的，你再纠正。上下文被失败的方法污染。

> **修复**：在两次失败的纠正后，`/clear` 并编写一个更好的初始提示，包含你学到的东西。

### 过度指定的 CLAUDE.md

如果你的 CLAUDE.md 太长，Claude 会忽略一半内容，因为重要的规则在噪音中丢失。

> **修复**：无情地修剪。如果 Claude 已经在没有指令的情况下正确做某事，删除它或将其转换为 hook。

### 信任与验证的差距

Claude 产生一个看起来合理的实现，但不处理边界情况。

> **修复**：始终提供验证（测试、脚本、屏幕截图）。如果你不能验证它，不要发布它。

### 无限探索

你要求 Claude "调查"某些东西而不限定范围。Claude 读取数百个文件，填满上下文。

> **修复**：狭隘地限定调查范围或使用 subagents，以便探索不会消耗你的主上下文。

---

**Task 系统原文推文**：https://x.com/nummanali/status/2014684862985175205

**Boris Cherny 原文推文**：https://x.com/bcherny/status/2007179832300581177

📺 **相关演讲**：[Claude Code 大师课](https://youtu.be/9UdZhTnMrTA) - 来自 31 个月代理编程的经验教训和项目示例

📝 **故事**：[我如何用 Claude Code 找到全职工作](content/how-i-got-a-job-with-claude-code.md)

📰 **通讯**：[有纪律和技巧的代理编程](https://agenticcoding.substack.com/) - 将代理编程实践提升到更高水平
