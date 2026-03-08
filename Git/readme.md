# Git
**Definition**: Git is a distributed version control system used to track changes in source code and coordinate work among developers during software development. It runs locally and handles things like commits, branches, merges, and history.

Brief **Description**:
Git allows developers to save versions of their code, track modifications, create branches for new features, and merge changes safely. Because it is distributed, every user has a full copy of the project history, which makes collaboration faster and more reliable.It is created by Linus Torvalds.

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
| Platform | Type                   | Owner       | Key idea                    |
| -------- | ---------------------- | ----------- | --------------------------- |
| Git      | version control system | open source | track code                  |
| GitHub   | hosting platform       | Microsoft   | biggest developer platform  |
| Gitea    | software               | open source | lightweight self-host Git   |
| Forgejo  | fork of Gitea          | community   | stronger open governance    |
| Codeberg | hosting service        | non-profit  | privacy-focused Git hosting |


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

**Commit** means making a change or modifying the current code
