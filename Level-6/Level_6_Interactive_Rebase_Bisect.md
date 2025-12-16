# 📘 Git Mastery – Level 6
## Interactive Rebase, Bisect & History Surgery

---

## 📌 Purpose of Level 6

Level 6 takes you into **advanced Git surgery**.
This is where Git becomes a precision tool for:
- Cleaning commit history
- Debugging regressions
- Rewriting mistakes safely
- Working like a senior maintainer or release engineer

At this level, you stop fearing history manipulation and start **controlling it deliberately**.

---

## 🧠 Mental Model Reminder

History is a **directed acyclic graph (DAG)**.
Advanced Git commands:
- Rewrite parts of the graph
- Replay commits
- Walk the graph to find problems

Nothing is random — everything is pointer movement + object reuse.

---

# 1️⃣ git rebase -i (Interactive Rebase)

### Purpose
Rewrite, clean, and organize commit history **before sharing it**.

### When to use
- Before merging a feature branch
- To squash noisy commits
- To fix commit messages
- To reorder commits logically

⚠️ Never use interactive rebase on **public/shared branches**.

---

### Examples

```bash
git rebase -i HEAD~3
```
Opens interactive editor for last 3 commits to edit, squash, or reorder.

```bash
git rebase -i main
```
Rewrites current branch commits on top of main interactively.

```bash
git rebase -i --rebase-merges
```
Preserves merge commits during interactive rebase.

```bash
git rebase -i --autosquash
```
Automatically squashes commits marked as fixup/squash.

```bash
git rebase -i --root
```
Rewrites history starting from the very first commit.

---

### Common Interactive Actions

| Action | Meaning |
|-----|-------|
| pick | Keep commit as-is |
| reword | Change commit message |
| edit | Modify commit content |
| squash | Combine with previous commit |
| fixup | Combine, discard message |
| drop | Remove commit |

---

# 2️⃣ git commit --fixup / --squash

### Purpose
Prepare commits for clean autosquash rebasing.

---

### Examples

```bash
git commit --fixup 4034bd8
```
Creates a fixup commit targeting a specific commit.

```bash
git commit --squash 4034bd8
```
Creates a squash commit with message preserved.

```bash
git rebase -i --autosquash main
```
Automatically reorders and squashes fixup commits.

---

# 3️⃣ git bisect

### Purpose
Find the exact commit that introduced a bug using binary search.

### Key Insight
Git bisect turns debugging into a **logarithmic search problem**.

---

### Examples

```bash
git bisect start
```
Starts bisect session.

```bash
git bisect bad
```
Marks current commit as bad.

```bash
git bisect good v1.0.0
```
Marks a known good commit or tag.

```bash
git bisect run ./test.sh
```
Automates bisect using a test script.

```bash
git bisect reset
```
Ends bisect session and returns to original state.

---

# 4️⃣ History Surgery Scenarios

### Scenario 1: Squash noisy commits
- Interactive rebase
- Squash/fixup commits
- Force-push safely (if private branch)

### Scenario 2: Fix wrong commit message
- `reword` during rebase
- Or `git commit --amend`

### Scenario 3: Remove sensitive data
- Drop commit
- Rewrite history
- Rotate secrets immediately

---

# 5️⃣ Safety Guidelines (Very Important)

- Never rebase shared branches
- Always `git fetch` before surgery
- Use `--force-with-lease`, never `--force`
- Keep backups via tags if unsure
- Reflog is your safety net

---

## 🏁 Level 6 Completion Checklist

You are ready to proceed if you can:
- Clean a feature branch before merge
- Use autosquash confidently
- Bisect a regression in minutes
- Explain why rebasing rewrites hashes

---

➡️ **Next: Level 7 – Git Hooks, Submodules & Enterprise GitOps Patterns**
