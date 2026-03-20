**English** | [中文](./01-getting-started.md)

# 01 - Getting Started: Your First Steps with AI Coding

> Choose a tool, install it, and write your first AI-assisted code from scratch.

## What is AI-Assisted Coding

AI-assisted coding uses large language models (LLMs) to help you with programming tasks — code generation, debugging, refactoring, testing, documentation, and more. You don't need to change your language or framework; the AI integrates into your existing workflow as a pair programming partner.

Core benefits:

- Eliminate repetitive coding; focus on architecture and logic
- Quickly explore unfamiliar APIs and frameworks
- Improve code quality (AI catches edge cases you might miss)

## Which Tool to Choose

```
Do you prefer working in the terminal?
├── Yes → Do you handle complex multi-file tasks?
│   ├── Yes → Claude Code
│   └── No  → Codex CLI / Gemini CLI
└── No  → Do you want a full IDE experience?
    ├── Yes → Cursor
    └── No  → GitHub Copilot (install in your existing VS Code)
```

**Beginner advice**: If you are not sure, start with GitHub Copilot (lowest barrier to entry). Once you are comfortable with AI-assisted coding, try Claude Code or Cursor.

## Installation

### Claude Code

```bash
# Requires Node.js 18+
npm install -g @anthropic-ai/claude-code

# Navigate to your project and launch
cd your-project
claude
```

### Cursor

1. Download from [cursor.com](https://cursor.com)
2. Open it — your VS Code settings are imported automatically
3. Press `Cmd+K` (Mac) or `Ctrl+K` (Windows/Linux) to start an AI conversation

### GitHub Copilot

1. Search "GitHub Copilot" in the VS Code extension marketplace and install
2. Sign in with your GitHub account and activate a subscription
3. Start typing — Copilot suggests completions inline (press Tab to accept)

## Your First AI Coding Session

Using Claude Code as an example, let's create a simple TODO API:

```bash
$ claude
> Create an Express.js TODO RESTful API with:
  - GET /todos — list all todos
  - POST /todos — create a todo
  - PUT /todos/:id — update a todo
  - DELETE /todos/:id — delete a todo
  Use in-memory storage, no database. Include basic error handling.
```

Key takeaways:

- Your first prompt doesn't need to be perfect; you can iterate
- Let the AI generate the skeleton, then refine the details
- Always **read and understand the code** — never accept blindly

## 5 Common Beginner Mistakes

**1. Accepting AI-generated code without review**

AI makes mistakes. Every line it generates needs your review. Treat it like a junior developer — fast but needs oversight.

**2. Vague prompts**

- Bad: `Build me a website`
- Good: `Create a blog homepage with Next.js 14 that displays a list of posts, each showing title, excerpt, and publish date`

**3. Giving the AI tasks that are too large**

Break big tasks into small steps. Don't expect one prompt to produce an entire project — work module by module.

**4. Ignoring context management**

AI conversations have context limits. As conversations grow long, early information may be "forgotten." Start fresh sessions when needed, and re-provide essential context.

**5. Not using project configuration files**

Create a `CLAUDE.md` or `.cursorrules` for your project to tell the AI about your project structure, tech stack, and coding standards. This significantly improves output quality. See [Project Setup](./04-project-setup.en.md).

---

Next: [Prompt Engineering - How to Talk to Your AI Assistant](./02-prompt-engineering.en.md)

Related cheatsheets: [Claude Code](../cheatsheets/claude-code.en.md) | [Cursor](../cheatsheets/cursor.en.md)
