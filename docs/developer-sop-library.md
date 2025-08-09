# Developer SOP Library

## Index Table
| SOP #        | Title                                     | Category  | Frequency | Est. Time Savings | Total Monthly Time Saved |
|--------------|-------------------------------------------|-----------|-----------|-------------------|--------------------------|

| DEV-SOP-001  | Local Branch Cleanup (Safe + Aggressive)  | Git Workflow  | ~5 per week | ~7 min | 2h 20m |

***

## DEV-SOP-001: Local Branch Cleanup (Safe + Aggressive)
**Category:** Git Workflow  
**Trigger:** My local repo has many stale branches (some merged, some tracking deleted remotes) and I want to clean them quickly and safely.  

**Steps:**  
1. Fetch and prune remotes: `git fetch --prune`.
2. List branches fully merged into main: `git branch --merged main`.
3. Delete merged locals (keep main): `git branch --merged main | grep -v "\*" | grep -v " main$" | xargs -r git branch -d`.
4. Prune remote-tracking refs: `git remote prune origin`.
5. Optionally remove locals with gone upstreams (aggressive): `git branch -vv | awk '/: gone]/{print $1}' | xargs -r git branch -D`.

**Notes & Optimizations:**  
- Replace `main` with your default branch name.
- Use the last step only if you’re sure the branches are safe to drop (no unpushed commits).
- Map cleanup to a shell alias for one-shot execution.

**Estimated Time Savings:** ~7 minutes per occurrence  
**Frequency:** ~5 per week  
**Automation Opportunity:** Yes — provide a `git-clean-branches` script/alias that runs the entire flow.  
**Status:** Finalized
**Category:** Git Workflow  
**Trigger:** I have multiple old local branches that are already merged and I want to remove them quickly.  

**Steps:**  
1. Run `git fetch --prune` to update remote tracking branches.
2. Run `git branch --merged main` to list merged branches.
3. Delete merged branches with `git branch --merged main | grep -v "main" | xargs git branch -d`.
4. Optionally, run `git remote prune origin` to clean up remote-tracking references.

**Notes & Optimizations:**  
- Make sure you have no unmerged work in branches before deleting.
- Replace `main` with your default branch name if different.

**Estimated Time Savings:** ~5 minutes per occurrence  
**Frequency:** ~4 per week  
**Automation Opportunity:** Yes — can be wrapped in a single shell alias or script.  
**Status:** Finalized

