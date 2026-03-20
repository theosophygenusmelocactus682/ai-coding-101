**English** | [中文](./claude-code.md)

# Claude Code Cheatsheet

> Keyboard shortcuts, slash commands, and common workflows at a glance.

## Slash Commands

| Command | Description |
|---------|-------------|
| `/help` | Show help information |
| `/clear` | Clear current conversation context |
| `/compact` | Compress conversation history to free context space |
| `/config` | View or modify configuration |
| `/cost` | Show token usage and cost for the current session |
| `/doctor` | Diagnose installation and configuration issues |
| `/init` | Create CLAUDE.md in the current project |
| `/login` | Log in or switch accounts |
| `/logout` | Log out |
| `/mcp` | Manage MCP server connections |
| `/model` | Switch model (Sonnet / Opus) |
| `/permissions` | Manage tool permissions (allow/deny) |
| `/pr-description` | Generate PR description from git diff |
| `/review` | Review current code changes |
| `/status` | Show current session status |
| `/vim` | Toggle vim mode |

## Keyboard Shortcuts

| Shortcut | Description |
|----------|-------------|
| `Ctrl+C` | Interrupt the current AI operation |
| `Ctrl+D` | Exit Claude Code |
| `Esc` | Cancel current input |
| `Up/Down` | Browse message history |
| `Tab` | Autocomplete file paths |
| `Shift+Tab` | Toggle multi-line input mode |

## CLI Arguments

```bash
# Start with an initial message
claude "Review my latest commit"

# Non-interactive mode (for scripts)
claude --message "Fix lint errors" --no-interactive

# Specify a model
claude --model opus

# Pipe input from stdin
cat error.log | claude "Analyze this error log"

# Resume last session
claude --resume
```

## Common Workflows

### Quick Fix Lint Errors

```
> Run npm run lint and fix all errors
```

### Generate Tests

```
> Write unit tests for all public methods in src/services/auth.ts,
  using Jest, mock all external dependencies
```

### Code Review

```
> Review all changes in git diff main...HEAD,
  focus on security issues and potential bugs
```

### Quick Feature Creation

```
> Add a GET /api/health endpoint in src/api/routes/,
  return { status: "ok", timestamp: Date.now() }
```

### Understand Code

```
> Explain how src/core/scheduler.ts works,
  focus on the core task scheduling logic
```

### Database Migration

```
> Read the current Prisma schema, add a Comment model:
  - id, content, authorId, postId, createdAt
  Then generate and run the migration
```

## Efficiency Tips

1. **Use `/compact` often**: Compress context when conversations get long to prevent the AI from "forgetting" important information
2. **Reference file paths**: Tell the AI the file path directly — more efficient than describing what's in the file
3. **Read before edit**: Have the AI analyze code before modifying it: `Read X file first, then...`
4. **Execute in steps**: Break complex tasks into small steps; confirm each before continuing
5. **Leverage CLAUDE.md**: Put key project info in the config file to avoid repeating context every session
