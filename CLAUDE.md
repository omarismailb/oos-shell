# {{PROJECT_NAME}} - Claude Code Configuration

**Purpose**: Your AI-powered second brain for personal knowledge management, business operations, and automated workflows.
**Last Updated**: {{DATE}}

---

## Quick Context

This is a knowledge management system using the PARA method (Projects, Areas, Resources, Archive) with Claude Code integration for AI-assisted operations.

**Key Files to Reference**:
- `.claude/docs/SYSTEM-CONTEXT.md` - Core operating principles
- `.claude/docs/README.md` - Complete memory system documentation
- `1__knowledge/core/` - Your core knowledge files

---

## Directory Structure

```
{{PROJECT_NAME}}/
├── .claude/                      ← Claude Code configuration
│   ├── agents/                   ← Specialized AI agents
│   ├── skills/                   ← Auto-activating skills
│   ├── rules/                    ← Glob-pattern activated rules
│   └── docs/                     ← System documentation
│
├── 0__inbox/                     ← Unprocessed items (triage here)
├── 1__knowledge/                 ← AREAS (ongoing responsibilities)
│   ├── core/                     ← Core knowledge files
│   ├── frameworks/               ← Strategic tools & mental models
│   ├── templates/                ← Reusable templates
│   └── memory/                   ← Chronicles & learnings
│       ├── chronicles/           ← Weekly/monthly logs
│       └── learnings/            ← Lessons learned, knowledge gaps
│
├── 2__projects/                  ← PROJECTS (bounded efforts with deadlines)
├── 3__scripts/                   ← Automation scripts
└── 9__archive/                   ← ARCHIVE (completed/inactive items)
```

---

## Core Principles

### Token Efficiency
- Target: 40-70% context window utilization
- Load only relevant files per task
- Keep core files focused and concise

### The Core Files Pattern
<!-- CUSTOMIZE: Define your own core knowledge files based on your domain -->
<!-- Examples: company.md, projects.md, goals.md, contacts.md, processes.md -->
<!-- Recommendation: Start with 3-5 files, expand as needed (max 7-10) -->

Your core files in `1__knowledge/core/` should cover:
1. **identity.md** - Who you are, your mission, values
2. **goals.md** - Current priorities and objectives
3. **projects.md** - Active projects and their status
4. **contacts.md** - Key people and relationships
5. **processes.md** - Your workflows and SOPs

### Update Cadences
| Type | Frequency | Examples |
|------|-----------|----------|
| Static | Monthly/Quarterly | identity.md, values |
| Dynamic | Weekly | goals.md, projects.md |
| Operational | Daily/Weekly | contacts.md, processes.md |

---

## Communication Standards

### Professional Objectivity
- Data-driven: quantify where possible
- Honest about challenges with solutions
- No unnecessary superlatives
- Direct guidance > vague suggestions

### Quantification Examples
❌ "Made good progress"
✅ "Completed 4/6 milestones (67%), 2 remaining for next week"

❌ "Things are going well"
✅ "Project on track: 3 deliverables shipped, 1 blocked on external dependency"

---

## Git Workflow

### Standard Pattern
```bash
git pull                    # Before starting
# (make changes)
git add .
git commit -m "Clear message explaining why"
git push                    # End of session
```

### Commit Message Format
```
[Action] [What changed]: [Why it matters]

Co-Authored-By: Claude <noreply@anthropic.com>
```

---

## Security

### Never Commit
- `.env` files and environment variables
- API keys, credentials, secrets
- Personal data exports
- Large data files (>10MB)

### Safe to Commit
- All markdown files
- Scripts (code, not data)
- Claude agents and skills
- Non-sensitive configuration

---

## Quick Commands

<!-- CUSTOMIZE: Add your own skills/commands as you create them -->
| Command | Purpose |
|---------|---------|
| `/onboard` | Ingest new context (transcripts, docs, etc.) |
| `/update-memory` | Extract insights and update knowledge files |
| `/audit-knowledge` | Find gaps in your knowledge base |

---

For detailed operating principles, see `.claude/docs/SYSTEM-CONTEXT.md`
