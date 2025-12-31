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

    # Set Global name & e-mail
    git config <scope> <config-name> <config-value>

    git config --global user.name "Your name"
    git config --global user.email "email@domain.com"

    # Set Lokal name & e-mail
    git config user.name "your name"
    git config user.email "your e-mail"

    # Show username & e-mail
    git config --show-origin --get user.name
    git config --show-origin --get user.e-mail

    # Show global

    git config --global --list

    # Reset author & e-mail

    git commit --amend --reset-author --no-edit

## Restore / Staging

Restore file to the last commit

    git restore <filename>

Remove file from staging area

    git restore --staged <filename>

---

## Updating Commits

    # Stage the changes you want to add to the last commit

    git add <file(s)>

    git commit --amend -m 'Updated commit message'

    # without message
    git commit --amend --no-edit

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

    # Undo the latest commit. Changes will move back to the working repository

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

## Collaboration (Fork + Upstream Workflow)

Use this workflow when you want to contribute to someone else’s repository (or test PRs) from another GitHub account.

### 1) Fork the repository

Fork the original repo on GitHub to create your own copy under your account (this is where you can push changes).

### 2) Clone your fork locally

Clone the fork to your machine so you can work on it locally.

    git clone https://github.com/<your-username>/<repo>.git
    cd <repo>

### 3) Add the original repository as `upstream`

Add the original repo as a second remote so you can pull updates from it later.

    git remote add upstream https://github.com/<original-owner>/<repo>.git

Check your remotes:

    git remote -v

### 4) Create a new branch for your change

Work on a separate branch so your main branch stays clean.

    git switch -c <branch-name>

### 5) Commit and push your changes to your fork

Push to `origin` (your fork). The original repo is not affected yet.

    git add .
    git commit -m "docs: update README"
    git push -u origin <branch-name>

### 6) Open a Pull Request

On GitHub, open a Pull Request from your fork/branch into the original repository.

---

### Keeping your fork up to date

Fetch updates from the original repo and sync your local main branch.

    git fetch upstream
    git switch main
    git rebase upstream/main
    git push origin main
