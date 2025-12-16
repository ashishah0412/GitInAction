# 📘 Git Mastery – Level 3
## Reset, Revert, Reflog & Recovery

---

## 📌 Purpose of Level 3

Level 3 focuses on **understanding mistakes and recovery in Git**.
This is the level where Git stops feeling dangerous and starts feeling safe.

At this level, you will learn:
- How Git moves pointers backward and forward
- The difference between undoing history vs adding corrective history
- How Git remembers *everything* you did
- How to recover commits that seem lost

---

## 🧠 Mental Model Reminder

Git rarely deletes data.
Most “loss” in Git is simply **moving pointers**.

```
HEAD → branch → commit
```

Recovery usually means **moving the pointer back**.

---

# 1️⃣ git reset

### Purpose
Moves the current branch pointer to another commit and optionally updates the index and working directory.

### Reset Modes
- `--soft`   → move HEAD only
- `--mixed`  → move HEAD + index (default)
- `--hard`   → move HEAD + index + working directory

---

### Examples

```bash
git reset --soft HEAD~1
```
Moves branch pointer back one commit but keeps all changes staged.

```bash
git reset HEAD~1
```
Moves branch back and unstages changes, keeping files intact.

```bash
git reset --hard HEAD~1
```
Completely removes last commit and all file changes (dangerous).

```bash
git reset --hard origin/main
```
Forces local branch to match remote exactly.

```bash
git reset file.txt
```
Unstages a file without touching its content.

---

## ⚠️ Important Warning
Never use `git reset --hard` on a **shared branch** unless you are 100% sure.

---

# 2️⃣ git revert

### Purpose
Undo a commit by creating a **new commit** that reverses changes.

### Key Difference from Reset
- Reset rewrites history
- Revert preserves history

---

### Examples

```bash
git revert HEAD
```
Creates a new commit that undoes the last commit.

```bash
git revert d072128
```
Reverts a specific commit by hash.

```bash
git revert HEAD~2..HEAD
```
Reverts a range of commits.

```bash
git revert --no-commit HEAD
```
Applies revert changes but allows manual editing before commit.

```bash
git revert -m 1 <merge-commit>
```
Reverts a merge commit by selecting the mainline parent.

---

# 3️⃣ git reflog

### Purpose
Shows a log of **all movements of HEAD**, including deleted or rewritten commits.

### Why reflog is critical
It is Git’s **transaction log**.

---

### Examples

```bash
git reflog
```
Shows all recent HEAD movements.

```bash
git reflog --oneline
```
Compact view of HEAD history.

```bash
git reflog main
```
Shows branch-specific movements.

```bash
git reset --hard HEAD@{2}
```
Recovers repository state from reflog entry.

```bash
git checkout HEAD@{1}
```
Checks out a previous HEAD position.

---

# 4️⃣ Recovery Scenarios

### Scenario 1: Accidentally deleted a commit
- Use `git reflog`
- Identify commit hash
- Reset or checkout to it

### Scenario 2: Bad reset
- Reflog shows previous HEAD
- Reset back safely

### Scenario 3: Lost branch
- Reflog still remembers branch tip
- Recreate branch from commit

---

# 5️⃣ Decision Matrix

| Situation | Command |
|--------|--------|
| Undo local commit | git reset |
| Undo pushed commit | git revert |
| Recover lost work | git reflog |
| Fix staging mistake | git reset file |

---

## 🏁 Level 3 Completion Checklist

You are ready to proceed if you can:
- Explain reset modes confidently
- Choose reset vs revert correctly
- Recover commits using reflog
- Stay calm after mistakes 😄

---

➡️ **Next: Level 4 – Fetch, Pull, Push & Remote Management**
