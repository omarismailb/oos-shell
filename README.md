# oOs Shell

**A replicable second brain template powered by Claude Code.**

oOs (Operating System for the Self) Shell is a pre-configured knowledge management system using the PARA method with Claude Code integration. Clone it, customize it, and build your own AI-assisted second brain.

---

## What You Get

- **7 Template Knowledge Files** - Pre-structured core files for any project or business
- **3 Specialized Agents** - Researcher, Writer, and Analyst ready to help
- **Auto-Activating Skills** - Onboarding, memory updates, and knowledge audits
- **Glob-Pattern Rules** - Consistent standards across file types
- **PARA Method Structure** - Projects, Areas, Resources, Archive organization

---

## Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/{{YOUR_USERNAME}}/oos-shell.git my-second-brain
cd my-second-brain
```

### 2. Customize CLAUDE.md

Open `CLAUDE.md` and replace placeholders:

```markdown
# Find and replace these:
{{PROJECT_NAME}}  → Your project name (e.g., "Acme Second Brain")
{{DATE}}          → Today's date (e.g., "2025-01-15")
{{YOUR_NAME}}     → Your name
```

### 3. Configure MCP Servers (Optional)

Add integrations to `.claude/settings.json` or your global `~/.claude.json`:

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_API_KEY": "your-notion-api-key"
      }
    }
  }
}
```

### 4. Start Using

```bash
claude
```

Tell Claude to onboard your first piece of context:

```
Onboard this transcript: [paste your content]
```

---

## Directory Structure

```
your-project/
├── .claude/                      ← Claude Code configuration
│   ├── agents/                   ← Specialized AI agents
│   ├── skills/                   ← Auto-activating skills
│   ├── rules/                    ← Glob-pattern standards
│   └── docs/                     ← Internal documentation
│
├── 0__inbox/                     ← Unprocessed items (triage here)
├── 1__knowledge/                 ← AREAS - ongoing responsibilities
│   ├── core/                     ← Your 7 core files
│   ├── frameworks/               ← Reusable thinking tools
│   └── templates/                ← Document templates
│
├── 2__projects/                  ← PROJECTS - bounded efforts with end dates
├── 3__scripts/                   ← Automation and data processing
└── 9__archive/                   ← ARCHIVE - completed items
```

---

## MCP Server Configuration

MCP (Model Context Protocol) servers extend Claude's capabilities with external tools and data sources.

### Configuration Locations

| Location | Scope | Use Case |
|----------|-------|----------|
| `.claude/settings.json` | This project only | Project-specific integrations |
| `~/.claude.json` | All projects | Personal tools you always want |

### Popular MCP Servers

#### Notion

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_API_KEY": "secret_..."
      }
    }
  }
}
```

**Getting your Notion API key:**
1. Go to [notion.so/my-integrations](https://www.notion.so/my-integrations)
2. Create a new integration
3. Copy the "Internal Integration Token"
4. Share your databases/pages with the integration

#### Slack

```json
{
  "mcpServers": {
    "slack": {
      "command": "npx",
      "args": ["-y", "@anthropic/slack-mcp-server"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-...",
        "SLACK_USER_TOKEN": "xoxp-..."
      }
    }
  }
}
```

**Getting Slack tokens:**
1. Create a Slack app at [api.slack.com/apps](https://api.slack.com/apps)
2. Add OAuth scopes: `channels:read`, `chat:write`, `users:read`
3. Install to your workspace
4. Copy the Bot Token and User Token

#### Google Drive

```json
{
  "mcpServers": {
    "gdrive": {
      "command": "npx",
      "args": ["-y", "@anthropic/gdrive-mcp-server"],
      "env": {
        "GOOGLE_CLIENT_ID": "...",
        "GOOGLE_CLIENT_SECRET": "...",
        "GOOGLE_REFRESH_TOKEN": "..."
      }
    }
  }
}
```

**Getting Google credentials:**
1. Create a project in [Google Cloud Console](https://console.cloud.google.com)
2. Enable the Google Drive API
3. Create OAuth 2.0 credentials (Desktop app)
4. Use the OAuth playground or a script to get refresh token

#### Filesystem (Local Files)

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@anthropic/filesystem-mcp-server", "/path/to/allowed/directory"]
    }
  }
}
```

