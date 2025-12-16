# 📘 Git Mastery – Level 4
## Fetch, Pull, Push & Remote Management

---

## 📌 Purpose of Level 4

Level 4 explains how Git enables **team collaboration** through remotes.
This is where individual Git usage scales to **enterprise and CI/CD workflows**.

You will learn:
- What remotes really are
- Fetch vs pull (and why they are different)
- How pushing works internally
- How Git tracks remote branches
- How to diagnose sync issues safely

---

## 🧠 Mental Model Reminder

Remote repositories are just **other Git repositories**.
Nothing moves unless you explicitly run a command.

Local Repo ⇄ Remote Repo

---

# 1️⃣ git remote

### Purpose
Manage connections to remote repositories.

### Examples

```bash
git remote
```
Lists remote names configured for the repository.

```bash
git remote -v
```
Shows fetch and push URLs for each remote.

```bash
git remote add origin https://github.com/org/repo.git
```
Adds a remote named origin.

```bash
git remote set-url origin git@github.com:org/repo.git
```
Changes remote URL (commonly HTTPS to SSH).

```bash
git remote remove origin
```
Removes the remote reference.

---

# 2️⃣ git fetch

### Purpose
Downloads commits and references without changing your working branch.

### Key Insight
Fetch is always **safe**.

### Examples

```bash
git fetch
```
Fetches updates from the default remote.

```bash
git fetch origin
```
Fetches all branches from origin.

```bash
git fetch origin main
```
Fetches only the main branch.

```bash
git fetch --all
```
Fetches from all remotes.

```bash
git fetch --prune
```
Removes stale remote-tracking branches.

---

# 3️⃣ git pull

### Purpose
Fetches and integrates remote changes into the current branch.

### Internal Operation
git pull = git fetch + git merge (or rebase)

### Examples

```bash
git pull
```
Fetches and merges into the current branch.

```bash
git pull origin main
```
Explicitly pulls from origin/main.

```bash
git pull --rebase
```
Rebases local commits on top of fetched changes.

```bash
git pull --ff-only
```
Allows pull only if fast-forward is possible.

```bash
git pull --no-commit
```
Merges changes but waits for manual commit.

---

# 4️⃣ git push

### Purpose
Uploads local commits to a remote repository.

### Key Rule
You can only push commits that the remote branch does not already have.

### Examples

```bash
git push
```
Pushes current branch to its upstream.

```bash
git push origin main
```
Pushes main branch explicitly.

```bash
git push -u origin testbranch
```
Pushes branch and sets upstream.

```bash
git push --force-with-lease
```
Force-pushes safely by checking remote state.

```bash
git push --tags
```
Pushes all tags.

---

# 5️⃣ Upstream Branches

### Purpose
Defines which remote branch a local branch tracks.

### Examples

```bash
git branch -vv
```
Shows upstream branch and ahead/behind status.

```bash
git branch --set-upstream-to=origin/main
```
Manually sets upstream for current branch.

```bash
git status
```
Displays sync status with upstream.

---

# 6️⃣ Common Sync Scenarios

- Local ahead → push required
- Local behind → pull or rebase required
- Diverged → merge or rebase decision

---

# 7️⃣ Enterprise Best Practices

- Prefer `git fetch` before risky operations
- Avoid `git push --force` (use `--force-with-lease`)
- Protect main/master branches
- Use pull requests for merges
- Keep branches short-lived

---

## 🏁 Level 4 Completion Checklist

You are ready to proceed if you can:
- Explain fetch vs pull clearly
- Push safely with upstream tracking
- Diagnose ahead/behind states
- Understand how CI/CD sees your code

---

➡️ **Next: Level 5 – Stash, Cherry-pick & Advanced Daily Tools**
