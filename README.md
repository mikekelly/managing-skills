# managing-skills

An agent skill for installing, finding, updating, and managing other agent skills via the [`npx skills`](https://github.com/vercel-labs/skills) CLI.

## What it does

When a user asks their coding agent to install, find, or update a skill, this skill handles it by running the appropriate `npx skills` command. It:

- **Installs** skills from GitHub repos, GitLab, or local paths
- **Finds** skills by keyword search
- **Checks** installed skills for available updates
- **Updates** all installed skills to their latest versions
- **Lists** currently installed skills

Defaults to project-level install targeting the current agent type. Supports global installs and multi-agent targeting when requested.

## Install

```bash
npx skills add mikekelly/managing-skills --yes -g --all
```
