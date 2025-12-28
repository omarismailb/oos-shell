---
globs:
  - "**/*.md"
description: General markdown standards for all documentation files in the knowledge base
---

# Markdown Standards

When editing any markdown file in this knowledge base, follow these principles.

## Quantification Over Vagueness

Be specific with data. Avoid subjective descriptors without supporting metrics.

❌ "Performance improved"
✅ "Response time reduced from 45s to 32s (29% improvement)"

❌ "Customer satisfaction is good"
✅ "NPS: 72 (+5 vs last month), 94% positive sentiment"

## Structure

- Use headers hierarchically (H1 → H2 → H3, never skip levels)
- Tables for comparative data
- Bullet lists for unordered items
- Numbered lists for sequences or steps

## Token Efficiency

- Use consistent abbreviations where appropriate
- Link to other files instead of duplicating content
- Remove redundant phrases: "In order to" → "To"

## Formatting

- One sentence per line (easier diffs in version control)
- Blank line between sections
- Code blocks with language specifier (```python, ```bash)
- Use callouts sparingly: `> **Note:**`

## File Organization

- Keep files focused on a single topic
- Split large files at natural boundaries
- Archive completed projects to `9__archive/`
- Follow PARA method: Projects, Areas, Resources, Archive

## Temporal Data

- Include dates for dynamic content: `(as of {{DATE}})`
- Use ISO format: `YYYY-MM-DD`
- Note update cadence in file header if applicable

## Uncertainty Markers

When information is incomplete or needs verification:
- Use `[NEED: explanation of what's missing]` markers
- Add uncertain items to a tracking system for follow-up
- Never guess metrics or decisions—mark them explicitly

## Examples

### Good Header Structure
```markdown
# Main Topic

## Section One

### Subsection A

### Subsection B

## Section Two
```

### Good Table Format
```markdown
| Metric | Current | Target | Status |
|--------|---------|--------|--------|
| Response Time | 28s | 30s | ✅ |
| Error Rate | 2.1% | 2.0% | ⚠️ |
```

### Good Uncertainty Marker
```markdown
- Revenue target: [NEED: confirm with finance team]
- Launch date: Q1 2026 (tentative, pending board approval)
```
