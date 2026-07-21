# Hands-On Git 1: Git Configuration and Basic Commands

## Objective

The objective of this hands-on exercise is to learn the basic Git commands used in software development. This exercise demonstrates Git configuration, repository initialization, file tracking, committing changes, and working with remote repositories.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Install and configure Git.
- Configure Git username and email.
- Set Notepad++ as the default Git editor.
- Initialize a local Git repository.
- Create and track files.
- Commit changes.
- Push and Pull code from a remote repository.
- Understand the Git workflow.

---

# Software Requirements

- Git Bash
- GitHub or GitLab Account
- Notepad++
- Windows 10/11

---

# Project Name

GitDemo

---

# Step 1: Verify Git Installation

Open Git Bash.

Execute:

```bash
git --version
```

### Expected Output

```text
git version 2.xx.x.windows.x
```

This confirms Git is installed successfully.

---

# Step 2: Configure Git Username

```bash
git config --global user.name "Your Name"
```

Example

```bash
git config --global user.name "Meghana Kesireddy"
```

---

# Step 3: Configure Git Email

```bash
git config --global user.email "your@email.com"
```

Example

```bash
git config --global user.email "meghana@gmail.com"
```

---

# Step 4: Verify Git Configuration

```bash
git config --list
```

### Expected Output

```text
user.name=Meghana Kesireddy

user.email=meghana@gmail.com
```

---

# Step 5: Configure Notepad++ as Default Editor

```bash
git config --global core.editor "notepad++"
```

Verify:

```bash
git config --global -e
```

---

# Step 6: Create Project Folder

```bash
mkdir GitDemo
```

Move into project:

```bash
cd GitDemo
```

---

# Step 7: Initialize Git Repository

```bash
git init
```

### Expected Output

```text
Initialized empty Git repository
```

---

# Step 8: Check Repository Status

```bash
git status
```

### Expected Output

```text
On branch master

No commits yet
```

---

# Step 9: Create File

```bash
echo Welcome to Git > welcome.txt
```

---

# Step 10: Verify File

```bash
dir
```

or

```bash
ls
```

---

# Step 11: View File Content

```bash
cat welcome.txt
```

### Output

```text
Welcome to Git
```

---

# Step 12: Check Git Status

```bash
git status
```

Output

```text
Untracked files:

welcome.txt
```

---

# Step 13: Add File to Staging Area

```bash
git add welcome.txt
```

or

```bash
git add .
```

---

# Step 14: Verify Status

```bash
git status
```

Output

```text
Changes to be committed

new file: welcome.txt
```

---

# Step 15: Commit Changes

```bash
git commit -m "Initial Commit"
```

### Expected Output

```text
1 file changed

create mode 100644 welcome.txt
```

---

# Step 16: Connect Remote Repository

```bash
git remote add origin https://github.com/username/GitDemo.git
```

Check Remote

```bash
git remote -v
```

---

# Step 17: Pull Latest Changes

```bash
git pull origin master
```

---

# Step 18: Push to Remote Repository

```bash
git push origin master
```

---

# Common Git Commands

| Command | Description |
|----------|-------------|
| git init | Creates a new Git repository |
| git status | Displays repository status |
| git add | Adds files to staging area |
| git commit | Saves changes locally |
| git push | Uploads changes to remote repository |
| git pull | Downloads latest changes |
| git config | Configures Git settings |
| git remote | Manages remote repositories |

---

# Git Workflow

```text
Working Directory

↓

git add

↓

Staging Area

↓

git commit

↓

Local Repository

↓

git push

↓

Remote Repository (GitHub/GitLab)
```

---

# Explanation

## git init

Initializes a new Git repository.

---

## git status

Displays tracked and untracked files.

---

## git add

Moves files from the Working Directory to the Staging Area.

---

## git commit

Saves staged changes to the Local Repository.

---

## git push

Uploads committed changes to the Remote Repository.

---

## git pull

Downloads the latest changes from the Remote Repository.

---

# Learning Outcome

- Installed and configured Git.
- Configured Git username and email.
- Set Notepad++ as the default editor.
- Created a local repository.
- Added and committed files.
- Connected a remote repository.
- Performed Push and Pull operations.

---

# Result

Successfully configured Git, initialized a local repository, added and committed files, and synchronized the local repository with a remote repository using Git commands.
