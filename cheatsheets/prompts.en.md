**English** | [中文](./prompts.md)

# Prompt Templates Cheatsheet

> Copy-paste prompt templates for the six most common development tasks.

## Bug Fix

### Template

```
Fix the following bug:

**Error message**:
[Paste the full error stack trace]

**Expected behavior**:
[Describe the correct behavior]

**Actual behavior**:
[Describe what goes wrong]

**Relevant code**:
[File path or code snippet]

**Already tried**:
[List approaches you have already attempted]
```

### Real Example

```
Fix the following bug:

Error message:
TypeError: Cannot read properties of undefined (reading 'email')
  at sendWelcomeEmail (src/services/email.ts:42:18)

Expected behavior: New users receive a welcome email after registration
Actual behavior: Registration succeeds but email sending crashes

Relevant code is in src/services/email.ts.
User data comes from the createUser function in src/services/user.ts.

Already tried: Added a null check but the error persists.
```

## New Feature

### Template

```
Add [feature name] to [project/module]:

**Requirements**:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

**Technical constraints**:
- Use [framework/library]
- Follow [coding standard]
- Integrate with existing [module]

**Acceptance criteria**:
- [Criterion 1]
- [Criterion 2]
```

### Real Example

```
Add password reset to the user module:

Requirements:
- POST /api/auth/forgot-password accepts email, sends a reset link
- GET /api/auth/reset-password?token=xxx validates token
- POST /api/auth/reset-password accepts new password + token, completes reset

Technical constraints:
- Use Express.js + TypeScript
- Generate token with crypto.randomBytes, 1-hour expiry
- Hash passwords with bcrypt, salt rounds = 12
- Integrate with existing User model (Prisma)

Acceptance criteria:
- Expired tokens return 400
- Old tokens are invalidated after password reset
- Rate limited to 3 requests per email per hour
```

## Code Refactoring

### Template

```
Refactor [file/module]:

**Current problems**:
[Describe the code smells or issues]

**Refactoring goals**:
[Desired outcome]

**Constraints**:
- Do not change the public interface
- Keep all existing tests passing
- [Other constraints]
```

### Real Example

```
Refactor src/controllers/orderController.ts:

Current problems: Single 400-line file. processOrder function is 150 lines
mixing validation, business logic, database operations, and email notifications.

Refactoring goals:
- Split into OrderValidator, OrderService, OrderNotifier
- Each class has a single responsibility
- processOrder function is no more than 20 lines

Constraints:
- Do not change how the router calls the controller
- Keep all existing tests passing
- Give me the plan first, then execute after confirmation
```

## Writing Tests

### Template

```
Write [test type] tests for [file path]:

**Test framework**: [Jest / Vitest / pytest / etc.]
**Cover**:
- Happy path
- Edge cases: [list them]
- Error handling: [list them]

**Mocking strategy**:
- Mock [external dependencies]
- Do not mock [internal modules]
```

### Real Example

```
Write unit tests for the processPayment function in src/services/payment.ts:

Test framework: Jest + ts-jest
Cover:
- Successful payment
- Amount of 0 is rejected
- Amount exceeding the limit is rejected
- Payment gateway timeout handling
- Duplicate payment idempotency check

Mocking strategy:
- Mock the payment gateway API (src/lib/stripe.ts)
- Mock database calls (src/repositories/payment.ts)
- Do not mock internal utilities like validateAmount
```

## Code Review

### Template

```
Review the following code changes, focusing on:

1. **Security**: Injection, XSS, sensitive data exposure
2. **Performance**: N+1 queries, memory leaks, unnecessary computation
3. **Maintainability**: Clear naming, understandable logic
4. **Error handling**: Are all failure cases covered?
5. **Test coverage**: Are additional tests needed?

[Paste code diff or specify git diff range]
```

### Real Example

```
Review all changes in git diff HEAD~3, focusing on:

1. Security: This change involves user input handling — check for injection risks
2. Performance: Do the new database queries need indexes?
3. Maintainability: Are the new utility function names consistent?
4. Error handling: Do API endpoints handle all error status codes correctly?
5. Test coverage: Do new features have corresponding tests?

For each finding, provide a severity level (high/medium/low) and a fix suggestion.
```

## Code Explanation

### Template

```
Explain [function/class/module] in [file path]:

**Please cover**:
- Overall architecture and data flow
- How the core algorithm works
- Why this design was chosen (over alternatives)
- Potential improvements

**Output format**: Clear, concise English.
```

### Real Example

```
Explain the reconcile function in src/core/reconciler.ts:

Please cover:
- The overall approach of this diff algorithm
- Time and space complexity
- The role of the key parameter in the algorithm
- Similarities and differences with React's reconciliation algorithm

Output format: Clear, concise English.
Include a simple example illustrating the algorithm's execution.
```

---

For more prompting techniques, see [Prompt Engineering](../guides/02-prompt-engineering.en.md)
