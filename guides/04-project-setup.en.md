**English** | [中文](./04-project-setup.md)

# 04 - Project Setup: Help the AI Understand Your Codebase

> Proper project configuration can dramatically improve AI output quality. Each tool has its own config format.

## CLAUDE.md Best Practices

`CLAUDE.md` is the project configuration file that Claude Code reads. Place it in the project root.

```markdown
# CLAUDE.md

## Project Overview
A SaaS order management system using Next.js 14 + Prisma + PostgreSQL.

## Tech Stack
- Frontend: Next.js 14 (App Router), TypeScript, Tailwind CSS
- Backend: Next.js API Routes, Prisma ORM
- Database: PostgreSQL 16
- Testing: Jest + React Testing Library

## Code Standards
- ESLint + Prettier; run lint before committing
- Functional components only, no class components
- API routes return { data, error, message } format
- Database queries go in src/repositories/

## Directory Structure
- src/app/ — pages and routes
- src/components/ — reusable components
- src/lib/ — utilities and config
- src/repositories/ — database access layer

## Common Commands
- npm run dev — start dev server
- npm test — run tests
- npx prisma migrate dev — run database migrations
```

**Key points**:

- Keep it concise — no more than 100 lines
- Include what the AI needs most: tech stack, standards, directory structure
- Update it as the project evolves

More CLAUDE.md templates and best practices: [awesome-claude-md](https://github.com/jnMetaCode/awesome-claude-md)

## .cursorrules Configuration

`.cursorrules` is Cursor's project-level config file.

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

`AGENTS.md` is the config file used by OpenAI Codex CLI.

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

`GEMINI.md` is the project config for Google Gemini CLI.

```markdown
# GEMINI.md

## Project
Node.js REST API using Express and TypeScript.

## Conventions
- All endpoints return JSON with status field
- Use zod for input validation
- Error responses follow RFC 7807 format
```

## Project-Level vs Global Configuration

| Level | Scope | Example Use |
|-------|-------|-------------|
| Project | Single project | Tech stack, code standards, directory structure |
| Global | All projects | Personal preferences (language, style), universal rules |

**Claude Code global config**: `~/.claude/CLAUDE.md`

```markdown
# Global Preferences
- Respond in English
- Code comments in English
- Always include error handling in generated code
```

**Cursor global config**: Set global rules in Settings.

## Skills and Superpowers

Claude Code supports Skills — predefined workflow templates that let you accomplish common tasks with a single command.

```bash
# Generate a PR description with a skill
> /pr-description

# Run a code review with a skill
> /review
```

More curated skills and advanced usage: [superpowers-zh](https://github.com/jnMetaCode/superpowers-zh)

---

Previous: [Workflow Patterns](./03-workflow-patterns.en.md) | Next: [Advanced Techniques](./05-advanced-techniques.en.md)
