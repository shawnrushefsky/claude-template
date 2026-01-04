# Claude Code Project Configuration

This project is a template for Claude Code-enhanced development. It's designed to evolve with the team's learnings and encode institutional knowledge directly into the development workflow.

## Project Philosophy

**Continuous learning through automation.** Every time we solve a problem, we should ask: "Can we teach Claude to do this automatically next time?" The answer is usually yes, through one of four mechanisms:

1. **Skills** - Reusable instructions for complex, multi-step tasks
2. **Plugins** - Extended capabilities via external tools
3. **Hooks** - Automated responses to specific events
4. **Documentation** - Context that makes Claude smarter about this project

## When to Create New Learning Artifacts

### Create a Skill When...

- You find yourself giving Claude the same multi-step instructions repeatedly
- A task requires specialized knowledge about this project's conventions
- You want to standardize a workflow across the team
- A procedure is error-prone and benefits from explicit steps

**Example triggers:** "Every time I create a new component...", "The deploy process always requires...", "When reviewing PRs we always check..."

```bash
# Skills live here:
.claude/skills/<skill-name>/SKILL.md
```

Use `/create-skill` to scaffold a new skill interactively.

### Enable a Plugin When...

- You need capabilities beyond Claude's built-in tools
- A third-party integration would improve the workflow
- Code analysis requires specialized tooling (LSP, linters)
- You want to search external documentation

**Currently enabled plugins:**
- `code-review` - Structured PR reviews
- `context7` - Up-to-date library documentation
- `hookify` - Create hooks interactively
- `typescript-lsp` - TypeScript language intelligence
- `agent-sdk-dev` - Agent SDK development support
- `plugin-dev` - Plugin development support

### Create a Hook When...

- An action should automatically trigger before/after tool use
- You want guardrails or validation on certain operations
- Notifications or logging should happen on specific events
- You want to enforce project conventions automatically

**Hook types:**
| Hook | Triggers |
|------|----------|
| `PreToolUse` | Before a tool executes |
| `PostToolUse` | After a tool completes |
| `Notification` | On specific Claude events |
| `Stop` | When Claude's response completes |

Use the `hookify` plugin to create hooks interactively.

### Update Documentation When...

- You discover something non-obvious about the codebase
- A dependency has quirks that tripped you up
- There's tribal knowledge that should be captured
- A decision was made that future-you will question

## Project Structure

```
.claude/
├── settings.json        # Shared settings (committed)
├── settings.local.json  # Personal settings (gitignored)
└── skills/
    ├── create-skill/    # Skill for creating new skills
    └── worktree/        # Isolated git worktree workflow
```

## Learning Loops

### After Solving a Bug

1. **Was it hard to find?** Consider adding search patterns or keywords to relevant docs
2. **Was it a common pattern?** Create a debugging skill or checklist
3. **Could it have been prevented?** Add a hook that validates or warns

### After Completing a Feature

1. **Were there repeated steps?** Create a skill to automate them
2. **Did you need external docs?** Ensure context7 or similar is configured
3. **Would others benefit?** Document the approach in this file or a dedicated guide

### After a PR Review

1. **Were the same issues caught again?** Add to code review checklist
2. **Did the reviewer share knowledge?** Capture it in docs or skills
3. **Could automation have caught it?** Consider hooks or CI integration

## Conventions

### Skill Naming
- Use kebab-case: `deploy-staging`, `create-component`, `review-security`
- Be descriptive: skill names should hint at their purpose
- Keep names short but unambiguous

### Documentation Style
- Lead with "why", follow with "how"
- Include concrete examples
- Keep sections scannable with headers and bullet points
- Update docs alongside code changes

### Hook Discipline
- Hooks should be fast and non-blocking where possible
- Log hook failures rather than blocking the workflow
- Test hooks in a worktree before merging

## Getting Started with Learning

New to this project? Here's how to start building your own learning artifacts:

1. **Review existing skills** in `.claude/skills/` to understand the format
2. **Check enabled plugins** in `.claude/settings.json`
3. **Ask Claude** to help create new skills, hooks, or documentation
4. **Use worktrees** (`/worktree`) to experiment safely

## Meta: Improving This Document

This `claude.md` is itself a learning artifact. When you:
- Find yourself explaining the same thing to Claude repeatedly
- Discover a better workflow or convention
- Learn something about the project that isn't captured here

...update this file. The next person (including future-you) will benefit.

---

*Remember: The goal isn't perfection—it's continuous improvement. Every small addition compounds over time.*
