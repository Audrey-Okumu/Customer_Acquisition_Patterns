# Customer_Acquisition_Patterns

# 🗂️ Git & GitHub Cheat Sheet
> **For Students | Data Science & Software Development Group Projects**
> A beginner-friendly reference guide to version control with Git and GitHub.

---

## Table of Contents
1. [Introduction to Git](#1-introduction-to-git)
2. [Introduction to GitHub](#2-introduction-to-github)
3. [Installing Git](#3-installing-git)
4. [Git Configuration](#4-git-configuration)
5. [Creating a Repository](#5-creating-a-repository)
6. [Core Git Commands](#6-core-git-commands)
7. [GitHub Commands](#7-github-commands)
8. [Branching](#8-branching)
9. [.gitignore](#9-gitignore)
10. [Team Collaboration Workflow](#10-team-collaboration-workflow)
11. [Best Practices](#11-best-practices)
12. [Quick Reference Table](#12-quick-reference-table)

---

## 1. Introduction to Git

### What is Git?
**Git** is a free, open-source **version control system** that tracks changes to files over time. Think of it as a detailed "save history" for your entire project — you can see who changed what, when, and why.

### Why Does Version Control Matter?
Without version control, working on a team project is chaotic: files get overwritten, changes are lost, and it's impossible to know what broke the code. Git solves this by:

- 📌 **Tracking every change** made to your project files
- 🔄 **Allowing you to revert** to any previous version of your work
- 👥 **Enabling collaboration** — multiple people can work on the same project without conflict
- 🧪 **Supporting experimentation** — try new ideas without risking the main project

> **Think of Git like Google Docs' version history — but for your entire codebase.**

---

## 2. Introduction to GitHub

### What is GitHub?
**GitHub** is a cloud-based platform that hosts Git repositories online. It provides a web interface for managing your code, reviewing changes, collaborating with teammates, and sharing your work with the world.

### Git vs. GitHub — What's the Difference?

| | **Git** | **GitHub** |
|---|---|---|
| **What it is** | A version control tool | A cloud hosting platform |
| **Where it runs** | On your local computer | On the internet (browser) |
| **Purpose** | Track and manage changes locally | Share, collaborate, and back up code online |
| **Needs internet?** | ❌ No | ✅ Yes |
| **Made by** | Linus Torvalds (2005) | GitHub, Inc. (acquired by Microsoft) |

> 💡 **Simple analogy:** Git is the engine; GitHub is the garage where you park and share your car.

---

## 3. Installing Git

### How to Download and Install Git

| Operating System | Instructions |
|---|---|
| **Windows** | Download from [git-scm.com](https://git-scm.com/download/win) and run the installer |
| **macOS** | Run `xcode-select --install` in Terminal, or install via [Homebrew](https://brew.sh): `brew install git` |
| **Linux (Ubuntu/Debian)** | Run `sudo apt update && sudo apt install git` in Terminal |

### Verify Your Installation

After installing, open your terminal (or Git Bash on Windows) and run:

```bash
git --version
```

**Expected output:**
```
git version 2.43.0
```

If you see a version number, Git is installed correctly. ✅

---

## 4. Git Configuration

Before you start using Git, tell it who you are. This information is attached to every commit you make.

### Set Your Name
```bash
git config --global user.name "Your Full Name"
```

### Set Your Email
```bash
git config --global user.email "your.email@example.com"
```

> ⚠️ Use the **same email address** you used to sign up on GitHub.

### View All Configuration Settings
```bash
git config --list
```

**Example output:**
```
user.name=Jane Doe
user.email=jane.doe@example.com
core.editor=vim
```

> The `--global` flag applies these settings to **all** repositories on your computer. You can also set per-project settings by omitting `--global` inside a specific project folder.

---

## 5. Creating a Repository

A **repository** (or "repo") is a folder that Git tracks. Here's how to create one from scratch.

### Step-by-Step

**1. Create a new project folder:**
```bash
mkdir my-project
```

**2. Navigate into the folder:**
```bash
cd my-project
```

**3. Initialize a Git repository:**
```bash
git init
```

**Expected output:**
```
Initialized empty Git repository in /path/to/my-project/.git/
```

This creates a hidden `.git/` folder inside your project — that's where Git stores all its tracking data. You only run `git init` **once** per project.

---

## 6. Core Git Commands

These are the commands you'll use every single day.

---

### `git status`
Shows the current state of your working directory — which files have been modified, staged, or are untracked.

```bash
git status
```

**Example output:**
```
On branch main
Changes not staged for commit:
  modified:   analysis.py

Untracked files:
  new_data.csv
```

> 🔍 Run this often — it's your best friend for understanding what's going on.

---

### `git add`
Stages files — tells Git which changes you want to include in your next commit.

```bash
# Stage a single file
git add filename.py

# Stage multiple specific files
git add file1.py file2.py

# Stage ALL changed files in the current directory
git add .
```

> Think of staging as putting items in a box before shipping (committing) them.

---

### `git commit`
Saves a snapshot of the staged changes with a descriptive message.

```bash
git commit -m "Add data cleaning script for sales dataset"
```

> ✏️ Always write a **clear, meaningful message** describing what you changed and why.

**Commit message examples:**
```
✅ Good: "Fix null value handling in preprocessing pipeline"
❌ Bad:  "fix stuff"
❌ Bad:  "asdfgh"
```

---

### `git log`
Displays the history of commits in your repository.

```bash
git log
```

**Example output:**
```
commit 3f2a1b9c...
Author: Jane Doe <jane@example.com>
Date:   Mon Jan 15 10:30:00 2024

    Add data cleaning script for sales dataset

commit 1a4e7d2f...
Author: John Smith <john@example.com>
Date:   Sun Jan 14 09:15:00 2024

    Initial project setup
```

**Compact one-line view:**
```bash
git log --oneline
```

```
3f2a1b9 Add data cleaning script for sales dataset
1a4e7d2 Initial project setup
```

---

### `git diff`
Shows the exact line-by-line changes that have been made but not yet staged.

```bash
git diff
```

```bash
# Compare staged changes against the last commit
git diff --staged
```

> Lines starting with `+` are additions; lines starting with `-` are deletions.

---

## 7. GitHub Commands

These commands connect your local repository to GitHub.

---

### `git clone`
Downloads a copy of an existing GitHub repository to your local machine.

```bash
git clone https://github.com/username/repository-name.git
```

This creates a new folder with all the project files and the full Git history. Use this when **joining an existing project**.

---

### `git remote add origin`
Links your local repository to a remote GitHub repository.

```bash
git remote add origin https://github.com/username/repository-name.git
```

- `origin` is just a nickname for the remote URL (standard convention)
- Run this **once** after `git init` when setting up a new project on GitHub

**Verify the remote was added:**
```bash
git remote -v
```

---

### `git push`
Uploads your local commits to GitHub.

```bash
# First-time push (sets the upstream branch)
git push -u origin main

# Subsequent pushes
git push
```

> ☁️ Think of `push` as uploading your saved work to the cloud.

---

### `git pull`
Downloads the latest changes from GitHub and merges them into your local branch.

```bash
git pull
```

> 📥 Always `git pull` before you start working to make sure you have the latest version of the project.

---

## 8. Branching

Branches let you work on new features or experiments **without touching the main codebase**. Each branch is an independent line of development.

---

### Create and Switch to a New Branch
```bash
git checkout -b feature/data-visualization
```

> The `-b` flag creates the branch AND switches to it in one step.

**Branch naming tips:**
```
feature/add-login-page
fix/null-value-bug
experiment/new-model-test
```

---

### Switch Between Branches
```bash
# Switch to an existing branch
git checkout main

# Modern alternative (Git 2.23+)
git switch main
```

---

### Merge a Branch into Main
When your feature is ready, merge it back into the `main` branch:

```bash
# 1. First, switch to the main branch
git checkout main

# 2. Merge your feature branch into main
git merge feature/data-visualization
```

---

### Delete a Branch
After merging, clean up by deleting the branch:

```bash
# Delete a local branch
git branch -d feature/data-visualization

# Delete a remote branch on GitHub
git push origin --delete feature/data-visualization
```

---

### View All Branches
```bash
# List local branches
git branch

# List all branches (local + remote)
git branch -a
```

---

## 9. .gitignore

### What is `.gitignore`?
A `.gitignore` file tells Git which files and folders to **ignore and never track**. This is essential for keeping your repository clean and secure.

### Why You Need It
- Avoid committing **secret keys, API tokens, and passwords**
- Exclude **large data files** that don't belong in version control
- Skip auto-generated files like `__pycache__/` or `.ipynb_checkpoints/`
- Prevent OS-specific files (like `.DS_Store` on macOS) from cluttering the repo

### Example `.gitignore` for a Data Science Project

Create a file named `.gitignore` in your project root:

```
# --- Python ---
__pycache__/
*.py[cod]
*.egg-info/
.env

# --- Jupyter Notebooks ---
.ipynb_checkpoints/
*.ipynb_checkpoints

# --- Data Files (large/sensitive) ---
data/raw/
*.csv
*.xlsx
*.parquet

# --- Environment ---
venv/
.env
*.env

# --- OS Files ---
.DS_Store
Thumbs.db

# --- IDE Settings ---
.vscode/
.idea/
```

> ✅ Create your `.gitignore` **before** your first commit so sensitive files are never accidentally tracked.

---

## 10. Team Collaboration Workflow

Follow this workflow every time you work on a shared project:

```
┌─────────────────────────────────────────────────────────────┐
│                   TEAM WORKFLOW CYCLE                       │
│                                                             │
│  1. Pull latest changes  →  git pull                       │
│  2. Create a branch      →  git checkout -b feature/name   │
│  3. Make your changes    →  (edit files)                   │
│  4. Stage changes        →  git add .                      │
│  5. Commit changes       →  git commit -m "message"        │
│  6. Push to GitHub       →  git push -u origin feature/name│
│  7. Open a Pull Request  →  (on GitHub website)            │
│  8. Review & Merge       →  (teammate reviews your code)   │
└─────────────────────────────────────────────────────────────┘
```

### Step-by-Step

**Step 1 — Pull before you start:**
```bash
git pull
```
Always sync with the latest code before making changes.

**Step 2 — Create a branch:**
```bash
git checkout -b feature/your-feature-name
```
Never work directly on `main`. Always use a branch.

**Step 3 — Make your changes**
Edit your files, write code, run your analysis.

**Step 4 — Stage and commit:**
```bash
git add .
git commit -m "Descriptive message about what you did"
```

**Step 5 — Push your branch:**
```bash
git push -u origin feature/your-feature-name
```

**Step 6 — Open a Pull Request (PR) on GitHub:**
- Go to your repository on GitHub
- Click **"Compare & pull request"**
- Add a description of your changes
- Request a teammate to review it

**Step 7 — Review, discuss, and merge**
Teammates review the PR, leave comments, request changes if needed, then merge it into `main`.

---

## 11. Best Practices

### ✏️ Write Meaningful Commit Messages
Your commit messages are the history of your project. Make them count.

```bash
# ✅ Good commit messages
git commit -m "Add exploratory data analysis notebook for Q3 sales"
git commit -m "Fix KeyError in feature_engineering.py when column is missing"
git commit -m "Update README with setup instructions"

# ❌ Bad commit messages
git commit -m "stuff"
git commit -m "fix"
git commit -m "changes"
```

---

### 🔐 Never Commit Secrets
- Never commit **API keys**, **passwords**, **database credentials**, or **tokens**
- Use a `.env` file for secrets and add it to `.gitignore`
- If you accidentally commit a secret, **rotate it immediately** — it's compromised

```bash
# Store secrets in a .env file
DATABASE_PASSWORD=my_secret_password
API_KEY=abc123xyz

# Add .env to .gitignore
echo ".env" >> .gitignore
```

---

### 📁 Keep Repositories Organized
- Use a clear folder structure (`data/`, `notebooks/`, `src/`, `reports/`)
- Include a `README.md` explaining what the project does and how to run it
- Commit early and often — small commits are easier to understand and revert
- Delete merged branches to keep the repo clean
- Never push large binary files (datasets >100MB) — use `.gitignore`

---

## 12. Quick Reference Table

| Command | Description |
|---|---|
| `git init` | Initialize a new Git repository |
| `git status` | Show the state of working directory and staging area |
| `git add <file>` | Stage a specific file for the next commit |
| `git add .` | Stage all changed files |
| `git commit -m "msg"` | Save a snapshot with a message |
| `git log` | View the full commit history |
| `git log --oneline` | View compact commit history |
| `git diff` | Show unstaged changes line by line |
| `git diff --staged` | Show staged changes vs last commit |
| `git clone <url>` | Copy a remote repository locally |
| `git remote add origin <url>` | Link local repo to a remote GitHub repo |
| `git push` | Upload local commits to GitHub |
| `git push -u origin main` | Push and set upstream branch (first time) |
| `git pull` | Download and merge latest changes from GitHub |
| `git checkout -b <branch>` | Create and switch to a new branch |
| `git checkout <branch>` | Switch to an existing branch |
| `git merge <branch>` | Merge a branch into the current branch |
| `git branch` | List all local branches |
| `git branch -d <branch>` | Delete a local branch |
| `git config --global user.name` | Set your Git username |
| `git config --global user.email` | Set your Git email |
| `git config --list` | View all Git configuration settings |

---

> 📘 **Keep learning:** [Official Git Documentation](https://git-scm.com/doc) · [GitHub Docs](https://docs.github.com) · [Pro Git Book (free)](https://git-scm.com/book/en/v2)

---
*Git & GitHub Cheat Sheet — Built for beginner developers and data science students.*
