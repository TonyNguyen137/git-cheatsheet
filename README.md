# Git cheatsheet

## Git status: untracked vs modified

### Untracked

**Untracked files** are files that **Git doesn’t know about yet**.

They exist in your project folder, but you **haven’t added them to Git**.

**Example:**  
You create a new file `notes.txt` → Git shows it as _untracked_.  
Once you run `git add notes.txt`, Git starts tracking it.

**Short version:**  
📌 _Untracked = new file, not versioned yet._

---

### Modified

**Modified files** are files that Git **already tracks**, but you **changed them since the last commit**.

Git sees the file has changes that are **not committed yet**.

**Example:**  
`index.html` is already in the repo → you edit it → Git shows it as _modified_.

**Short version:**  
📌 _Modified = already tracked, but changed._

## Staging Area (Index)

The **staging area** (also called the **index**) is a **preparation area for your next commit**.

Think of it like a “shopping cart”:

- Your **working directory** = where you edit files
- The **staging area** = what you _plan to commit_
- The **commit** = the saved snapshot in Git history

### Why it exists

It lets you choose **exactly what goes into the next commit**.

You can:

- stage only some files (or even parts of a file)
- keep other changes for a later commit

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

The Log Command

    git log
    git log --stat
    git log --oneline
    git log --all --graph

Examine Commits

    git show <commit-hash>

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
