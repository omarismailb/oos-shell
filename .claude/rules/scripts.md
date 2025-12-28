---
globs:
  - "3__scripts/**/*.py"
  - "3__scripts/**/*.sh"
  - "3__scripts/**/*.js"
  - "3__scripts/**/*.ts"
description: Rules for automation scripts and utilities
---

# Script Standards

Scripts in `3__scripts/` automate recurring tasks and data processing.

## Directory Organization

```
3__scripts/
├── data-processing/     ← CSV, JSON, data transformation
├── reports/             ← Report generation scripts
├── utilities/           ← Shared helper functions
└── automation/          ← Scheduled or triggered tasks
```

## Code Standards

### Python
- Python 3.10+ features allowed
- Type hints required for function signatures
- Docstrings for public functions (Google or NumPy style)
- Use `pathlib` for file paths, not `os.path`

### Shell Scripts
- Include shebang: `#!/bin/bash` or `#!/usr/bin/env bash`
- Use `set -euo pipefail` for safety
- Quote variables: `"${variable}"`

### All Languages
- Clear, descriptive function names
- Comments for non-obvious logic
- Handle errors gracefully with useful messages

## Documentation Requirements

Every script should have a header comment:

```python
"""
Script Name: analyze_data.py
Purpose: Process weekly metrics and generate summary report
Author: {{YOUR_NAME}}
Created: YYYY-MM-DD

Usage:
    python analyze_data.py input.csv --output report.md

Dependencies:
    - pandas >= 2.0
    - See requirements.txt in this directory
"""
```

## Data Handling

### NEVER Commit
- CSV/JSON data files (add to `.gitignore`)
- API keys or credentials
- Database connection strings
- Customer PII or sensitive data

### Safe Patterns
- Use environment variables for secrets: `os.getenv("API_KEY")`
- Read data from designated input directories
- Write output to designated output directories
- Log to files, not just stdout

## Dependencies

Each script directory should have:
- `requirements.txt` (Python)
- `package.json` (Node.js)
- README explaining setup and usage

## Error Handling

```python
# Good: Explicit error handling with useful message
try:
    data = load_csv(filepath)
except FileNotFoundError:
    logger.error(f"Input file not found: {filepath}")
    sys.exit(1)
except pd.errors.EmptyDataError:
    logger.error(f"Input file is empty: {filepath}")
    sys.exit(1)

# Bad: Silent failure or generic catch
try:
    data = load_csv(filepath)
except:
    pass  # ❌ Never do this
```

## Testing

- Include example usage in docstring
- Test with sample data before production runs
- Document expected input/output formats
- Add unit tests for critical functions

## Example Script Structure

```python
#!/usr/bin/env python3
"""
Weekly Report Generator

Generates a markdown report from metrics CSV.

Usage:
    python generate_report.py metrics.csv -o weekly_report.md
"""

import argparse
import logging
from pathlib import Path

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)


def parse_args() -> argparse.Namespace:
    """Parse command line arguments."""
    parser = argparse.ArgumentParser(description=__doc__)
    parser.add_argument("input", type=Path, help="Input CSV file")
    parser.add_argument("-o", "--output", type=Path, help="Output file")
    return parser.parse_args()


def main() -> None:
    """Main entry point."""
    args = parse_args()

    if not args.input.exists():
        logger.error(f"Input file not found: {args.input}")
        return

    # Process data...
    logger.info(f"Processing {args.input}")

    # Write output...
    logger.info(f"Report written to {args.output}")


if __name__ == "__main__":
    main()
```

## Anti-Patterns

❌ Hardcoded file paths (`/Users/john/data/file.csv`)
❌ Secrets in code (`api_key = "sk-1234..."`)
❌ No error handling (script crashes without explanation)
❌ No documentation (what does this script do?)
❌ Committing data files to git
❌ Print statements instead of proper logging
