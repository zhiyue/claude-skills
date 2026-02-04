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

## GitLab MCP Configuration

The plugin bundles a GitLab MCP server,需要提供 `GITLAB_PERSONAL_ACCESS_TOKEN` 和 `GITLAB_API_URL`。以下任选一种方式配置：

### Option A: Shell 环境变量

```bash
# 添加到 ~/.zshrc 或 ~/.bashrc
export GITLAB_PERSONAL_ACCESS_TOKEN="your-gitlab-token"
export GITLAB_API_URL="https://gitlab.example.com/api/v4"
```

插件 marketplace.json 中使用 `${GITLAB_PERSONAL_ACCESS_TOKEN}` 语法，Claude Code 启动时会自动从 shell 环境变量解析。

### Option B: CLI 直接添加

```bash
claude mcp add --transport stdio gitlab \
  --env GITLAB_PERSONAL_ACCESS_TOKEN=your-token \
  --env GITLAB_API_URL=https://gitlab.example.com/api/v4 \
  -- npx -y @zereight/mcp-gitlab
```

### Option C: 项目级 `.mcp.json`

在项目根目录创建 `.mcp.json`（可加入 `.gitignore`）：

```json
{
  "mcpServers": {
    "gitlab": {
      "command": "npx",
      "args": ["-y", "@zereight/mcp-gitlab"],
      "env": {
        "GITLAB_PERSONAL_ACCESS_TOKEN": "${GITLAB_PERSONAL_ACCESS_TOKEN}",
        "GITLAB_API_URL": "${GITLAB_API_URL:-https://gitlab.example.com/api/v4}"
      }
    }
  }
}
```

### Option D: 用户级 `~/.claude.json`

直接写入 token（仅限个人机器）：

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

> **Tip:** `${VAR:-default}` 语法可设置默认值，如 `${GITLAB_API_URL:-https://gitlab.com/api/v4}`

## Manual Installation

```bash
git clone https://github.com/zhiyue/claude-skills.git ~/.claude/skills/claude-skills
```

Or copy individual skills:

```bash
cp -r skills/gitlab-mr-review ~/.claude/skills/gitlab-mr-review
```

手动安装时需要自行配置 GitLab MCP server（参考上述 Option B/C/D）。

## License

MIT
