# Git: An Underlying Conceptual Guide

This document summarizes the core concepts of Git, helping developers move beyond memorizing commands to understanding the underlying database structure and mechanics, enabling them to navigate complex scenarios like rebase and history manipulation.

## 1. Git Fundamentals: The Database and the Commit

Git is fundamentally a **database**, and the basic unit of this database is the **commit**. 

Git is a distributed, content-addressable object database where the fundamental unit of versioned history is the commit, and no single repository is inherently central.

### What is a Commit?
A commit is a complete **snapshot** (a photograph) of your entire project at a specific moment in time. It records the entire state of every file, not just the changes you made.

Each commit contains three crucial pieces of information:
1.  A pointer to the **complete snapshot** of the project state.
2.  **Metadata**: Who created it, when it was created, and the commit message.
3.  A pointer to the **parent commit** (the commit that came directly before it).

Commits point **backwards**—children know their parents, but parents never know their future children.

## 2. Project History Structure: The DAG

When commits are chained together, they form the project's history.

### Directed Acyclic Graph (DAG)
The structure of Git history is formally known as a **Directed Acyclic Graph**.

*   **Graph**: Consists of nodes (commits) and connections (the links between them). This structure captures every branch, merge, and decision ever made by a developer.
*   **Directed**: Relationships only flow one way; children point to parents, never the reverse.
*   **Acyclic**: There are no loops; it is impossible to create a cycle in the history (e.g., no commit can be its own grandparent).

Because every commit holds a complete snapshot, Git allows you to jump to **any point** in this graph and see the project exactly as it existed at that time.

### Origin and Merges
The **very first commit** is special as it has no parent; it is the origin point of your project history. When merging branches, you create commits that point to **two parents**.

## 3. Navigating History: Branches and HEAD

Git uses simple pointers to navigate the complex DAG structure.

### Branches (Sticky Notes)
A branch is simply a **pointer** (like a sticky note) that contains only one piece of information: the **hash of a commit**.

*   Branches are **labels** stuck onto different commits. The commits themselves are unaware of what branches exist.
*   Creating a branch is **instantaneous** because Git is only placing a new sticky note, not copying the codebase.
*   When you commit while on a branch, Git creates the new commit, points it back to the previous commit, and then moves the branch's sticky note forward to the new commit.
*   The `main` branch is not special; it is simply another sticky note agreed upon by convention as the primary line of work.

### HEAD: Your Current Location
**HEAD** is Git's pointer for tracking your current location.

*   Usually, HEAD points **at a branch** (e.g., when you are on `main`, HEAD points to `main`, and `main` points to a commit).
*   Running `git checkout <branch_name>` simply moves the HEAD pointer to point at the new branch.

### Detached HEAD State
This state occurs when HEAD points directly to a specific **raw commit hash** instead of pointing to a branch.

*   **Risk**: You can still commit changes in this state, but because no branch is following along, those new commits are **orphaned** when you switch back to a branch.
*   Orphaned commits are floating in space and will eventually be cleaned up by Git's **garbage collection**. Git warns about this because any new commits won't be saved unless a branch is created to hold them.

## 4. The Three Areas of Git (The Layers)

Understanding where your code resides is key to manipulating history safely. Git has three distinct areas:

1.  **Working Directory**: The actual files on your disk that you see and edit.
2.  **Staging Area (or Index)**: A waiting room used to prepare exactly what content will go into your next commit. Running `git add` moves changes from the Working Directory into the Staging Area.
3.  **Repository**: The database of commits; this is the **permanent history**. Running `git commit` takes everything from the Staging Area and creates a permanent commit in the Repository.

## 5. History Manipulation: Checkout, Reset, and Revert

These commands manipulate the pointers and the three layers differently.

### A. `git checkout` (The Safe Explorer)
The job of `checkout` is to **move HEAD**.

*   **Pointers Moved**: Only HEAD.
*   **Layers Affected**: Working directory updates to match the target commit snapshot.
*   **History Effect**: **Non-destructive**; history and branches are untouched.
*   **Use Case**: Safely looking around history or switching branches.

### B. `git reset` (The Branch Mover)
`reset` moves a branch to a specified commit. Commits ahead of the new branch location are orphaned but still exist in the database.

| Mode | Branch Movement | Staging Area | Working Directory | Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **`--soft`** | Moves the branch to the target commit. | Unchanged (Undone changes appear staged). | Unchanged. | Combining multiple commits into one. |
| **`--mixed`** (Default) | Moves the branch to the target commit. | Reset to match the target commit. | Changes still exist in files, but are now **unstaged**. | Restaging committed work differently. |
| **`--hard`** | Moves the branch to the target commit. | Reset. | Reset (Uncommitted work is permanently **gone** from your disk). | Completely abandoning work and starting fresh. |

### C. `git revert` (The Corrective History Writer)
`revert` creates a **new commit** that performs the opposite action of an old commit.

*   **Action**: If commit C added 50 lines, revert creates commit D that removes those 50 lines.
*   **History Effect**: **History is preserved**; the original commit still exists.
*   **Safety**: Safe to use on shared history.
*   **Use Case**: Necessary to undo something that has already been **pushed and shared**, as you cannot rewrite shared history.

## 6. Rebasing: Rewriting Local History

**Rebase** takes a set of commits and replays them on top of a new base, which results in history being rewritten.

### The Rebase Process
1.  A commit's identity (its hash) depends on its content, metadata, and its parent pointer. Git **cannot move commits**.
2.  Rebase looks at an existing commit (B), calculates the changes it introduced, and then creates a **brand new commit** (B1) with those same changes, but pointing to a new parent.
3.  The old commits (B and C) are left behind and become **orphaned**, eventually to be garbage collected.
4.  The branch pointer is moved to point to the new set of commits (C1).

### The Trade-Off
Rebasing creates a **linear and clean** history, which is often described as choosing a "clean story over the messy truth".

> ⚠️ **Critical Rule**: **Never rebase commits that others have seen** or shared. Pushing new commits with different hashes for the same content causes Git to see them as unrelated work, leading to merging nightmares and duplicate changes.

## 7. Disaster Recovery: The Ref Log

Git almost never truly deletes anything immediately—it just hides it.

*   The **ref log** (`git ref log`) shows **every location HEAD has pointed recently** (every checkout, commit, and reset).
*   The "lost" commits (orphaned commits after a reset or the old commits before a rebase) are usually recorded here.
*   To recover work, find the hash of the lost commit in the ref log and create a new branch pointing to it.
*   **Caveat**: Ref log entries expire, typically 90 days for reachable commits and 30 days for unreachable ones, so immediate recovery is advised. The ref log is your map when everything goes wrong.
