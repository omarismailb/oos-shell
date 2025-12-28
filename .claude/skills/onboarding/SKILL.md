---
name: onboarding
description: Ingest new context and populate knowledge files. Use when user mentions "onboard", "ingest", "import context", "add to knowledge base", "process this transcript", or shares raw content to be organized.
---

# Onboarding Skill

## When to Use This Skill

Activate when the user wants to:
- Import content from external sources (transcripts, PDFs, Notion exports)
- Populate their knowledge base with new information
- Process raw meeting notes or documents
- Set up their second brain for the first time

## Quick Workflow

1. **Identify Input Type**
   - Transcript (meeting notes, call recordings)
   - PDF document
   - Notion export (markdown)
   - Raw text/notes
   - URL to fetch

2. **Read the Content**
   - Use Read tool for local files
   - Use WebFetch for URLs
   - Ask user to paste if no file path provided

3. **Extract Key Information**
   - People mentioned → `1__knowledge/core/team.md`
   - Projects/initiatives → `2__projects/`
   - Processes/workflows → `1__knowledge/core/operations.md`
   - Company info → `1__knowledge/core/company.md`
   - Customer insights → `1__knowledge/core/customers.md`
   - Financial data → `1__knowledge/core/financials.md`
   - Priorities/goals → `1__knowledge/core/rocks.md`
   - Product details → `1__knowledge/core/product.md`

4. **Update Knowledge Files**
   - Append to existing sections (don't overwrite)
   - Use consistent formatting
   - Add `(as of {{DATE}})` for temporal data
   - Mark uncertainties with `[NEED: clarification]`

5. **Report What Was Added**
   - Summarize changes per file
   - Flag any conflicts with existing data
   - List items that need user confirmation

## Input Types

### Transcripts
Best for extracting:
- Action items and owners
- Decisions made
- People and their roles
- Project updates

### PDFs
Best for extracting:
- Formal documentation
- Contracts and agreements
- Reports and analyses

### Notion Exports
Best for extracting:
- Structured knowledge
- Existing documentation
- Team wikis

### Raw Notes
Best for extracting:
- Quick captures
- Meeting summaries
- Ideas and brainstorms

## Output Format

After processing, provide:

```markdown
## Onboarding Summary

### Files Updated
- `1__knowledge/core/team.md`: Added [X] team members
- `1__knowledge/core/operations.md`: Added [Y] processes
- `2__projects/[project-name].md`: Created new project file

### Key Extractions
- **People**: [List of names and roles identified]
- **Projects**: [List of projects mentioned]
- **Decisions**: [Key decisions captured]
- **Action Items**: [Tasks with owners]

### Needs Clarification
- [NEED: What is [Person]'s exact role?]
- [NEED: Is [Project] still active?]

### Conflicts Found
- Existing: [What was already documented]
- New: [What the new content says]
- Resolution needed: [What user should decide]
```

## Quality Checklist

Before completing onboarding:
- [ ] All people added to team.md with roles
- [ ] Projects have dedicated files or sections
- [ ] Temporal data has dates
- [ ] Uncertainties marked with `[NEED: ...]`
- [ ] No duplicate entries created
- [ ] Consistent formatting maintained
- [ ] Summary provided to user

## Example Transformation

### Input (Raw Transcript Snippet)
```
"...so Sarah will be leading the Q1 launch, she's our new Head of Marketing.
We're targeting $50K MRR by March. John mentioned the API integration is
blocking us, needs to be done by next Friday..."
```

### Output (Extracted to Knowledge Files)

**team.md addition:**
```markdown
### Sarah [Last Name TBD]
- **Role**: Head of Marketing
- **Joined**: [NEED: start date]
- **Owns**: Q1 Launch
```

**rocks.md addition:**
```markdown
### Q1 Launch
- **Owner**: Sarah (Head of Marketing)
- **Target**: $50K MRR by March
- **Status**: In Progress
```

**Action item captured:**
```markdown
- [ ] Complete API integration → John → [Next Friday date]
  - Blocker for: Q1 Launch
```

## First-Time Setup

For users setting up their second brain for the first time:

1. **Start with company.md**
   - Mission statement
   - Core values
   - Vision

2. **Then team.md**
   - Who's involved
   - Their roles
   - Reporting structure

3. **Then active projects**
   - What you're working on now
   - Key milestones
   - Owners and timelines

4. **Build from there**
   - Add context as it comes in
   - Don't try to document everything at once
   - Focus on what's actively needed
