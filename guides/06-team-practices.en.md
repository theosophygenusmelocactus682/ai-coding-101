**English** | [中文](./06-team-practices.md)

# 06 - Team Practices: Adopting AI Coding Across Your Team

> From individual use to team-wide standards — covering adoption strategy, shared config, security, and cost management.

## Onboarding Your Team

### A Phased Approach

**Phase 1 (1-2 weeks): Pilot**

- Pick 2-3 interested developers to try first
- Choose a real task of moderate complexity as the pilot
- Track productivity gains and issues encountered

**Phase 2 (2-4 weeks): Expand**

- Turn pilot learnings into an internal guide
- Host a team demo showcasing real examples
- Create standardized project config files (CLAUDE.md, etc.)

**Phase 3 (ongoing): Standardize**

- Incorporate AI tools into the team's standard workflow
- Build a shared prompt library and skills library
- Regularly review and optimize usage patterns

### Addressing Common Resistance

| Resistance | Response |
|-----------|----------|
| "AI will replace us" | AI is a productivity tool, not a replacement. It handles repetitive work so you can focus on creative work |
| "AI code quality is unreliable" | Set code review standards — AI-generated code goes through the same review process as human code |
| "The learning curve is too steep" | Start with simple tasks (completions, writing tests), then go deeper gradually |

## Shared Configuration and Standards

### Project Config Templates

Create standardized config templates for the team, stored in an internal repository:

```
team-ai-config/
├── templates/
│   ├── CLAUDE.md.template     # Claude Code project config
│   ├── cursorrules.template   # Cursor config
│   └── AGENTS.md.template     # Codex config
├── skills/
│   ├── code-review.md         # Code review skill
│   ├── pr-description.md      # PR description skill
│   └── api-endpoint.md        # API endpoint creation skill
└── prompts/
    ├── bug-fix.md             # Bug fix prompt template
    └── feature.md             # New feature prompt template
```

### Unified Code Standards

Declare team standards explicitly in config files so every member's AI output is consistent:

```markdown
## Team Code Standards
- Naming: camelCase (JS/TS), snake_case (Python)
- Functions must not exceed 50 lines
- Every public function must have a doc comment
- Error handling: no empty catch blocks
- Commit format: type(scope): description
```

## Code Review in AI-Assisted Teams

### New Review Checkpoints

When your team uses AI tools, code review should add these focus areas:

- **Comprehension check**: Does the author understand the AI-generated code? Can they explain the key logic?
- **Over-engineering check**: AI sometimes over-designs. Is this abstraction layer actually needed?
- **Hallucination check**: Do the APIs or library functions cited by the AI actually exist? Are the versions correct?
- **Security check**: Did the AI introduce hardcoded secrets, insecure dependencies, or injection vulnerabilities?

### Recommended Flow

```
Developer completes feature
    ↓
AI auto-review (round 1)
    ↓
Fix issues found by AI
    ↓
Human review (round 2) — focus on business logic and architecture
    ↓
Merge
```

## Security Considerations

### Do

- Confirm the AI tool's data handling policy (does it train on your code?)
- Exclude sensitive files from `.gitignore` and AI config (`.env`, key files, etc.)
- Verify dependencies in AI-generated code — ensure packages actually exist and versions are secure
- Apply extra human review to code involving auth, encryption, and payments

### Don't

- Don't paste production API keys into AI conversations
- Don't let AI directly operate on production databases
- Don't discuss unreleased trade secrets in public AI tools

## Cost Management

### Control Strategies

| Strategy | Details |
|----------|---------|
| Set usage quotas | Monthly API call limits per team member |
| Choose the right model | Use cheaper models for simple tasks, premium models for complex ones |
| Optimize prompts | Good prompts reduce the number of retry attempts |
| Use project config | CLAUDE.md and similar files eliminate repeated context |

### Cost Estimates

| Tool | Monthly per seat | Best for |
|------|-----------------|----------|
| GitHub Copilot Business | $19 | Any team size |
| Cursor Pro | $20 | Small to mid-size teams |
| Claude Code Max | $100-200 | High-frequency core developers |

---

Previous: [Advanced Techniques](./05-advanced-techniques.en.md) | Next: [Tools Comparison](./07-tools-comparison.en.md)
