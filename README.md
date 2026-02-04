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

# Install the skill (includes GitLab MCP server)
/plugin install gitlab-mr-review@zhiyue-claude-skills
```

### Prerequisites

The `gitlab-mr-review` plugin bundles a GitLab MCP server. Set these environment variables before use:

```bash
export GITLAB_PERSONAL_ACCESS_TOKEN="your-gitlab-token"
export GITLAB_API_URL="https://gitlab.example.com/api/v4"
```

## Manual Installation

```bash
git clone https://github.com/zhiyue/claude-skills.git ~/.claude/skills/claude-skills
```

Or copy individual skills:

```bash
cp -r skills/gitlab-mr-review ~/.claude/skills/gitlab-mr-review
```

When installing manually, you also need to configure the GitLab MCP server in `~/.claude.json`:

```json
{
  "mcpServers": {
    "gitlab": {
      "command": "npx",
      "args": ["-y", "@zereight/mcp-gitlab"],
      "env": {
        "GITLAB_PERSONAL_ACCESS_TOKEN": "your-token",
        "GITLAB_API_URL": "https://gitlab.example.com/api/v4",
        "GITLAB_READ_ONLY_MODE": "false"
      }
    }
  }
}
```

## License

MIT
