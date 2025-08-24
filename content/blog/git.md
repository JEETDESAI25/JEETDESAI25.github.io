---
title: "Git"
description: "Some useful Git commands."
tags: ["git", "version-control", "developer-tools"]
showToc: true
showReadingTime: true
weight: 1
---

Your commit message was wrong. You accidentally committed to the wrong branch. Your teammate's merge broke everything and you need to find exactly when. Here are the Git commands that can help.

## Fix Your Mistakes

### Wrong commit message

```bash
git commit --amend -m "Correct message"
```

Changes your last commit message. Only works if you haven't pushed yet.

### Undo your last commit

```bash
git reset --soft HEAD~1
```

Removes the commit but keeps your changes staged. Your work is safe.

### Wrong branch

```bash
git log --oneline -1        # Copy the commit hash
git reset --hard HEAD~1     # Remove from current branch
git checkout correct-branch
git cherry-pick abc123      # Apply to correct branch
```

Moves your commit to where it belongs.

### Committed too early

```bash
# Make more changes
git add .
git commit --amend --no-edit
```

Adds new changes to your previous commit.

## Clean Your History

### Squash messy commits

```bash
git rebase -i HEAD~3
```

Opens editor. Change `pick` to `squash` for commits you want to combine.

### Save work without committing

```bash
git stash                   # Save current changes
git stash pop              # Get them back
git stash list             # See all stashes
git stash drop             # Delete a stash
```

Perfect when you need to switch branches quickly.

### Find "lost" commits

```bash
git reflog
```

Shows everything you've done. Find your lost commit hash and `git checkout abc123`.

### Compare anything

```bash
git diff HEAD~2            # Changes in last 2 commits
git diff main..feature     # Changes between branches
git diff --name-only       # Just file names
git diff --stat           # Summary stats
```

## Keep Things Tidy

### Clean up untracked files

```bash
git clean -n               # Preview what will be deleted
git clean -fd              # Actually delete files and directories
```

Removes files that aren't in Git. Use `-n` first to be safe.

### Better branch management

```bash
git branch -d feature      # Safe delete (only if merged)
git branch -D feature      # Force delete
git remote prune origin    # Remove stale remote branches
```

### See what happened

```bash
git log --oneline --graph  # Visual commit history
git log --since="2 weeks ago" --author="yourname"
git show HEAD              # Full details of last commit
```

## Collaboration

### Undo public commits safely

```bash
git revert abc123          # Creates new commit that undoes abc123
```

Never use `reset` on published commits. `revert` is safe for shared history.

### Apply commits from other branches

```bash
git cherry-pick abc123
```

Copy fixes between branches without merging everything.

### Clean merge

```bash
git merge --squash feature # All changes as single commit
git commit -m "Add feature"
```

Keeps main branch history clean.

---
