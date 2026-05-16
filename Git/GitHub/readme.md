# Github
Github **Definition** a cloud based platform that let us store, manage and collaborate on code using **Git** version control system.

Description: It records everything that has been changed and by whom it was changed.You can also go back to a previous commit to revert those changes.It is **microsoft** owned company where you can put these git repositories. It uses **Markdown** language to edit it's readme.md file.

A **pull request** in GitHub is a request to review and merge your code changes from one branch into another branch of a repository.

## Access
| Feature           | Public Repo       | Private Repo             |
| ----------------- | ----------------- | ------------------------ |
| Storage           | Free              | Free                     |
| GitHub Actions    | Unlimited minutes | ~2000 free minutes/month |
| Security scanning | Available         | Available                |

# Branching
Branches help to provide a developer the capability to work on a dedicated functionality.

A Language Template on GitHub usually means a pre-made .gitignore template based on your programming language or framework.

When creating a repository, GitHub asks if you want to add .gitignore. Then it lets you pick templates like:

Python
Java
Node
C++
Android
Django
React
Unity
etc.

These templates already contain common files/folders that should not be uploaded to Git.

## 1. What is `.gitignore`?

A **`.gitignore`** file tells Git which files/folders it should **not track or upload** to the repository.

### Why use it?

Some files should stay out of version control, such as:

* Temporary files
* Build/output folders
* Dependencies
* Environment secrets (`.env`)
* OS-generated files (`.DS_Store`, `Thumbs.db`)

### Example for Python:

```gitignore
__pycache__/
*.pyc
.env
venv/
```

### Example for Node.js:

```gitignore
node_modules/
.env
dist/
```

When creating a repo, GitHub lets you choose a ready-made `.gitignore` template for languages like Python, Java, Node, etc.

---

## 2. What is a LICENSE?

A **LICENSE** file tells others **what they are allowed to do with your code**.

Without a license, legally people usually **cannot freely reuse, modify, or distribute** your code.

### Common licenses:

#### MIT License

* Very permissive
* Anyone can use/modify/sell your code
* Must include original license notice

Good for open source beginners.

#### Apache 2.0

* Similar to MIT
* Adds patent protection

#### GPL v3

* If someone modifies and distributes your code, they must also open-source their changes.

#### No License

* Others can view code, but reuse rights are limited.

---

## 3. What should you choose?

### If personal learning project:

* `.gitignore`: choose your language template
* License: MIT is common, or no license if private use only

### If professional/open-source project:

* `.gitignore`: definitely yes
* License: MIT / Apache 2.0 / GPL depending on goals

---


## GitHub Actions:
an automation tool inside GitHub that lets you automatically build, test, and deploy your code when certain events happen in a repository.

GitHub Actions is the whole system that:
- Reads the .yml file
- Detects triggers
- Starts runners
- Runs jobs
- Shows logs/results

How it works (When a trigger is initiated):

1.like You push code to a Git repository on GitHub

2.A workflow file (written in YAML) gets triggered

3.GitHub runs automated jobs like:
 - Installing dependencies
 - Running tests
 - Building the project
 - Deploying the app

It is mainly used for:
- CI/CD (Continuous Integration / Continuous Deployment)
- Running tests automatically
- Building apps
- Deploying websites/apps
- Linting / formatting code
- Sending notifications
- Scheduled jobs


Example triggers:
- Push to a branch
- Pull request opened
- Scheduled time
- Manual trigger

When you push code:
GitHub detects the push
It runs your workflow
Tests execute automatically
If successful, it can deploy the app

These automations are defined in YAML files inside:

.github/workflows/

Example workflow:
```
name: Python Tests

on: [push]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - run: python --version
      - run: pip install -r requirements.txt
      - run: pytest
```


What is a GitHub Runner?

A GitHub Runner is the machine that actually executes your GitHub Actions workflow.

GitHub Actions = the automation system / instructions
Runner = the computer doing the work
Types of Runners
1. GitHub-hosted runners

Provided by GitHub.

Examples:

Ubuntu Linux
Windows
macOS

You use:

runs-on: ubuntu-latest

GitHub creates a temporary machine, runs the job, then removes it.

2. Self-hosted runners

Your own computer/server runs the jobs.

Useful when you need:

- More power
- Private network access
- Custom software
- Cheaper large workloads
- Internal company servers


Why Developers Use It
Automatic testing on every push
Prevent broken code merges
Auto deploy apps
Save manual work
Team collaboration
Beginner Summary

If you are building projects:

Push code to GitHub
GitHub Actions can test it automatically
Runner is the machine doing that testing

## Disadvantages of using Github
- It doesn't directly provide repository **mirroring**(keeping a copy of the source code of a perticular repository).
- Microsoft uses Github to train AI models.
