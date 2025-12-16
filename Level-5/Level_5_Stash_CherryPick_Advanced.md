# 📘 Git Mastery – Level 5
## Stash, Cherry-pick & Advanced Daily Tools

---

## 📌 Purpose of Level 5

Level 5 focuses on **day-to-day power tools** that senior engineers use
to stay productive without breaking history or workflows.

This level teaches you how to:
- Pause and resume work safely
- Move commits across branches precisely
- Apply fixes without full merges
- Work efficiently in real-world scenarios

---

## 🧠 Mental Model Reminder

At this level, Git is about **manipulating commits and working state safely**,
not just creating history.

---

# 1️⃣ git stash

### Purpose
Temporarily saves uncommitted changes so you can switch context safely.

### Key Insight
Stash works like a **temporary shelf**, not a commit.

---

### Examples

```bash
git stash
```
Saves tracked file changes and cleans the working directory.

```bash
git stash push -m "WIP login feature"
```
Creates a named stash for easier identification.

```bash
git stash list
```
Lists all stashed entries.

```bash
git stash show
```
Shows summary of the latest stash.

```bash
git stash pop
```
Applies the latest stash and removes it from stash list.

```bash
git stash apply
```
Applies stash but keeps it for reuse.

```bash
git stash drop stash@{0}
```
Deletes a specific stash entry.

```bash
git stash clear
```
Deletes all stashes (irreversible).

```bash
git stash push -u
```
Stashes untracked files as well.

---

# 2️⃣ git cherry-pick

### Purpose
Applies a specific commit from another branch onto the current branch.

### Key Insight
Cherry-pick copies a commit — it does NOT move it.

---

### Examples

```bash
git cherry-pick 4034bd8
```
Applies a single commit onto the current branch.

```bash
git cherry-pick commit1 commit2
```
Applies multiple commits sequentially.

```bash
git cherry-pick commit1..commit2
```
Applies a range of commits.

```bash
git cherry-pick --continue
```
Continues cherry-pick after conflict resolution.

```bash
git cherry-pick --abort
```
Cancels cherry-pick and restores original state.

```bash
git cherry-pick -n 4034bd8
```
Applies changes without committing immediately.

---

# 3️⃣ git clean

### Purpose
Removes untracked files and directories.

### ⚠️ Warning
This command permanently deletes files.

---

### Examples

```bash
git clean -n
```
Shows what would be deleted (dry run).

```bash
git clean -f
```
Deletes untracked files.

```bash
git clean -fd
```
Deletes untracked files and directories.

```bash
git clean -fx
```
Deletes ignored files as well.

```bash
git clean -i
```
Interactive clean mode.

---

# 4️⃣ git restore (modern undo tool)

### Purpose
Restores file content from index or commit.

---

### Examples

```bash
git restore file.txt
```
Discards local changes in a file.

```bash
git restore --staged file.txt
```
Unstages a file.

```bash
git restore --source=HEAD~1 file.txt
```
Restores file from previous commit.

---

# 5️⃣ Advanced Daily Patterns

### Hotfix from main to feature
- Cherry-pick fix commit
- Avoid full merge

### Context switch during debugging
- Stash changes
- Switch branch
- Resume work

### Clean build environment
- git clean + git reset

---

## 🏁 Level 5 Completion Checklist

You are ready to proceed if you can:
- Pause and resume work safely
- Apply fixes across branches precisely
- Clean working directory confidently
- Avoid accidental data loss

---

➡️ **Next: Level 6 – Interactive Rebase, Bisect & History Surgery**
