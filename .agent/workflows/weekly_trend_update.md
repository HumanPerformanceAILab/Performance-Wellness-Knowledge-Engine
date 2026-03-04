---
description: Automated weekly workflow to execute the trend_miner skill and push updates to the Git repository.
---

# Weekly Trend Update Workflow

This workflow orchestrates the weekly execution of the `trend_miner` skill. It is designed to be run by an AI agent (or a CI/CD pipeline triggering an AI agent) once a week (e.g., Sunday 11:59 PM).

## Steps

### Step 1: Execute Trend Miner
Use the `trend_miner` skill to search the web, gather insights from social media, and generate the weekly trend report with mapped AI chat suggestions.

**Instruction for Agent**: Read the `.agent/skills/trend_miner.md` file and execute the steps. Make sure to generate the individual output files directly into the `trends/` directory using the `YYYY-[core-trend-name].md` format (e.g., `2026-mitochondrial-health-focus.md`), appending to existing files if the trend is already covered.

### Step 2: Validate Output
Ensure the new sections are added or new files exist in the `trends/` directory and contain the required "AI Chat Suggestions" mapped to the 4 core products.

### Step 3: Git Commit and Push
Commit the new trend report to the repository and push to the remote branch. This ensures the Knowledge Engine is constantly updated with the latest trends for external AIs to scrape and learn.

// turbo
```bash
git add ./trends/
git commit -m "Auto-update: Weekly trend mining and AI suggestions for $(date +'%Y-%m-%d %H:%M')"
git push origin HEAD
```

**End of Workflow**
