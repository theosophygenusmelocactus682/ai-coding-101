[English](./02-prompt-engineering.en.md) | **中文**

# 02 - 提示词篇：如何与 AI 高效对话

> 提示词是你和 AI 之间的接口。写好提示词，产出质量天差地别。

## 与 AI 编程助手对话的基本原则

AI 不是搜索引擎，它是一个需要"指令"的协作者。好的提示词包含三个要素：

1. **目标**：你要完成什么
2. **上下文**：当前的技术栈、约束条件、已有代码
3. **格式**：你希望输出什么样的结果

## 好提示词 vs 坏提示词

### 示例 1：Bug 修复

```
# 不好
这个函数有 bug，帮我修一下

# 好
这个函数在输入空数组时抛出 TypeError。期望行为是返回空数组。
请修复并添加对空输入的边界检查。

function filterActive(users) {
  return users.filter(u => u.status === 'active');
}
```

### 示例 2：新功能

```
# 不好
加个登录功能

# 好
为现有的 Express.js 后端添加 JWT 登录功能：
- POST /auth/login 接收 email 和 password
- 验证成功返回 JWT token（有效期 24h）
- 使用 bcrypt 比较密码
- 错误时返回 401 和具体错误信息
- 与现有的 User model（Prisma ORM）集成
```

### 示例 3：重构

```
# 不好
重构这段代码

# 好
将这个 200 行的 handleSubmit 函数拆分为更小的函数：
- 表单验证逻辑提取为 validateForm()
- API 调用提取为 submitToApi()
- 错误处理提取为 handleError()
保持现有行为不变，不改变对外接口。
```

## 上下文管理

### 该包含什么

- 相关的类型定义 / 接口
- 报错信息的完整 stack trace
- 数据库 schema 或 API 的关键字段
- 你期望的行为和实际的行为

### 该省略什么

- 无关的代码文件
- 过长的日志（只贴关键部分）
- 已经在项目配置文件中说明的信息（AI 会自动读取）

### 实用技巧

```bash
# Claude Code 中引用文件
> 请阅读 src/auth/login.ts 和 src/models/user.ts，
  然后为登录流程添加 rate limiting

# Cursor 中使用 @ 引用
# 在对话框输入 @filename 引用特定文件
```

## 多轮对话策略

**策略 1：渐进式细化**

```
第 1 轮：帮我设计一个缓存模块的接口
第 2 轮：好的，现在用 Redis 实现这个接口
第 3 轮：添加 TTL 支持和缓存淘汰策略
第 4 轮：为这个模块写单元测试
```

**策略 2：先计划再执行**

```
> 我需要把项目从 REST 迁移到 GraphQL。
  先别写代码，帮我列出迁移步骤和需要修改的文件。

（审查计划后）

> 计划看起来不错，先从第 1 步开始：创建 GraphQL schema
```

**策略 3：角色设定**

```
> 你是一个资深的安全工程师。请审查以下登录代码，
  找出潜在的安全漏洞并给出修复建议。
```

## 各语言提示词技巧

### Python

```
> 使用 Python 3.12+ 的特性，包括 type hints。
  遵循 PEP 8 规范。使用 dataclass 而非普通 dict。
```

### JavaScript / TypeScript

```
> 使用 TypeScript strict mode。
  优先使用 interface 而非 type。
  异步操作使用 async/await 而非 .then() 链。
```

### Go

```
> 遵循 Go 惯例：错误处理用 error return，不用 panic。
  结构体字段使用 json tag。
  公开函数必须写 godoc 注释。
```

### Java

```
> 使用 Java 21+ 的特性。
  遵循 Spring Boot 3 的最佳实践。
  使用 record 替代简单的 POJO。
```

---

上一篇：[入门篇](./01-getting-started.md) | 下一篇：[工作流篇](./03-workflow-patterns.md)