### Verifying MCP Setup

After configuring, restart Claude and check:

```bash
claude
/mcp
```

This lists all connected MCP servers and their available tools.

---

## The 7 Core Files

Your knowledge base is anchored by 7 files in `1__knowledge/core/`. Never create an 8th.

| File | Purpose | Update Frequency |
|------|---------|------------------|
| `company.md` | Mission, values, vision | Quarterly |
| `product.md` | Features, pricing, specs | Quarterly |
| `team.md` | People, roles, structure | Weekly |
| `goals.md` | Current priorities, OKRs | Weekly |
| `customers.md` | Personas, case studies | Weekly |
| `financials.md` | Metrics, unit economics | Daily/Weekly |
| `operations.md` | Processes, workflows, SLAs | Daily/Weekly |

**Why 7?** Research shows 5-10 semantic units are optimal for retrieval. More files = diminishing returns.

---

## Available Agents

Use the Task tool with `subagent_type` parameter:

| Agent | Purpose | When to Use |
|-------|---------|-------------|
| `researcher` | Deep research, source verification | Complex questions, fact-finding |
| `writer` | Content creation, documentation | Blog posts, reports, documentation |
| `analyst` | Data analysis, metrics | Trends, patterns, quantitative questions |

Example:
```
Use the researcher agent to find information about [topic]
```

---

## Available Skills

Skills auto-activate based on trigger phrases:

| Skill | Triggers | Purpose |
|-------|----------|---------|
| onboarding | "onboard", "ingest", "import" | Process new content into knowledge base |
| update-memory | "update memory", "extract insights" | Extract learnings from transcripts |
| audit-knowledge | "audit", "what's missing" | Find gaps in your knowledge base |

---

## Customization

### Adding a New Agent

Create `.claude/agents/your-agent.md`:

```yaml
---
name: your-agent
description: When to invoke this agent. Include trigger keywords.
role: Functional Role
tools: Read, Grep, Glob
model: inherit
---

# Your Agent

## Expertise
What this agent is good at...

## Approach
How this agent works...
```

### Adding a New Skill

Create `.claude/skills/your-skill/SKILL.md`:

```yaml
---
name: your-skill
description: Trigger phrases and when to use this skill.
---

# Your Skill

## When to Use
Conditions for activation...

## Quick Workflow
1. Step one
2. Step two
3. Step three
```

### Adding a New Rule

Create `.claude/rules/your-rule.md`:

```yaml
---
globs:
  - "path/to/files/**/*.md"
description: What these rules enforce
---

# Your Rule

Standards that apply to matched files...
```

---

## Best Practices

### 1. Quantify Everything

```markdown
❌ "Performance improved"
✅ "Response time reduced from 45s to 32s (29% improvement)"
```

### 2. Mark Uncertainties

```markdown
When you don't know something:
- Revenue target: [NEED: confirm with finance]
- Launch date: Q1 2026 (tentative)
```

### 3. One Sentence Per Line

```markdown
This makes git diffs cleaner.
Each sentence on its own line.
Easier to track changes over time.
```

### 4. Use ISO Dates

```markdown
✅ 2025-01-15
❌ January 15, 2025
❌ 1/15/25
```

---

## Security

### Never Commit

- `.env` files
- API keys or credentials
- Customer data
- Large data files (>10MB)

### .gitignore Template

```gitignore
# Secrets
.env
*.pem
credentials.json

# Data
*.csv
*.xlsx
data/

# System
.DS_Store
*.log
```

---

## Git Workflow

```bash
git pull                    # Before starting
# (make changes)
git add .
git commit -m "What you changed: why it matters"
git push                    # End of session
```

Include co-author when Claude helps:
```
Co-Authored-By: Claude <noreply@anthropic.com>
```

---

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [PARA Method](https://fortelabs.com/blog/para/)
- [Building a Second Brain](https://www.buildingasecondbrain.com/)
- [MCP Protocol Specification](https://modelcontextprotocol.io/)

---

## License

MIT License - Use freely, modify as needed.

---

**Built with Claude Code** | Created {{DATE}}
