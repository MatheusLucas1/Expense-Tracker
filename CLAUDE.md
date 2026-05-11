# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a CLI expense tracker application (spec from https://roadmap.sh/projects/expense-tracker). The repository currently contains only a README with requirements — no implementation exists yet. The language and tooling are open choices.

## Functional Requirements

Core commands the CLI must support:

```
expense-tracker add --description "Lunch" --amount 20
expense-tracker update --id 1 --description "Lunch" --amount 25
expense-tracker delete --id 2
expense-tracker list
expense-tracker summary
expense-tracker summary --month 8
```

Extended features (optional):
- Expense categories with filtering by category
- Monthly budget with a warning when exceeded
- CSV export

## Design Constraints

- Data must persist to a local file (JSON or CSV are both acceptable)
- Error handling is required for: negative amounts, non-existent IDs, invalid input
- Use a CLI argument parsing library appropriate for the chosen language (e.g. `argparse` for Python, `commander` for Node.js)
- Use functions/modules to keep the code testable

## Expected Output Format

```
$ expense-tracker list
# ID  Date       Description  Amount
# 1   2024-08-06  Lunch        $20
# 2   2024-08-06  Dinner       $10

$ expense-tracker summary
# Total expenses: $30

$ expense-tracker summary --month 8
# Total expenses for August: $20
```

IDs are auto-incremented integers assigned at creation time.
