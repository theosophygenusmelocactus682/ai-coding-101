**English** | [中文](./03-workflow-patterns.md)

# 03 - Workflow Patterns: AI in Your Daily Development

> Five core patterns for using AI in real development: TDD, code review, debugging, refactoring, and documentation.

## TDD with AI

**When to use**: Before building new features or fixing bugs — write tests first.

**Steps**:

1. Describe the feature; have the AI generate test cases
2. Run tests — confirm they all fail (red)
3. Have the AI write the implementation
4. Run tests — confirm they all pass (green)
5. Have the AI refactor while keeping tests green

```bash
# Claude Code example
> Write tests for a calculateDiscount(price, tier) function:
  - tier="standard" gets no discount
  - tier="vip" gets 10% off
  - Negative price throws an error
  - Price of 0 returns 0
  Use Jest. Write only the test file for now.

> All tests are failing. Now write the implementation to make them pass.
```

**Common pitfalls**:

- Don't let the AI write tests and implementation at the same time — it will make them "fit" each other rather than truly test the feature
- Check whether AI-generated tests cover edge cases

## Code Review with AI

**When to use**: Pre-PR self-review, reviewing others' code, understanding unfamiliar code.

**Steps**:

1. Provide the code diff to the AI
2. Ask it to review from specific angles (security, performance, readability, etc.)
3. Evaluate suggestions and adopt the reasonable ones

```bash
# Claude Code example
> Review the changes in git diff HEAD~1, focusing on:
  1. Potential security issues
  2. Performance bottlenecks
  3. Completeness of error handling
  4. Opportunities for simpler code
```

**Common pitfalls**:

- AI may over-optimize — not every suggestion is worth adopting
- AI lacks your business context; business logic decisions are yours to make

## Debugging with AI

**When to use**: Hard-to-locate bugs, confusing error messages.

**Steps**:

1. Provide the full error message (stack trace)
2. Describe expected vs actual behavior
3. Provide the relevant code
4. Let the AI analyze the root cause and suggest a fix

```bash
# A good debugging prompt
> Running npm test produces this error:
  TypeError: Cannot read properties of undefined (reading 'map')
  at UserList (src/components/UserList.tsx:15:22)

  Expected: component renders the user list
  Actual: crashes on first load

  Relevant code is in src/components/UserList.tsx
  Data comes from a useQuery hook
```

**Common pitfalls**:

- Pasting only the error without the code forces the AI to guess
- Not mentioning what you have already tried leads to repeated suggestions

## Refactoring with AI

**When to use**: Code works but needs better structure, lower complexity, or improved maintainability.

**Steps**:

1. Define the refactoring goal (do not change external behavior)
2. Ensure you have test coverage
3. Have the AI analyze current code issues
4. Refactor incrementally; verify tests pass after each step

```bash
# Claude Code example
> This file is 500 lines long and does too many things.
  Analyze its responsibilities and suggest how to split it
  into multiple modules. Give me the plan first — don't change code yet.

(After reviewing the plan)

> Plan looks good. Start by extracting DB logic into
  src/repositories/user.ts. Keep existing exports unchanged.
```

**Common pitfalls**:

- Refactoring without tests — the AI may introduce bugs you can't catch
- Refactoring too much at once — take small, verifiable steps

## Documentation with AI

**When to use**: API docs, READMEs, code comments, architecture docs.

**Steps**:

1. Specify the doc type and target audience
2. Provide source code or existing docs as input
3. Specify format requirements (Markdown, JSDoc, OpenAPI, etc.)

```bash
# Claude Code example
> Read all route files in src/api/ and generate
  OpenAPI 3.0 documentation. Include descriptions,
  parameters, request bodies, and response examples.

# Code comments
> Add JSDoc comments to all public functions in src/utils/crypto.ts,
  including parameter descriptions, return values, and usage examples.
```

**Common pitfalls**:

- The AI may fabricate API parameters that don't exist — always verify against code
- Not specifying a format results in inconsistent output styles

---

Previous: [Prompt Engineering](./02-prompt-engineering.en.md) | Next: [Project Setup](./04-project-setup.en.md)
