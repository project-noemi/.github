# AGENTS.md — project-noemi/.github

The organization-level `.github` repository for Project NoéMI. Today it holds only the organization profile README (`profile/README.md`).

## 🪪 Machine identity (mandatory)

Every agent (Codex, Claude Code, Gemini, Cursor, or any other) opens pull requests only as the `noemi-agent` machine identity:

- Open PRs with `bash scripts/agent-gh.sh pr create ...`, or `node scripts/agent-pr.js` where `gh` is unavailable, with `AGENT_GH_EXPECTED_LOGIN=noemi-agent` set so the wrapper refuses any other account. Those scripts live in the [project-noemi/agents](https://github.com/project-noemi/agents) framework repository, not in this one.
- Never open an agent PR with a human's `gh` login or token, including the reviewing human's own. GitHub blocks a PR's author from approving it, so a human-authored agent PR cannot get human review.
- Commit as `noemi-agent <311935378+noemi-agent@users.noreply.github.com>`. Commit metadata does not set PR authorship; the token that opens the PR does.
- If no `noemi-agent` token resolves, stop and say so. Do not fall back to human credentials.
- Approving and merging stay human-only; the machine identity does neither.

Details: [docs/MACHINE_IDENTITY.md](https://github.com/project-noemi/agents/blob/develop/docs/MACHINE_IDENTITY.md) and [`mcp-protocols/github.md`](https://github.com/project-noemi/agents/blob/develop/mcp-protocols/github.md) §6 (PR Authorship) in project-noemi/agents.

## What this repository is, and what it is not

- `profile/README.md` is the public Project NoéMI organization profile shown on github.com/project-noemi. Edit it only for profile content changes.
- Root files named like community health files (`CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `SECURITY.md`, `SUPPORT.md`, `FUNDING.yml`, issue and PR templates) would become defaults for every project-noemi repository that lacks its own copy. Do not add one here without the owners deciding it should apply org-wide.
- `AGENTS.md`, `CLAUDE.md`, and `GEMINI.md` are not community health files. GitHub does not pass them on to other repositories, so these files govern agent work in this repository only. Each project-noemi repository keeps its own `AGENTS.md`.

## Conventions

- There is no build or test tooling here; changes are Markdown only.
- Commits are signed off (`git commit -s`).
- `main` is the default and only branch; open PRs against `main`.
