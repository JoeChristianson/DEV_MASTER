# Developer SOP Library

## Index Table
| SOP #        | Title                                     | Category  | Frequency | Est. Time Savings | Total Monthly Time Saved |
|--------------|-------------------------------------------|-----------|-----------|-------------------|--------------------------|

| DEV-SOP-001  | Quick Local Branch Cleanup in Git  | Git Workflow  | ~4 per week | ~5 min | 1h 20m |

***

## DEV-SOP-001: Quick Local Branch Cleanup in Git
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

