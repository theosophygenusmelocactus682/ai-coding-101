**English** | [中文](./02-prompt-engineering.md)

# 02 - Prompt Engineering: How to Talk to Your AI Assistant

> The prompt is the interface between you and the AI. Better prompts produce dramatically better results.

## Principles of Communicating with AI Coding Assistants

AI is not a search engine — it is a collaborator that needs clear instructions. Good prompts have three elements:

1. **Goal**: What you want to accomplish
2. **Context**: Tech stack, constraints, existing code
3. **Format**: What the output should look like

## Good Prompts vs Bad Prompts

### Example 1: Bug Fix

```
# Bad
This function has a bug, please fix it

# Good
This function throws TypeError when given an empty array.
Expected behavior: return an empty array.
Please fix it and add a boundary check for empty input.

function filterActive(users) {
  return users.filter(u => u.status === 'active');
}
```

### Example 2: New Feature

```
# Bad
Add a login feature

# Good
Add JWT-based login to the existing Express.js backend:
- POST /auth/login accepts email and password
- Return a JWT token on success (24h expiry)
- Use bcrypt for password comparison
- Return 401 with a specific error message on failure
- Integrate with the existing User model (Prisma ORM)
```

### Example 3: Refactoring

```
# Bad
Refactor this code

# Good
Split this 200-line handleSubmit function into smaller functions:
- Extract form validation into validateForm()
- Extract the API call into submitToApi()
- Extract error handling into handleError()
Keep existing behavior unchanged. Do not change the public interface.
```

## Context Management

### What to Include

- Relevant type definitions / interfaces
- Full stack traces from error messages
- Database schema or key API fields
- Expected behavior vs actual behavior

### What to Skip

- Unrelated code files
- Excessively long logs (paste only the relevant section)
- Information already covered in your project configuration file (the AI reads it automatically)

### Practical Tips

```bash
# Reference files in Claude Code
> Read src/auth/login.ts and src/models/user.ts,
  then add rate limiting to the login flow

# Reference files in Cursor using @
# Type @filename in the chat to reference a specific file
```

## Multi-Turn Conversation Strategies

**Strategy 1: Progressive Refinement**

```
Turn 1: Design an interface for a caching module
Turn 2: Now implement the interface using Redis
Turn 3: Add TTL support and an eviction policy
Turn 4: Write unit tests for this module
```

**Strategy 2: Plan Before Executing**

```
> I need to migrate the project from REST to GraphQL.
  Don't write code yet — list the migration steps and files to modify.

(After reviewing the plan)

> The plan looks good. Start with step 1: create the GraphQL schema.
```

**Strategy 3: Role Assignment**

```
> You are a senior security engineer. Review the following login code,
  identify potential vulnerabilities, and suggest fixes.
```

## Language-Specific Prompting Tips

### Python

```
> Use Python 3.12+ features with type hints.
  Follow PEP 8. Prefer dataclasses over plain dicts.
```

### JavaScript / TypeScript

```
> Use TypeScript strict mode.
  Prefer interface over type.
  Use async/await instead of .then() chains.
```

### Go

```
> Follow Go conventions: use error returns, not panic.
  Add json tags to struct fields.
  Public functions must have godoc comments.
```

### Java

```
> Use Java 21+ features.
  Follow Spring Boot 3 best practices.
  Use records instead of simple POJOs.
```

---

Previous: [Getting Started](./01-getting-started.en.md) | Next: [Workflow Patterns](./03-workflow-patterns.en.md)
