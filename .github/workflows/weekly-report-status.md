---
name: Weekly Report Status
description: Publish a concise weekly activity report for commits, issues, and pull requests.
on:
  schedule:
    - cron: "0 9 * * 1"
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
engine: copilot
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

Create a concise activity report for the previous seven full days ending at workflow start, using UTC for all dates and times.

Review repository activity during that window:

- Commits, including the total and a brief summary of notable changes.
- Issues opened or updated, including the total and a brief summary.
- Pull requests opened, merged, or updated, including the total and a brief summary.

Publish the report as one new issue using the `create-issue` safe output. The issue title must begin with `[weekly-report] `. Use `###` headings for the report sections and keep the report concise. State the UTC reporting window and workflow trigger in the report. Clearly state that no activity occurred when there were no qualifying commits, issues, or pull requests in the window; do not omit the issue in that case.