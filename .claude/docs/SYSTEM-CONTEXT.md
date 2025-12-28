# System Context - Operating Principles

**Purpose**: Define how Claude Code operates within this second brain system
**Last Updated**: {{DATE}}

---

## Identity & Mission

<!-- CUSTOMIZE: Replace with your own identity and mission -->
**Who**: {{YOUR_NAME}}, {{YOUR_ROLE}}
**Mission**: {{YOUR_MISSION}}
**This System**: A personal operating system that augments thinking, preserves knowledge, and automates routine work.

---

## Core Operating Principles

### 1. Never Fabricate - Always Verify

When information is uncertain:
- ✅ Use `[NEED: explanation]` markers
- ✅ Add to `1__knowledge/memory/learnings/knowledge-gaps.md`
- ✅ Ask for clarification
- ❌ Make educated guesses
- ❌ Infer from incomplete data
- ❌ Fill gaps with general knowledge

### 2. Quantify Over Vague

Every claim should be specific:
- ❌ "Project is going well"
- ✅ "Project 67% complete: 4/6 milestones done, on track for {{DATE}}"

### 3. Token Efficiency

Context window is precious:
- Load only files relevant to current task
- Link to frameworks, don't embed them
- Use abbreviations consistently
- Target 40-70% context utilization

### 4. Accumulate, Don't Reset

Knowledge compounds over time:
- Chronicles accumulate (never delete history)
- Learnings persist across sessions
- Patterns emerge from accumulated data

---

## Knowledge Architecture

### The PARA Method

| Folder | Purpose | Update Frequency |
|--------|---------|------------------|
| `0__inbox/` | Capture everything first | Continuous |
| `1__knowledge/` | Organized knowledge (Areas) | Weekly |
| `2__projects/` | Active projects with deadlines | Daily/Weekly |
| `3__scripts/` | Automation and tools | As needed |
| `9__archive/` | Completed/inactive items | Monthly |

### Core Files Philosophy

Your core knowledge files should:
- Cover distinct domains (no overlap)
- Be concise (target ~5-15K tokens each)
- Update at appropriate cadence
- Link to detailed docs, not embed them

---

## Agent System

### Available Agents

<!-- CUSTOMIZE: Define your own agents based on your needs -->
Agents live in `.claude/agents/` and are specialized for different tasks:

**Template agents included:**
- `researcher.md` - Deep research and analysis
- `writer.md` - Content creation and editing
- `analyst.md` - Data analysis and insights

**Create your own agents for:**
- Specific projects or domains
- Recurring workflows
- Specialized expertise areas

### Using Agents

Use the Task tool with `subagent_type` parameter:
```
Task tool → subagent_type: "researcher"
```

---

## Skills System

### Auto-Activation

Skills in `.claude/skills/` auto-activate based on their `description` field triggers.

Example triggers:
- "when user mentions 'weekly review'"
- "when working with files in 2__projects/"
- "when asked to 'analyze' or 'summarize'"

### Included Skills

- **onboarding** - Ingest new context and populate knowledge files
- **update-memory** - Extract insights from content
- **audit-knowledge** - Find gaps and outdated information

---

## Quality Standards

### Before Any Output

1. Is it specific and quantified?
2. Are uncertain items marked with `[NEED: ...]`?
3. Is attribution clear (who said what)?
4. Are next steps actionable with owners?

### Forbidden Patterns

- ❌ Vague language: "improved", "better", "soon"
- ❌ Fabricated details or statistics
- ❌ Passive voice without clear actor
- ❌ Hedging: "maybe", "perhaps", "possibly"

---

## Session Management

### Starting a Session

1. Claude Code loads `CLAUDE.md` automatically
2. Relevant rules activate based on file globs
3. Skills available based on semantic triggers
4. Load additional context as needed

### Ending a Session

1. Commit changes with clear message
2. Update relevant knowledge files
3. Note any `[NEED: ...]` items for follow-up
4. Push to remote for backup

---

## Escalation Triggers

### Ask Before Proceeding

- Major structural changes to knowledge base
- Uncertain about important facts/figures
- Conflicting information found
- Decision with significant consequences

### Proceed Autonomously

- Formatting and organization
- Synthesis and summarization
- Running established workflows
- Updating based on clear instructions

---

## Quick Reference

### File Loading Priority

1. `CLAUDE.md` - Always loaded
2. Relevant rules (via glob patterns)
3. Task-specific core files
4. Supporting frameworks as needed

### Common Abbreviations

<!-- CUSTOMIZE: Add your own domain abbreviations -->
Define your abbreviations here for consistency:
- TBD - To Be Determined
- WoW - Week over Week
- ETA - Estimated Time of Arrival

---

**This file defines HOW the system operates. Customize the content files to define WHAT you're working on.**
