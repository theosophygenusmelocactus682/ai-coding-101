[English](./prompts.en.md) | **中文**

# 提示词模板速查表

> 可直接复制使用的提示词模板，覆盖日常开发中最常见的六类任务。

## Bug 修复

### 模板

```
修复以下 bug：

**错误信息**：
[粘贴完整的 error stack trace]

**期望行为**：
[描述正确的行为]

**实际行为**：
[描述错误的表现]

**相关代码**：
[文件路径或代码片段]

**已尝试**：
[列出你已经尝试过的方案]
```

### 实际示例

```
修复以下 bug：

错误信息：
TypeError: Cannot read properties of undefined (reading 'email')
  at sendWelcomeEmail (src/services/email.ts:42:18)

期望行为：新用户注册后收到欢迎邮件
实际行为：注册成功但邮件发送时崩溃

相关代码在 src/services/email.ts，用户数据来自 src/services/user.ts 的 createUser 函数

已尝试：添加了 null check 但仍然报错
```

## 新增功能

### 模板

```
为 [项目/模块] 添加 [功能名称]：

**需求**：
- [需求点 1]
- [需求点 2]
- [需求点 3]

**技术约束**：
- 使用 [框架/库]
- 遵循 [编码规范]
- 与现有的 [模块] 集成

**验收标准**：
- [标准 1]
- [标准 2]
```

### 实际示例

```
为用户模块添加密码重置功能：

需求：
- POST /api/auth/forgot-password 接收邮箱，发送重置链接
- GET /api/auth/reset-password?token=xxx 验证 token 有效性
- POST /api/auth/reset-password 接收新密码和 token，完成重置

技术约束：
- 使用 Express.js + TypeScript
- Token 使用 crypto.randomBytes 生成，有效期 1 小时
- 密码使用 bcrypt 加密，salt rounds = 12
- 与现有的 User model（Prisma）集成

验收标准：
- Token 过期后返回 400 错误
- 密码重置后旧 token 失效
- 包含 rate limiting（每邮箱每小时最多 3 次）
```

## 代码重构

### 模板

```
重构 [文件/模块]：

**当前问题**：
[描述代码 smell 或问题]

**重构目标**：
[期望达成的效果]

**约束**：
- 不改变对外接口
- 保持所有现有测试通过
- [其他约束]
```

### 实际示例

```
重构 src/controllers/orderController.ts：

当前问题：单个文件 400 行，processOrder 函数 150 行，混杂了验证、业务逻辑、数据库操作和邮件通知

重构目标：
- 拆分为 OrderValidator、OrderService、OrderNotifier
- 每个类职责单一
- processOrder 函数不超过 20 行

约束：
- 不改变路由层的调用方式
- 保持所有现有测试通过
- 先给出重构方案，确认后再执行
```

## 写测试

### 模板

```
为 [文件路径] 写 [测试类型] 测试：

**测试框架**：[Jest / Vitest / pytest / 等]
**需覆盖**：
- 正常路径
- 边界条件：[列举]
- 错误处理：[列举]

**Mock 策略**：
- Mock [外部依赖]
- 不要 mock [内部模块]
```

### 实际示例

```
为 src/services/payment.ts 的 processPayment 函数写单元测试：

测试框架：Jest + ts-jest
需覆盖：
- 正常支付成功
- 金额为 0 时拒绝
- 金额超过限额时拒绝
- 支付网关超时处理
- 重复支付幂等性检查

Mock 策略：
- Mock 支付网关 API（src/lib/stripe.ts）
- Mock 数据库调用（src/repositories/payment.ts）
- 不要 mock validateAmount 等内部工具函数
```

## 代码审查

### 模板

```
审查以下代码变更，关注：

1. **安全性**：是否有注入、XSS、敏感信息泄露
2. **性能**：是否有 N+1 查询、内存泄漏、不必要的计算
3. **可维护性**：命名是否清晰、逻辑是否易懂
4. **错误处理**：是否覆盖了异常情况
5. **测试覆盖**：是否需要补充测试

[粘贴代码 diff 或指定 git diff 范围]
```

### 实际示例

```
审查 git diff HEAD~3 的所有变更，关注：

1. 安全性：这次改动涉及用户输入处理，检查是否有注入风险
2. 性能：新增的数据库查询是否需要添加索引
3. 可维护性：新增的工具函数命名是否一致
4. 错误处理：API 端点是否正确处理了所有错误状态码
5. 测试覆盖：新功能是否有对应的测试

对每个发现的问题给出严重程度（高/中/低）和修复建议。
```

## 代码解释

### 模板

```
解释 [文件路径] 中的 [函数/类/模块]：

**需要说明**：
- 整体架构和数据流
- 核心算法的工作原理
- 为什么这样设计（而不是其他方案）
- 潜在的改进空间

**输出格式**：用简洁的中文说明，关键术语保留英文。
```

### 实际示例

```
解释 src/core/reconciler.ts 中的 reconcile 函数：

需要说明：
- 这个 diff 算法的整体思路
- 时间复杂度和空间复杂度
- key 参数在算法中的作用
- 与 React 的 reconciliation 算法的异同

输出格式：用简洁的中文说明，关键术语保留英文。
包含一个简单的例子来说明算法的执行过程。
```
