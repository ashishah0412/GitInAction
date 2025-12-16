# 📘 Git Mastery – Level 7
## Git Hooks, Submodules & Enterprise GitOps Patterns

---

## 📌 Purpose of Level 7

Level 7 connects **Git internals to enterprise-grade delivery models**.
This is where Git stops being a developer tool and becomes a **governance,
automation, and platform backbone**.

At this level, you will learn:
- How Git Hooks enforce quality and security
- How and when to use Git Submodules
- How Git underpins GitOps and CI/CD
- Enterprise patterns used in regulated environments (BFSI, large orgs)

---

## 🧠 Mental Model Reminder

At enterprise scale:
- Git = **source of truth**
- Commits = **change contracts**
- Branches = **control points**
- Pipelines = **automated enforcers**

---

# 1️⃣ Git Hooks

### What are Git Hooks?
Scripts that run **automatically** at specific points in the Git lifecycle.

They live in:
```
.git/hooks/
```

Hooks are **local by default** (not versioned unless managed explicitly).

---

## Types of Hooks

### Client-side Hooks
- `pre-commit`
- `commit-msg`
- `pre-push`

### Server-side Hooks
- `pre-receive`
- `update`
- `post-receive`

---

## 1.1 pre-commit Hook

### Purpose
Run checks before a commit is created.

### Examples
- Linting
- Formatting
- Secret scanning
- Unit tests (lightweight)

```bash
#!/bin/sh
npm test || exit 1
```

Prevents bad commits from entering history.

---

## 1.2 commit-msg Hook

### Purpose
Enforce commit message standards.

### Example
```bash
#!/bin/sh
grep -E "^(feat|fix|chore|docs):" "$1" || exit 1
```

Used heavily in enterprises for traceability.

---

## 1.3 pre-push Hook

### Purpose
Final safety net before code leaves developer machine.

### Examples
- Run tests
- Block force pushes
- Check branch naming

---

# 2️⃣ Git Submodules

### What is a Submodule?
A Git repository **embedded inside another Git repository** as a reference.

The parent repo stores:
- Repo URL
- Exact commit hash

---

## When to Use Submodules

✅ Shared libraries  
✅ Platform components  
❌ Fast-moving app code  
❌ Beginners or small teams  

---

## Submodule Commands

```bash
git submodule add https://github.com/org/lib.git libs/lib
```
Adds a submodule.

```bash
git submodule init
```
Initializes local submodule config.

```bash
git submodule update
```
Checks out the recorded commit.

```bash
git submodule update --remote
```
Pulls latest commit from submodule branch.

```bash
git clone --recurse-submodules <repo>
```
Clones repo including submodules.

---

## Submodule Pitfalls

- Detached HEAD inside submodule
- Forgetting to commit updated submodule pointer
- CI failures due to missing init/update

---

# 3️⃣ GitOps Fundamentals

### What is GitOps?
An operational model where:
> **Git is the single source of truth for system state**

Used heavily with:
- Kubernetes
- Terraform
- Cloud platforms

---

## GitOps Flow

```
Developer Commit
     ↓
Git Repository (desired state)
     ↓
CI/CD / GitOps Controller
     ↓
Actual Infrastructure / App
```

---

## GitOps Key Principles

- Declarative definitions
- Pull-based deployments
- Immutable history
- Auditable changes
- Easy rollback via Git

---

# 4️⃣ Branching Strategies (Enterprise)

## GitFlow
- main
- develop
- feature/*
- release/*
- hotfix/*

Used in release-heavy enterprises.

---

## Trunk-Based Development
- Short-lived branches
- Frequent merges to main
- Heavy automation

Preferred in high-velocity teams.

---

## Environment Branching (Anti-pattern)
- dev / qa / prod branches

Often discouraged due to drift risk.

---

# 5️⃣ Git + CI/CD Integration

### How Pipelines Use Git

- Commits trigger pipelines
- Branch rules control promotion
- Tags trigger releases
- PRs enforce quality gates

---

## Common Enterprise Controls

- Protected branches
- Mandatory reviews
- Required checks
- Signed commits
- Audit logs

---

# 6️⃣ Git + Terraform / IaC (GitOps Example)

### Pattern
- Terraform code in Git
- PR = infrastructure change request
- Plan on PR
- Apply on approval
- Rollback via Git revert

---

# 7️⃣ Security & Compliance Considerations

- Commit signing (GPG)
- Secret scanning
- Least-privilege repo access
- Immutable audit trails
- Change traceability

---

## 🏁 Level 7 Completion Checklist

You are ready if you can:
- Explain how Git enforces governance
- Design a GitOps workflow
- Decide between submodules and monorepo
- Explain why Git is central to DevSecOps

---

🎉 **Congratulations!**
You have completed **Git Mastery Levels 0–7**.

Next (optional advanced topics):
- Monorepos vs Multirepos
- Large repo performance tuning
- Partial clone & sparse checkout
- Git at hyperscale (Google, Meta models)
