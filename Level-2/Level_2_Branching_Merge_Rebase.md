# 📘 Git Mastery – Level 2
## Branching, Checkout, Merge & Rebase

---

## 📌 Purpose of Level 2

Level 2 explains how Git enables **parallel development** using branches.
This is where Git becomes a **graph-based change management system**, not just version control.

You will learn:
- How branches really work
- How to switch safely between branches
- How Git combines histories
- When and when NOT to rebase

---

## 🧠 Mental Model Reminder

Branches are **lightweight pointers** to commits.

branch → commit → parent commit(s)

---

# 1️⃣ git branch

### Purpose
Create, list, and delete branch pointers.

### Examples

```bash
git branch
```
Lists all local branches and marks the current one.

```bash
git branch testbranch
```
Creates a new branch pointing to the current commit.

```bash
git branch -a
```
Lists local and remote-tracking branches.

```bash
git branch -vv
```
Shows branch pointers with upstream tracking information.

```bash
git branch -d testbranch
```
Deletes a branch that has already been merged.

---

# 2️⃣ git checkout

### Purpose
Switch branches or restore files (legacy command).

### Examples

```bash
git checkout testbranch
```
Moves HEAD to testbranch and updates the working tree.

```bash
git checkout -b feature/login
```
Creates and switches to a new branch.

```bash
git checkout main -- file.txt
```
Restores a file from main branch.

```bash
git checkout HEAD~1
```
Checks out a previous commit in detached HEAD state.

---

# 3️⃣ git switch

### Purpose
Modern, safer alternative to checkout for branch switching.

### Examples

```bash
git switch main
```
Switches to the main branch.

```bash
git switch -c feature/api
```
Creates and switches to a new branch.

```bash
git switch -
```
Switches back to the previously used branch.

---

# 4️⃣ git merge

### Purpose
Integrates changes from one branch into another.

### Examples

```bash
git merge testbranch
```
Merges testbranch into the current branch.

```bash
git merge --no-ff feature/login
```
Forces a merge commit for visibility.

```bash
git merge --abort
```
Cancels a merge in progress.

```bash
git merge --squash feature/login
```
Combines all feature commits into one.

---

# 5️⃣ git rebase

### Purpose
Rewrites history by replaying commits on top of another base.

⚠️ Never rebase shared branches.

### Examples

```bash
git rebase main
```
Rebases current branch onto main.

```bash
git rebase -i HEAD~3
```
Interactively edits last three commits.

```bash
git rebase --continue
```
Continues after conflict resolution.

```bash
git rebase --abort
```
Cancels the rebase and restores state.

---

## 🔄 Merge vs Rebase

| Merge | Rebase |
|----|----|
| Preserves history | Rewrites history |
| Safe for shared branches | Unsafe for shared branches |
| Shows true branching | Produces linear history |

---

## 🏁 Level 2 Completion

You are ready for Level 3 when you can:
- Predict pointer movement
- Resolve conflicts confidently
- Choose merge vs rebase correctly

➡️ Next: **Level 3 – Reset, Revert, Reflog & Recovery**
