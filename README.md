# Git cheatsheet

## Configuration

    git config <scope> <config-name> <config-value>

    git config --global user.name "Your name"
    git config --global user.email "email@domain.com"

### show global

    git config --global --list

## Restore / Staging

Restore file to the last commit

    git restore <filename>

Remove file from staging area

    git restore --staged <filename>

---

## Commit

Update commit, but keep the commit message

    git commit --amend --no-edit

---

## Inspect commits

Shows the most recent commit including: the commit message, author & timestamp, a list of changed files, with status like D (Deleted), M (Modified), A (Added)

    git show --name-status HEAD

See only deleted files from last commit

    git show --diff-filter=D --name-only HEAD

---

## Reset (delete last commit)

Delete commit  
Man befindet sich im letzten commit + modified Daten

    git reset HEAD~1

---

## Branches

Create branch

    git branch <branch-name>

Switch branch

    git switch <branch-name>

Switch branch (legacy)

    git checkout <branch-name>

Create and switch to the new branch

    git switch -c <branch-name>
    # or
    git checkout -b <branch-name>

Show all branches

    git branch

Safe Delete (won’t delete if branch has unmerged work). Git will warn you if the branch hasn’t been merged.

    git branch -d <branch-name>

Force Delete (even if unmerged)

    git branch -D <branch-name>

---

## Merge

Merge branch into current branch  
Switch to `main` first if you want to merge into main

    git merge <branch-name>

Cancel merge

    git merge --abort
