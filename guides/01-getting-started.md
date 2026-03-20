[English](./01-getting-started.en.md) | **中文**

# 01 - 入门篇：开始你的 AI 编程之旅

> 从零开始，选择工具、完成安装、写出你的第一段 AI 辅助代码。

## 什么是 AI 辅助编程

AI 辅助编程是指借助大语言模型（LLM）来帮助你完成编码任务——包括代码生成、调试、重构、写测试、写文档等。你不需要改变编程语言或框架，AI 作为你的"结对编程伙伴"融入现有工作流。

核心价值：

- 减少重复性编码工作，专注于架构和逻辑设计
- 快速探索不熟悉的 API 和框架
- 提升代码质量（AI 可以发现你忽略的 edge case）

## 选择哪个工具

```
你习惯在终端工作吗？
├── 是 → 你需要处理复杂的多文件任务吗？
│   ├── 是 → Claude Code
│   └── 否 → Codex CLI / Gemini CLI
└── 否 → 你想要完整的 IDE 体验吗？
    ├── 是 → Cursor
    └── 否 → GitHub Copilot（在现有 VS Code 中安装插件）
```

**新手建议**：如果你不确定选哪个，先从 GitHub Copilot 开始（门槛最低），熟悉 AI 编程的节奏后再尝试 Claude Code 或 Cursor。

## 安装指南

### Claude Code

```bash
# 需要 Node.js 18+
npm install -g @anthropic-ai/claude-code

# 进入项目目录后启动
cd your-project
claude
```

### Cursor

1. 前往 [cursor.com](https://cursor.com) 下载安装包
2. 安装后打开，它会自动导入你的 VS Code 配置
3. 使用 `Cmd+K`（Mac）或 `Ctrl+K`（Windows/Linux）开始 AI 对话

### GitHub Copilot

1. 在 VS Code 扩展市场搜索 "GitHub Copilot" 并安装
2. 登录 GitHub 账号并激活订阅
3. 开始输入代码，Copilot 会自动给出补全建议（按 Tab 接受）

## 你的第一次 AI 编程

以 Claude Code 为例，创建一个简单的 TODO API：

```bash
$ claude
> 帮我创建一个 Express.js 的 TODO RESTful API，包含：
  - GET /todos 获取所有待办
  - POST /todos 创建待办
  - PUT /todos/:id 更新待办
  - DELETE /todos/:id 删除待办
  使用内存存储，不需要数据库。包含基本的错误处理。
```

关键点：

- 你的第一个提示词不需要完美，AI 可以迭代
- 先让 AI 生成骨架代码，再逐步完善细节
- 生成后一定要**阅读并理解代码**，不要盲目接受

## 5 个常见新手错误

**1. 完全不审查 AI 生成的代码**

AI 会犯错。每一行生成的代码都需要你理解和审查。把 AI 当作初级开发者——它写得快，但需要你把关。

**2. 提示词过于模糊**

- 不好：`帮我写个网站`
- 好：`用 Next.js 14 创建一个博客首页，展示文章列表，每篇文章显示标题、摘要和发布日期`

**3. 一次给 AI 太大的任务**

把大任务拆分成小步骤。不要指望一句话就让 AI 生成整个项目，分模块逐步推进效果更好。

**4. 忽略上下文管理**

AI 的对话窗口有上下文限制。当对话变长时，早期的信息可能被"遗忘"。适时开启新会话，并在新会话中提供必要的背景信息。

**5. 不利用项目配置文件**

为项目创建 `CLAUDE.md` 或 `.cursorrules`，告诉 AI 你的项目结构、技术栈和编码规范，能大幅提升生成质量。详见[项目配置篇](./04-project-setup.md)。

---

下一篇：[提示词篇 - 如何与 AI 高效对话](./02-prompt-engineering.md)

相关速查表：[Claude Code 速查](../cheatsheets/claude-code.md) | [Cursor 速查](../cheatsheets/cursor.md)
