[English](./04-project-setup.en.md) | **中文**

# 04 - 项目配置篇：让 AI 理解你的项目

> 正确的项目配置能让 AI 的输出质量提升一个量级。每种工具有自己的配置文件格式。

## CLAUDE.md 最佳实践

`CLAUDE.md` 是 Claude Code 读取的项目配置文件，放在项目根目录。

```markdown
# CLAUDE.md

## 项目概述
这是一个 SaaS 订单管理系统，使用 Next.js 14 + Prisma + PostgreSQL。

## 技术栈
- 前端：Next.js 14 (App Router), TypeScript, Tailwind CSS
- 后端：Next.js API Routes, Prisma ORM
- 数据库：PostgreSQL 16
- 测试：Jest + React Testing Library

## 代码规范
- 使用 ESLint + Prettier，提交前运行 lint
- 组件使用函数式写法，不使用 class 组件
- API 路由统一返回 { data, error, message } 格式
- 数据库查询统一放在 src/repositories/ 目录

## 目录结构
- src/app/ — 页面和路由
- src/components/ — 可复用组件
- src/lib/ — 工具函数和配置
- src/repositories/ — 数据库操作层

## 常用命令
- npm run dev — 启动开发服务器
- npm test — 运行测试
- npx prisma migrate dev — 执行数据库迁移
```

**关键点**：

- 简洁明了，不要超过 100 行
- 包含 AI 最需要知道的信息：技术栈、规范、目录结构
- 随项目演进持续更新

更多 CLAUDE.md 模板和最佳实践：[awesome-claude-md](https://github.com/jnMetaCode/awesome-claude-md)

## .cursorrules 配置

`.cursorrules` 是 Cursor 的项目级配置文件。

```
You are an expert in Next.js 14, TypeScript, and Tailwind CSS.

Code Style:
- Use functional components with TypeScript interfaces
- Prefer named exports over default exports
- Use absolute imports with @/ prefix
- Always handle loading and error states in components

Naming:
- Components: PascalCase (UserProfile.tsx)
- Utilities: camelCase (formatDate.ts)
- Constants: UPPER_SNAKE_CASE

Testing:
- Write tests alongside implementation
- Use React Testing Library, avoid testing implementation details
- Mock external services, not internal modules
```

## AGENTS.md (Codex)

`AGENTS.md` 是 OpenAI Codex CLI 使用的配置文件。

```markdown
# AGENTS.md

## Setup
Run `npm install` before any task.

## Testing
Run `npm test` to verify changes. All tests must pass.

## Style
- Follow existing code patterns in the repository
- Use TypeScript strict mode
- Prefer composition over inheritance
```

## GEMINI.md (Gemini CLI)

`GEMINI.md` 是 Google Gemini CLI 的项目配置。

```markdown
# GEMINI.md

## Project
Node.js REST API using Express and TypeScript.

## Conventions
- All endpoints return JSON with status field
- Use zod for input validation
- Error responses follow RFC 7807 format
```

## 项目级 vs 全局配置

| 配置层级 | 适用范围 | 示例场景 |
|----------|----------|----------|
| 项目级 | 单个项目 | 技术栈、代码规范、目录结构 |
| 全局级 | 所有项目 | 个人偏好（语言、风格）、通用规则 |

**Claude Code 全局配置**：`~/.claude/CLAUDE.md`

```markdown
# 全局偏好
- 回答使用中文
- 代码注释用英文
- 生成代码时默认包含错误处理
```

**Cursor 全局配置**：在 Settings 中设置 global rules。

## Skills 和超能力

Claude Code 支持通过 Skills 扩展能力——预定义的工作流模板，让常见任务一句话完成。

```bash
# 使用 skill 一键生成 PR 描述
> /pr-description

# 使用 skill 执行代码审查
> /review
```

更多精选 Skills 和进阶用法：[superpowers-zh](https://github.com/jnMetaCode/superpowers-zh)

---

上一篇：[工作流篇](./03-workflow-patterns.md) | 下一篇：[进阶篇](./05-advanced-techniques.md)
