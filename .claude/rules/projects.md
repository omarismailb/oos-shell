---
globs:
  - "2__projects/**/*.md"
  - "2__projects/*.md"
description: Rules for project files - bounded efforts with clear outcomes
---

# Project File Standards

Projects are bounded efforts with specific outcomes and end dates. They differ from Areas (ongoing responsibilities) in that projects finish.

## Required Sections

Every project file should include:

### 1. Project Header
```markdown
# Project Name

**Status**: [Active / On Hold / Completed / Cancelled]
**Owner**: {{NAME}}
**Started**: YYYY-MM-DD
**Target Completion**: YYYY-MM-DD
```

### 2. Objective
One clear sentence describing what success looks like.

### 3. Key Results / Milestones
Measurable outcomes that define completion:
```markdown
## Key Results

- [ ] KR1: [Measurable outcome]
- [ ] KR2: [Measurable outcome]
- [x] KR3: [Completed outcome] ✓ YYYY-MM-DD
```

### 4. Progress Log
Chronological updates (most recent first):
```markdown
## Progress Log

### YYYY-MM-DD
- Completed: [What was done]
- Next: [What's planned]
- Blockers: [Any issues] or "None"
```

## Status Definitions

| Status | Meaning |
|--------|---------|
| **Active** | Work happening this week/sprint |
| **On Hold** | Paused, will resume (note why and expected restart) |
| **Completed** | All key results achieved, ready to archive |
| **Cancelled** | Stopped, won't resume (note why for learning) |

## Linking

- Link to relevant knowledge files: `See [topic](../1__knowledge/core/topic.md)`
- Link to related projects if dependencies exist
- Reference frameworks used: `Using [Framework Name](../1__knowledge/frameworks/framework.md)`

## Archiving

When a project completes:
1. Update status to "Completed"
2. Add completion date and summary
3. Move to `9__archive/projects/YYYY/`
4. Extract learnings to `1__knowledge/memory/learnings/`

## Example Project File

```markdown
# Website Redesign

**Status**: Active
**Owner**: Jane Smith
**Started**: 2025-01-15
**Target Completion**: 2025-03-31

## Objective

Redesign company website to improve conversion rate from 2.1% to 3.5%.

## Key Results

- [ ] KR1: New design approved by stakeholders
- [ ] KR2: Development complete and tested
- [ ] KR3: Launched with A/B testing framework
- [ ] KR4: 30-day post-launch conversion rate ≥ 3.5%

## Progress Log

### 2025-02-01
- Completed: Wireframes for all 5 main pages
- Next: Stakeholder review meeting scheduled for Feb 5
- Blockers: None

### 2025-01-20
- Completed: Competitive analysis of 10 sites
- Next: Start wireframing
- Blockers: Waiting on brand guidelines update
```

## Anti-Patterns

❌ Projects without end dates (those are Areas)
❌ Vague objectives ("make things better")
❌ No measurable key results
❌ Stale progress logs (update at least weekly for active projects)
❌ Projects left in "Active" when actually on hold
