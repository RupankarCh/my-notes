## Git Intro
**Definition**: Git is a distributed version control system it's a program for managing source code and coordinate among developers during software development. It runs locally and handles things like commits, branches, merges, and history.

Brief **Description**:
Git allows developers to save versions of their code, track modifications, create branches for new features, and merge changes safely. Because it is distributed, every user has a full copy of the project history, which makes collaboration faster and more reliable.It is created by Linus Torvalds.Github hosts a copy of that code online, VCS tracks every changes so that we can get back to our previous changes. 

**Features of VCS**
Backup and restore 
Collaboration 
Branches and Merging: users can diverge from the main base of code, experiment and then bring changes back in ling without losing work.
Tracking Activity of Changes.

Brief **History**:
```
Git (2005)
   │
   ├── GitHub (2008) → biggest hosting platform
   │
   └── Self-hosted Git platforms
          │
          ├── Gogs
          │
          └── Gitea (2016)
                 │
                 └── Forgejo (2022)
                        │
                        └── Used by Codeberg
```
## Git Installation
Search Git>download the executable file> only uncheck all the boxes except git for Windows updates> use visual studio code and get default edition> overwrite the default branch name of new repo> unix tools and command prompt> install
Install VSCode
Initialize a folder to reflect your git repository(Set a folder)


| Platform | Type                   | Owner       | Key idea                    |
| -------- | ---------------------- | ----------- | --------------------------- |
| Git      | version control system | open source | track code                  |
| GitHub   | hosting platform       | Microsoft   | biggest developer platform  |
| Gitea    | software               | open source | lightweight self-host Git   |
| Forgejo  | fork of Gitea          | community   | stronger open governance    |
| Codeberg | hosting service        | non-profit  | privacy-focused Git hosting |

## Repository
A Git **repository** is a folder that contains your project files and the complete history of all changes made to those files and it is managed by Git.
A repo usually contains:
- Project files – source code, images, documentation, etc.
- Version history – every change (called commits) saved over time
- Branches – different versions of the project being developed simultaneously
- Configuration files – stored inside the hidden .git folder

Types of Git repositories

1.Local repository
- Stored on your computer
- You work and commit changes locally

2.Remote repository
Hosted online on services like GitHub, GitLab, or Bitbucket, Used for collaboration and backup.


## Git Storage
.git directory contains all the internal Git data — including your commits, branches, logs, config, and other versioning information.It’s essentially the database Git uses to track changes in your project.After this, you can start committing versions using git add and git commit.


## Git Bash Commands
Here are some of the **most commonly used commands in Git** when working in **Git Bash**. Think of them as the core toolkit most developers use daily.

---

1️⃣ **Repository setup**

**Initialize a new repo**

```bash
git init
```

**Clone a remote repo to your local system**

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/user/project.git
```

---

**2️⃣ Checking status & history**

**Check current repo status**

```bash
git status
```

**View commit history**

```bash
git log
```

Short version:

```bash
git log --oneline
```

---

**3️⃣ Adding files**

**Add a specific file**

```bash
git add filename
```

**Add all files**

```bash
git add .
```

This moves files to the **staging area**.

---

**4️⃣ Commit changes**

Save staged changes to repository history.**Commit** is a snapshot of a project at a specific time, It records file changes with a descriptive message.

```bash
git commit -m "your commit message"
```

Example:

```bash
git commit -m "Fix login bug"
```

---

**5️⃣ Branch management**

**Create a branch**

```bash
git branch new-branch
```

**Switch branch**

```bash
git checkout branch-name
```

Modern command:

```bash
git switch branch-name
```

Create + switch:

```bash
git checkout -b new-branch
```

---

**6️⃣ Push & pull (remote repositories)**

Push uploads **local commits to a remote repository**. So that others can also collaborate in the project.

```bash
git push origin branch-name
```

Pull updates from remote:

```bash
git pull
```

Fetch changes without merging:

```bash
git fetch
```

These are commonly used with platforms like
GitHub, GitLab, or Codeberg.

---

**7️⃣ Remote repository management**

Check remotes:

```bash
git remote -v
```

Add remote:

```bash
git remote add origin <repo-url>
```

---

**8️⃣ Undo mistakes**

Unstage a file:

```bash
git reset filename
```

Discard file changes:

```bash
git checkout -- filename
```

Undo last commit (keep changes):

```bash
git reset --soft HEAD~1
```

---

**9️⃣ Branch merging**

Merge branch into current branch:

```bash
git merge branch-name
```

---

**🔟 Stashing temporary work**

Save unfinished work temporarily:

```bash
git stash
```

Restore it later:

```bash
git stash pop
```

---

**⭐ The **daily workflow** most developers follow**

```bash
git clone repo
git checkout -b feature-branch
git add .
git commit -m "Add feature"
git push origin feature-branch
```

---

**Top 10 commands developers use daily**

```
git clone
git status
git add
git commit
git push
git pull
git branch
git checkout
git merge
git log
```
