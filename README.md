# Claude Code Project Template

A starter template for projects using [Claude Code](https://claude.ai/claude-code), Anthropic's AI-powered CLI for software development.

## What's Included

```
.
├── .claude/
│   ├── settings.json         # Shared project settings & plugins
│   ├── settings.local.json   # Personal settings (gitignored)
│   └── skills/
│       ├── create-skill/     # Create new skills from templates
│       └── worktree/         # Isolated git worktree workflow
├── claude.md                 # Project context for Claude
└── README.md
```

## Quick Start

1. **Use this template**
   ```bash
   # Via GitHub template feature, or:
   git clone https://github.com/shawnrushefsky/claude-template.git my-project
   cd my-project
   rm -rf .git && git init
   ```

2. **Start Claude Code**
   ```bash
   claude
   ```

3. **Verify setup**
   ```
   > /skills
   ```
   You should see `worktree` and `create-skill` available.

## Pre-configured Plugins

| Plugin | Purpose |
|--------|---------|
| `context7` | Access up-to-date library documentation |
| `code-review` | Structured pull request reviews |
| `typescript-lsp` | TypeScript language intelligence |
| `hookify` | Create hooks interactively |
| `agent-sdk-dev` | Claude Agent SDK development |
| `plugin-dev` | Plugin development support |

## Included Skills

### `/worktree`

Creates isolated git worktrees for parallel development:

```
> /worktree add-authentication
```

Creates `../my-project-add-authentication/` with a new branch, copies local settings, and runs dependency installation.

### `/create-skill`

Scaffolds new skills interactively:

```
> /create-skill
```

Guides you through creating a new skill with proper frontmatter and structure.

## Customizing for Your Project

### 1. Update `claude.md`

The `claude.md` file provides project-specific context to Claude. Update it with:

- Project overview and architecture
- Coding conventions and patterns
- Common workflows and procedures
- Links to important documentation

### 2. Add Project Skills

Create skills for repeated workflows:

```bash
.claude/skills/
├── deploy/SKILL.md          # Deployment procedures
├── test-coverage/SKILL.md   # Testing standards
└── api-design/SKILL.md      # API conventions
```

### 3. Configure Plugins

Edit `.claude/settings.json` to enable/disable plugins:

```json
{
  "enabledPlugins": {
    "your-plugin@source": true
  }
}
```

### 4. Set Up Hooks

Use the `hookify` plugin or create hooks manually for:

- Pre-commit validation
- Automated formatting
- Custom notifications

## Project Philosophy

This template encourages **continuous learning**—capturing knowledge as skills, hooks, and documentation so Claude gets smarter about your project over time.

See `claude.md` for detailed guidance on when to create:
- Skills (repeated multi-step tasks)
- Hooks (automated responses to events)
- Documentation (project knowledge)

## File Reference

| File | Purpose | Committed? |
|------|---------|------------|
| `.claude/settings.json` | Shared plugin config | Yes |
| `.claude/settings.local.json` | Personal settings | No |
| `.claude/skills/*/SKILL.md` | Reusable instructions | Yes |
| `claude.md` | Project context | Yes |

## Contributing

When contributing to projects using this template:

1. Read `claude.md` for project conventions
2. Check existing skills before creating duplicates
3. Update documentation alongside code changes
4. Consider creating skills for new workflows

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Skills Guide](https://docs.anthropic.com/claude-code/skills)
- [Hooks Reference](https://docs.anthropic.com/claude-code/hooks)
- [Plugin Development](https://docs.anthropic.com/claude-code/plugins)

## License

MIT
