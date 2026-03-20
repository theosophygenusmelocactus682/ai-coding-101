[English](./claude-code.en.md) | **中文**

# Claude Code 速查表

> 快捷键、斜杠命令、常用工作流一页掌握。

## 斜杠命令

| 命令 | 说明 |
|------|------|
| `/help` | 显示帮助信息 |
| `/clear` | 清空当前对话上下文 |
| `/compact` | 压缩对话历史，释放上下文空间 |
| `/config` | 查看或修改配置 |
| `/cost` | 显示当前会话的 token 用量和费用 |
| `/doctor` | 诊断 Claude Code 的安装和配置问题 |
| `/init` | 在当前项目创建 CLAUDE.md |
| `/login` | 登录或切换账号 |
| `/logout` | 退出登录 |
| `/mcp` | 管理 MCP server 连接 |
| `/model` | 切换模型（Sonnet / Opus） |
| `/permissions` | 管理工具权限（允许/拒绝） |
| `/pr-description` | 根据 git diff 生成 PR 描述 |
| `/review` | 审查当前代码变更 |
| `/status` | 显示当前会话状态 |
| `/vim` | 切换 vim 模式 |

## 快捷键

| 快捷键 | 说明 |
|--------|------|
| `Ctrl+C` | 中断当前 AI 操作 |
| `Ctrl+D` | 退出 Claude Code |
| `Esc` | 取消当前输入 |
| `Up/Down` | 浏览历史消息 |
| `Tab` | 自动补全文件路径 |
| `Shift+Tab` | 切换多行输入模式 |

## 命令行参数

```bash
# 启动并附带初始消息
claude "帮我审查最近的 commit"

# 非交互模式（适合脚本）
claude --message "修复 lint 错误" --no-interactive

# 指定模型
claude --model opus

# 从 stdin 读取输入
cat error.log | claude "分析这个错误日志"

# 恢复上次会话
claude --resume
```

## 常用工作流

### 快速修复 lint 错误

```
> 运行 npm run lint，修复所有报错
```

### 生成测试

```
> 为 src/services/auth.ts 的所有公开方法写单元测试，
  使用 Jest，mock 外部依赖
```

### 代码审查

```
> 审查 git diff main...HEAD 的所有变更，
  关注安全问题和潜在 bug
```

### 快速创建功能

```
> 在 src/api/routes/ 添加一个 GET /api/health 端点，
  返回 { status: "ok", timestamp: Date.now() }
```

### 理解代码

```
> 解释 src/core/scheduler.ts 的工作原理，
  重点说明任务调度的核心逻辑
```

### 数据库迁移

```
> 阅读当前的 Prisma schema，添加一个 Comment 模型：
  - id, content, authorId, postId, createdAt
  然后生成并运行迁移
```

## 高效使用技巧

1. **善用 `/compact`**：对话变长时压缩上下文，避免 AI "遗忘"重要信息
2. **引用文件路径**：直接告诉 AI 文件路径，比描述文件内容更高效
3. **先看再改**：让 AI 先分析代码再修改，`先阅读 X 文件，然后...`
4. **分步执行**：复杂任务拆成小步骤，每步确认后再继续
5. **利用 CLAUDE.md**：把项目的关键信息写进配置文件，减少每次重复说明
