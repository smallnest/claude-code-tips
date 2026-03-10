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
- [技巧 19：初始化 CLAUDE.md](#技巧-19初始化-claudemd)
- [技巧 20：团队共享与持续迭代](#技巧-20团队共享与持续迭代)
- [技巧 21：代码审查时自动更新规则](#技巧-21代码审查时自动更新规则)
- [技巧 22：使用权限预授权](#技巧-22使用权限预授权)
- [技巧 23：自动格式化钩子](#技巧-23自动格式化钩子)
- [技巧 24：快速设置脚本](#技巧-24快速设置脚本)
- [技巧 25：使用无头模式](#技巧-25使用无头模式)
- [技巧 26：组建 Agent 团队](#技巧-26组建-agent-团队)
- [技巧 27：使用 Task 系统管理任务](#技巧-27使用-task-系统管理任务)
- [技巧 28：避免常见反模式](#技巧-28避免常见反模式)
- [技巧 29：使用 /loop 定时执行任务](#技巧-29使用-loop-定时执行任务)
- [技巧 30：使用 Code Simplifier 简化代码](#技巧-30使用-code-simplifier-简化代码)

## 技巧 1：自定义状态栏

自定义底部状态栏，显示模型名称、当前目录、Git 分支、Token 使用量等关键信息：

```
Opus 4.5 | 📁claude-code-tips | 🔀main | ██░░░░░░░░ 18% of 200k tokens
```

设置方法：使用[示例脚本](scripts/context-bar.sh)，参考[设置说明](scripts/README.md)。支持 10 种颜色主题。

## 技巧 2：常用斜杠命令

输入 `/` 查看全部命令。

- `/usage` - 查看速率限制使用情况
- `/chrome` - 启用/禁用 Chrome 浏览器集成
- `/mcp` - 管理 MCP 服务器
- `/permissions` - 预授权安全命令，减少确认
- `/clear` - 清除对话历史

## 技巧 3：使用 Voice 模式

Claude 网页版支持完全通过语音交互。

**启用方式**：点击输入框旁的麦克风图标。

**两种模式**：
- **Hands-free**（默认）：持续监听，适合安静环境
- **Push-to-talk**：按住说话，适合嘈杂环境

详情：[官方 Voice 模式文档](https://support.claude.com/en/articles/11101966-using-voice-mode)

## 技巧 4：分解复杂问题

这是最重要的工作方式。当 Claude 无法一次性解决困难问题时，请它分解为子问题，继续分解直到所有子问题都可解决。

## 技巧 5：从终端获取输出

高效获取内容的方法：
- `/copy` - 将 Claude 最后响应复制到剪贴板
- `pbcopy` - Mac/Linux 上直接发送到剪贴板
- 写入文件 - 保存到文件并在 VS Code 中打开
- 打开 URL - 在浏览器中打开

## 技巧 6：上下文管理与计划模式

**压缩上下文**：使用 `/compact` 总结对话，释放空间。最佳实践是在重新开始前创建交接文档。

**计划模式**：大多数会话应从计划模式开始（按两次 Shift+Tab）。先用计划模式讨论，满意后切换到自动接受模式执行。

## 技巧 7：复制页面内容

当 Claude 无法访问某个 URL 时，全选页面内容（Cmd+A / Ctrl+A），复制后粘贴到 Claude Code。

## 技巧 8：使用 Gemini CLI 访问受限网站

当 WebFetch 无法访问某些网站时，创建技能使用 Gemini CLI 作为后备方案。详见 [skills/reddit-fetch/SKILL.md](skills/reddit-fetch/SKILL.md)。

## 技巧 9：使用 Git Worktree 并行开发

同时处理同一项目的多个任务时，让 Claude 创建 git worktree，实现不同目录处理不同分支。

## 技巧 10：长时间任务处理策略

- **手动指数退避**：以递增间隔检查状态（1 分钟、2 分钟、4 分钟...）
- **后台代理验证**：完成后使用后台代理验证结果
- **Stop 钩子验证**：使用 Agent Stop 钩子验证
- **Ralph Wiggum 插件**：自动循环直到完成

## 技巧 11：恢复对话与倒带

**恢复对话**：
```bash
claude --continue    # 继续最近的对话
claude --resume      # 从列表中选择
```

**倒带**：双击 `Escape` 或 `/rewind` 打开菜单，可恢复对话、代码或两者。

**纠正方向**：`Esc` 停止执行，`Esc+Esc` 倒带。同一问题纠正两次以上后，用 `/clear` 重新开始。

## 技巧 12：理解扩展机制

- **CLAUDE.md** - 默认提示词，每个对话开始时加载
- **Skills** - 结构化的 CLAUDE.md，可自动或手动调用
- **斜杠命令** - 打包指令，放在 `.claude/commands/`
- **插件** - 打包技能、命令、代理、钩子和 MCP 服务器

## 技巧 13：将 Claude Code 作为通用 Agent

让 Claude 使用各种工具：通过 MCP 发送 Slack 消息、运行 BigQuery 查询、获取 Sentry 日志、调查 CI 失败。

可打包为 `/gha` 命令，自动调查 GitHub Actions 失败。

## 技巧 14：后台运行命令与子代理

**后台运行**：按 Ctrl+B 将长时间命令移到后台。

**子代理**：用于流程自动化（如 code-simplifier、verify-app），而非"专家分工"。可自定义数量、前后台、模型。

## 技巧 15：输入框导航与编辑

**导航**：`Ctrl+A/E` 行首/尾，`Option+←/→` 按词跳转

**编辑**：`Ctrl+W` 删除前词，`Ctrl+U/K` 删除到行首/尾，`Ctrl+C/L` 清除输入

**换行**：输入 `\` 后按 Enter

**粘贴图片**：`Ctrl+V`（Mac/Linux）或 `Alt+V`（Windows）

**权限模式**：`Shift+Tab` 切换 Normal / Auto-Accept / Plan 模式

## 技巧 16：使用远程控制

将 claude.ai/code 连接到本地 Claude Code 会话，从手机或其他设备继续。

```bash
claude remote-control    # 启动会话
/rc                       # 从现有会话继续
```

要求 Max 计划，详情见[官方文档](https://code.claude.com/docs/zh-CN/remote-control)。

## 技巧 17：有效沟通

**理解代码库**：提问快速理解，如"日志系统如何工作？"

**让 Claude 面试你**：使用 AskUserQuestion 工具明确需求：
```
我想构建[描述]。使用 AskUserQuestion 工具面试我，明确技术实现和边界情况。
```

## 技巧 18：使用 Subagents

Subagents 在独立上下文中运行，不污染主对话。

**用途**：
- 调查代码库（不消耗主上下文）
- 验证实现
- 并行分析不同部分

**自定义**：在 `.claude/agents/` 创建配置文件。

## 技巧 19：初始化 CLAUDE.md

CLAUDE.md 在每个对话开始时加载，提供持久上下文。

**快速初始化**：`/init` 自动检测构建系统、测试框架等。

**保持简洁**：只包含 Claude 无法猜测的内容。臃肿的文件会被忽略。

**文件位置**：`~/.claude/CLAUDE.md`（全局）或 `./CLAUDE.md`（项目）

**导入文件**：使用 `@path/to/import` 语法。

## 技巧 20：团队共享与持续迭代

将 CLAUDE.md 提交到 git 团队共享。关键机制：每当 Claude 做错什么，就加到 CLAUDE.md，形成飞轮。

定期审查和修剪，保持内容新鲜。

## 技巧 21：代码审查时自动更新规则

在 PR 上 `@.claude` 让 Claude 把规则加到 CLAUDE.md。

设置：`/install-github-action`

## 技巧 22：使用权限预授权

不要用 `--dangerously-skip-permissions`。

使用 `/permissions` 预授权安全命令，设置保存到 `.claude/settings.json`：

```json
{
  "permissions": {
    "allow": ["Bash(*)"],
    "deny": ["Bash(rm -rf *)"]
  }
}
```

## 技巧 23：自动格式化钩子

使用 PostToolUse 钩子格式化代码，处理最后的 10%：

```json
{
  "hooks": {
    "PostToolUse": [{ "hooks": [{ "type": "command", "command": "npm run format" }] }]
  }
}
```

思路：在关键检查点验证，而非限制每一步。

## 技巧 24：快速设置脚本

一次性设置多个推荐项：

```bash
bash <(curl -s https://raw.githubusercontent.com/ykdojo/claude-code-tips/main/scripts/setup.sh)
```

## 技巧 25：使用无头模式

直接从命令行传递提示词，适合一次性任务：

```bash
claude -p "分析认证系统并建议改进"
npm test 2>&1 | claude -p "分析测试失败原因"
```

**常用选项**：`-c` 继续，`-r` 恢复，`--model opus` 指定模型

## 技巧 26：组建 Agent 团队

生成多个专业代理协同处理复杂任务，每个有独立上下文。

**何时使用**：全栈功能、大型重构、多阶段项目

**代理类型**：Explore（只读探索）、Plan（规划）、General-purpose（完整功能）

## 技巧 27：使用 Task 系统管理任务

Tasks 将复杂项目分解为持久化清单，存储在 `~/.claude/tasks`，上下文压缩后仍存活。

**跨会话共享**：设置 `CLAUDE_CODE_TASK_LIST_ID` 环境变量

**查看进度**：按 `Ctrl+T`

## 技巧 28：避免常见反模式

- **厨房水槽会话**：上下文充满无关信息 → 不相关任务间用 `/clear`
- **重复纠正**：上下文被失败方法污染 → 两次失败后 `/clear` 重来
- **过度指定的 CLAUDE.md**：Claude 忽略一半内容 → 无情修剪
- **信任与验证的差距**：不处理边界情况 → 始终提供验证
- **无限探索**：读取数百文件填满上下文 → 限定范围或用 subagents

## 技巧 29：使用 /loop 定时执行任务

按间隔重复执行提示，用于轮询部署、监控 PR、检查构建任务。

**基本用法**：
```
/loop 5m 检查部署是否完成
/loop 20m /review-pr 1234
下午 3 点提醒我推送分支    # 一次性提醒
```

**时间单位**：`s` 秒、`m` 分、`h` 时、`d` 天（默认 10 分钟）

**管理**：自然语言列出或取消任务

**特性**：会话作用域、低优先级、3 天自动过期、最多 50 个任务

详情：[官方定时任务文档](https://code.claude.com/docs/en/scheduled-tasks)

## 技巧 30：使用 Code Simplifier 简化代码

专门子代理，在不改变功能的情况下清理、重构和简化代码。

**安装**：
```bash
claude plugin marketplace update claude-plugins-official
claude plugin install code-simplifier
```

**使用**：`/simplify` 或让 Claude 完成任务后自动调用

**原则**：保持功能不变、应用项目标准、增强清晰度、避免过度简化

**适用场景**：编码会话后整理、提交 PR 前、AI 生成代码后

详情：[Code Simplifier 源码](https://github.com/anthropics/claude-code/blob/main/plugins/pr-review-toolkit/agents/code-simplifier.md)
