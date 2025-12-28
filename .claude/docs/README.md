# Claude Code Memory System

This directory contains the configuration and documentation for your Claude Code-powered second brain.

## Directory Structure

```
.claude/
├── docs/                    ← You are here
│   ├── README.md           ← This file
│   └── SYSTEM-CONTEXT.md   ← Operating principles
│
├── agents/                  ← Specialized AI agents
│   ├── researcher.md       ← Deep research tasks
│   ├── writer.md           ← Content creation
│   └── analyst.md          ← Data analysis
│
├── skills/                  ← Auto-activating skills
│   ├── onboarding/         ← Context ingestion
│   ├── update-memory/      ← Knowledge extraction
│   └── audit-knowledge/    ← Gap analysis
│
└── rules/                   ← Glob-pattern rules
    ├── markdown-general.md ← All .md files
    ├── projects.md         ← 2__projects/ files
    └── scripts.md          ← 3__scripts/ files
```

## How It Works

### 1. Automatic Loading

When you start Claude Code in this directory:
1. `CLAUDE.md` loads automatically (project instructions)
2. Rules activate based on file patterns you're working with
3. Skills are available via semantic triggers or `/skill-name`

### 2. Agents

Agents are specialized personas for different tasks. Use them via:
```
Task tool → subagent_type: "agent-name"
```

Each agent has:
- **Role**: What they specialize in
- **Tools**: Which tools they can use
- **Context**: What knowledge they load

### 3. Skills

Skills are reusable workflows. They activate when:
- You use a trigger phrase (e.g., "let's do a weekly review")
- You invoke directly (e.g., `/onboarding`)
- Context matches their description

### 4. Rules

Rules apply formatting and behavior standards based on file patterns:
- `**/*.md` → General markdown rules
- `2__projects/**` → Project-specific rules
- `3__scripts/**/*.py` → Python code standards

## Customization

### Adding an Agent

Create `.claude/agents/your-agent.md`:

```yaml
---
name: your-agent
description: When to use this agent and what it does
role: The Agent's Role
tools: Read, Grep, Glob, Task
model: inherit
---

# Your Agent Name

## Expertise
What this agent specializes in...

## Approach
How this agent works...

## Context to Load
Which files this agent needs...
```

### Adding a Skill

Create `.claude/skills/your-skill/SKILL.md`:

```yaml
---
name: your-skill
description: Trigger phrases and when to auto-invoke
---

# Your Skill Name

## When to Use
Conditions that trigger this skill...

## Workflow
1. Step one
2. Step two
3. Step three

## Output Format
What the skill produces...
```

### Adding a Rule

Create `.claude/rules/your-rule.md`:

```yaml
---
globs:
  - "pattern/**/*.md"
  - "**/specific-file.md"
description: When this rule applies
---

# Rule Name

## Standards
What to enforce...

## Examples
Good vs bad patterns...
```

## Best Practices

### Keep Context Focused
- Don't load all files for every task
- Link to detailed docs instead of embedding
- Use agents for specialized knowledge

### Maintain Your Knowledge Base
- Process inbox items weekly
- Update core files when things change
- Archive completed projects
- Document learnings and gaps

### Use Semantic Triggers
- Skills activate on natural language
- Name things descriptively
- Include trigger phrases in descriptions

## Troubleshooting

### Skill Not Activating
- Check the `description` field has trigger phrases
- Try invoking directly with `/skill-name`
- Verify SKILL.md is in correct location

### Agent Not Working
- Verify frontmatter format is correct
- Check `tools` field lists needed tools
- Ensure `model` is valid (inherit, sonnet, opus, haiku)

### Rules Not Applying
- Check glob patterns match your files
- Verify frontmatter YAML is valid
- Rules only apply to matching file paths

## Resources

- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [PARA Method](https://fortelabs.com/blog/para/)
- [Building a Second Brain](https://www.buildingasecondbrain.com/)
