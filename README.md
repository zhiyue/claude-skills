# Claude Skills

A collection of Claude Code skills for development workflows.

## Skills

| Skill | Description |
|-------|-------------|
| [gitlab-mr-review](skills/gitlab-mr-review/) | GitLab MR code review - auto checkout, deep review, and post inline comments via GitLab MCP |

## Installation

```bash
# Add this marketplace in Claude Code
/plugin marketplace add zhiyue/claude-skills

# Install the skill
/plugin install gitlab-mr-review@zhiyue-claude-skills
```

## Manual Installation

```bash
git clone https://github.com/zhiyue/claude-skills.git ~/.claude/skills/claude-skills
```

Or copy individual skills:

```bash
cp -r skills/gitlab-mr-review ~/.claude/skills/gitlab-mr-review
```

## License

MIT
