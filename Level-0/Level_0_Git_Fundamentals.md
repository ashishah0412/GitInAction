# 📘 Git Mastery – Level 0
## Git Fundamentals & Internal Mental Model

---

## 📌 Purpose of Level 0

Level 0 is about **understanding Git before using Git**.

Most Git mistakes in enterprises (lost commits, broken branches, force-push disasters) happen because people **memorize commands without understanding what Git is actually doing internally**.

This level focuses on:
- How Git **stores data**
- How Git **tracks changes**
- What really happens when you run Git commands
- How Git differs from traditional version control systems

---

## 🧠 What Git Is (Conceptually)

### Git is:
- A **distributed version control system**
- A **content-addressable file system**
- A **snapshot-based system**, not diff-based
- A **local-first tool**, not server-first

### Git is NOT:
- A central database
- A file-diff tracker
- A cloud-only tool
- A linear history system

---

## 🏗️ Git’s Core Architecture

Git internally works with **four conceptual areas**:

Working Directory → Staging Area (Index) → Local Repository → Remote Repository

---

## 📂 Working Directory
The actual files you edit. Changes here are not tracked until explicitly staged.

---

## 📦 Staging Area (Index)
A pre-commit buffer allowing precise control over what goes into a commit.

---

## 🗄️ Local Repository (.git)
Stores full history, commits, branches, and metadata locally.

---

## 🌍 Remote Repository
A synchronization point like GitHub or GitLab, not the master truth.

---

## 🧱 Git Objects

### Blob
Stores file content only.

### Tree
Represents directory structure.

### Commit
Snapshot of the project with metadata and parent references.

### Tag
Human-readable pointer to a commit, often for releases.

---

## 🧠 Content-Addressable Storage
Git uses SHA hashes to uniquely identify content, ensuring integrity and deduplication.

---

## 🎯 HEAD
Pointer to the current commit, usually via a branch reference.

---

## 🌿 Branches
Branches are lightweight pointers to commits, not copies of code.

---

## 🔄 Conceptual Git Workflow

Edit → Stage → Commit → Push (optional)

---

## ❌ Common Misconceptions
- Commit is a diff ❌ → Commit is a snapshot ✅
- Branch is a copy ❌ → Branch is a pointer ✅

---

## 🏁 Level 0 Completion

You are ready to proceed if you understand Git’s internal model, objects, and workflow.

---

➡️ Next: **Level 1 – Essential Git Commands**
