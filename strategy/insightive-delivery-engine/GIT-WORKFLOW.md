# Git Workflow For Insightive Agency Agents

**Purpose:** Maintain Insightive's version of `agency-agents` while regularly pulling improvements from the original public repo.

## Remote Layout

Use this layout:

```bash
upstream = https://github.com/msitarzewski/agency-agents.git
origin   = Insightive-owned GitHub repo or fork
```

`upstream` is read-only for us. `origin` is where Insightive branches, commits, pull requests, and releases live.

## Branches

| Branch | Purpose |
|---|---|
| `main` | Insightive's stable base branch. Keep it close to upstream unless a deliberate Insightive change is accepted. |
| `codex/insightive-delivery-team` | Working branch for the Insightive delivery engine layer. |
| `insightive/*` | Future long-lived Insightive feature branches if needed. |

## Initial Setup

If starting from a fresh clone:

```bash
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents
git remote rename origin upstream
git remote add origin <INSIGHTIVE_REPO_URL>
git switch -c codex/insightive-delivery-team
```

If the Insightive GitHub repo is created as a fork, GitHub may configure `origin` automatically. In that case, make sure the original repo is still available as `upstream`.

## Push Insightive Work

```bash
git push -u origin codex/insightive-delivery-team
```

Open a pull request from `codex/insightive-delivery-team` into Insightive's `main` when the delivery-engine docs are ready.

## Pull Updates From Upstream

Run this regularly:

```bash
git fetch upstream
git switch main
git merge upstream/main
git push origin main
```

Then refresh the Insightive delivery branch:

```bash
git switch codex/insightive-delivery-team
git merge main
```

Use merge by default. Rebase only if the branch is private and no one else is using it.

## Conflict Rule

When upstream changes conflict with Insightive files:

- Preserve upstream agent catalog changes unless they break Insightive usage.
- Keep Insightive-specific operating doctrine under `strategy/insightive-delivery-engine/`.
- Avoid modifying source role files unless the change should apply to all future Insightive use.
- Resolve conflicts in small commits with clear messages.

## Update Cadence

Recommended:

- Weekly: `git fetch upstream` and review changes.
- Biweekly: merge upstream `main` into Insightive `main`.
- Before major Insightive changes: update from upstream first.
- Before productionizing the hosted engine: tag a known-good Insightive baseline.

## Safety Checks

After each upstream sync:

```bash
scripts/check-divisions.sh
git status --short
```

If source agent files changed, run the repo's conversion/lint checks before pushing any generated integration updates.
