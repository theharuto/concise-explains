<details>
  <summary> Undone explains</summary>
  - git is distributed version control system
- distribued : teams can work independently on each isolated features with having the full copy of the source code with each one of them, there is no single point of failure
- git provides good branching features
- git has many commands to work with such as
  - git status = checks the current status of the local repo
  - git init = initialize the local repo
  - git add = add the mentioned files to the staging area where they can be considered for the next commit
  - git commit -m "<message>" = commit the changes from the staging area with a message mentioned, this typically saves the work from the staging as a snapshot that can be sent to remote repo
  - git push origin <branch-name> = pushes the commited changes from the local repo to remote repo
  - git remote -v = shows the remote repo where the commits may be sent
  - git remote add origin <url> = adds the remote origin
  - git config --global user.name <username>
  - git config --global user.email <email> // can remove the --global to set the things only for the current local repo
  - git fetch = fetches the remote branches and changes to the local, origin/main, origin/feature = specifies that it is remote repo branches
  - git merge <branch-name> = merges two branches, specifically merges the mentioned branch with current branch when the command is called - can cause conflicts
  - git pull = fetches and merges the remote branches or branch that is mentioned with the command - can cause conflicts
  - git stash = saves the changes temporarily when we need to change the branch when we don't want to commit the undone work
  - git apply = pops the changes from the stash stack

familiar with just theory 
  - git reset = goes back to the previous commit
  - git revert = goes back to the previous commit by creating a new commit
just know the words exists  but no knowledge on that
 - cherry pick
 - editing the history
 - rebasing and also editing with it
</details>

# 📘 GIT REVISION NOTES (My Words)

---

## What is Git

* Git is a **distributed version control system**
* Distributed means:

  * Every developer has a **full copy of the code + full history**
  * Work can be done **offline**
  * No single point of failure (server down ≠ work stops)
* GitHub / GitLab / Bitbucket are **hosting platforms**, not Git itself

👉 Git works using **snapshots**, not file differences.

---

## Core Git Idea (Very Important)

* Git stores:

  * **Snapshots of files**
  * Not line-by-line diffs
* Every change saved in Git is stored as a **commit**
* A **commit is immutable** (cannot be changed)
* **Branches are just pointers to commits**, not copies of code

👉 Creating a branch is cheap because it is just creating a pointer.

---

## Git Repository Basics

### `git init`

* Initializes a Git repository
* Creates `.git` folder
* This folder contains:

  * commit history
  * branches
  * config
  * object database

---

### `git status`

* Shows:

  * which files are modified
  * which files are staged
  * current branch
  * whether branch is ahead/behind remote

---

## Working Directory → Staging → Commit

### `git add`

* Adds file **content** to staging area (index)
* Staging area stores a **snapshot of the file at that moment**
* If file is changed again after `git add`, Git remembers **old staged version**

Example:

```text
edit file → git add → edit again → commit
(commit will contain old version)
```

---

### `git commit -m "message"`

* Creates a **local commit**
* Commit contains:

  * snapshot of files
  * parent commit reference
  * author + message
* Commit does **not** go to remote automatically
* Commits exist **independent of branches**

👉 Commits are local first, always.

---

## Branching in Git

* Branch = pointer to a commit
* `HEAD` = pointer to current branch

Example:

```text
main → C1 → C2
feature → C2
```

* Switching branches = moving `HEAD`
* Deleting a branch does **not** delete commits (if reachable)

---

## Remote Repositories

### `git remote add origin <url>`

* Adds a remote repo
* `origin` is just a **name**, not special

### `git remote -v`

* Shows fetch and push URLs

---

## Push, Fetch, Pull (Very Important Difference)

### `git push origin branch`

* Pushes local commits to remote
* Updates remote branch pointer
* Can fail if remote has new commits

---

### `git fetch`

* Fetches changes from remote
* Updates:

  * `origin/main`
  * `origin/feature`
* Does **not** change local branches
* Safe operation

👉 `git fetch` = read-only

---

### `git pull`

* `git pull = git fetch + git merge (or rebase)`
* Can create merge commits
* Can cause conflicts
* Can mess history

👉 **Never blindly use git pull**

---

## Merging Branches

### `git merge branch-name`

* Merges mentioned branch into current branch
* Creates a **merge commit**
* Merge commit has **two parents**
* History is preserved

Used when:

* You want full history
* Shared branches (main, develop)

---

## Rebase (History Rewriting)

* Rebase means:

  * Replaying commits on top of another base
  * Commit hashes change
* Produces **clean, linear history**

⚠️ **Danger**

* Never rebase shared branches
* Rewriting public history causes conflicts for others

Golden rule:

> Rebase only your own local commits

---

## Reset vs Revert (Interview Favorite)

### `git reset`

* Moves branch pointer backward
* Rewrites history
* Types:

  * `--soft` → keep staged changes
  * `--mixed` → unstage changes
  * `--hard` → delete changes

⚠️ Never use reset on shared branches

---

### `git revert`

* Creates a **new commit**
* Undoes changes safely
* Used in production

👉 Reset = dangerous
👉 Revert = safe

---

## Stash (Temporary Save)

### `git stash`

* Temporarily saves uncommitted changes
* Useful when switching branches
* Stored as a stack of commits

### `git stash apply`

* Applies stash but keeps it

### `git stash pop`

* Applies stash and removes it

⚠️ Stash is **not long-term storage**

---

## Cherry-pick

* Takes **one specific commit**
* Applies it to another branch
* Creates a new commit

Used for:

* Hotfixes
* Picking one fix without merging full branch

---

## Git Fetch vs Pull (One-Line Interview Answer)

* `git fetch` → safe, updates remote references
* `git pull` → dangerous, modifies local branch

---

## Why Git is Fast and Powerful

* Commits are immutable
* Branches are pointers
* History is a graph (DAG)
* Git allows recovery using reflog

---

## Real-World Git Best Practices

* Never commit `target/` or build files
* Write meaningful commit messages
* Rebase local commits before pushing
* Do not rewrite shared history
* Always understand what branch you are on

---

## Interview-Ready Summary (Say This)

> Git stores snapshots, not diffs.
> Commits are immutable, branches are pointers.
> Fetch is safe, pull is not.
> Rebase rewrites history, merge preserves it.
> Reset is dangerous, revert is safe.

---

## Self-Check Before Interview

I should be able to explain:

* What a commit contains
* Why branching is cheap
* Why rebasing shared branches is dangerous
* Difference between fetch, pull, merge
* When to use revert vs reset
