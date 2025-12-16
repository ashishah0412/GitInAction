# 📘 Git Mastery – Level 1
## Essential Git Commands (Beginner → Practitioner)

---

## 📌 Purpose of Level 1

Level 1 introduces the **essential Git commands** that every developer, architect, and DevOps engineer uses daily.

At this level, you will:
- Translate Git theory (Level 0) into **hands-on usage**
- Understand **what each command does internally**
- Learn **safe and correct usage patterns**
- Avoid common beginner mistakes

---

## 🧠 Mental Model Reminder (from Level 0)

Working Directory → Staging Area → Local Repository → Remote Repository

---

# 1️⃣ git init

### Purpose
Initializes a new Git repository by creating a `.git` directory.

### Examples

```bash
git init
```
Initializes Git in the current directory.

```bash
git init my-repo
```
Creates and initializes a new repository folder.

```bash
git init --initial-branch=main
```
Sets `main` as the default branch.

---

# 2️⃣ git clone

### Purpose
Creates a local copy of a remote repository.

### Examples

```bash
git clone https://github.com/org/app.git
```
Clones repository using HTTPS.

```bash
git clone git@github.com:org/app.git
```
Clones repository using SSH.

```bash
git clone --depth 1 https://github.com/org/app.git
```
Creates a shallow clone for CI/CD.

---

# 3️⃣ git status

### Purpose
Shows current repository state.

### Examples

```bash
git status
```
Displays full status.

```bash
git status -s
```
Displays short status.

```bash
git status --branch
```
Shows branch info.

---

# 4️⃣ git add

### Purpose
Stages changes for commit.

### Examples

```bash
git add file.txt
```
Stages a file.

```bash
git add .
```
Stages all changes.

```bash
git add -p
```
Stages selected hunks interactively.

---

# 5️⃣ git commit

### Purpose
Creates a snapshot of staged changes.

### Examples

```bash
git commit -m "Initial commit"
```
Commits staged changes.

```bash
git commit --amend
```
Modifies last commit.

```bash
git commit -am "Quick fix"
```
Stages and commits tracked files.

---

# 6️⃣ git log

### Purpose
Views commit history.

### Examples

```bash
git log
```
Shows commit history.

```bash
git log --oneline
```
Compact history view.

```bash
git log --graph
```
Graphical history view.

```bash
git branch -vv
```
-vv (very verbose), Show all local branches, which commit they point to, and which remote branch (if any) they are tracking — plus whether they’re ahead or behind.

---

# 7️⃣ git diff

### Purpose
Shows changes between states.

### Examples

```bash
git diff
```
Unstaged changes.

```bash
git diff --staged
```
Staged changes.

```bash
git diff HEAD
```
Working tree vs last commit.

---

# 8️⃣ git rm

### Purpose
Removes files from Git tracking.

### Examples

```bash
git rm file.txt
```
Deletes tracked file.

```bash
git rm --cached file.txt
```
Untracks file but keeps locally.

```bash
git rm -r folder/
```
Removes directory recursively.

---

# 9️⃣ git mv

### Purpose
Moves or renames files.

### Examples

```bash
git mv old.txt new.txt
```
Renames file.

```bash
git mv file.txt src/
```
Moves file.

```bash
git mv -n old new
```
Dry-run move.

---

## 🏁 Level 1 Completion

You are ready for Level 2 once you can use these commands confidently.

➡️ Next: **Level 2 – Branching and Merging**
