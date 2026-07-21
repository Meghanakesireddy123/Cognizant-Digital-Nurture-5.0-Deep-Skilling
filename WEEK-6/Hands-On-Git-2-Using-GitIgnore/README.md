# Hands-On Git 2: Using .gitignore to Ignore Files and Folders

## Objective

The objective of this hands-on exercise is to understand the purpose of the **.gitignore** file and learn how to ignore unwanted files and folders from being tracked by Git.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand the purpose of `.gitignore`.
- Ignore specific file types.
- Ignore folders from tracking.
- Verify ignored files using `git status`.
- Maintain a clean Git repository.

---

# Software Requirements

- Git Bash
- GitHub
- Windows
- Notepad++
- Existing Git Repository

---

# Project Name

GitDemo

---

# Scenario

Developers often generate temporary files, log files, and folders that should not be committed to the repository.

In this exercise:

- Create a `.log` file.
- Create a `logs` folder.
- Configure `.gitignore`.
- Verify Git ignores these files.

---

# Step 1: Open Existing Repository

Navigate to your project.

```bash
cd GitDemo
```

---

# Step 2: Check Repository Status

```bash
git status
```

---

# Step 3: Create a Log File

```bash
echo Application Started > application.log
```

---

# Step 4: Create a Logs Folder

```bash
mkdir logs
```

Create a sample log file.

```bash
echo Error Log > logs/error.log
```

---

# Step 5: Create .gitignore File

```bash
notepad .gitignore
```

Add the following content.

```text
*.log

logs/
```

Save the file.

---

# Step 6: Verify Repository Files

```bash
dir
```

or

```bash
ls
```

---

# Step 7: Check Git Status

```bash
git status
```

### Expected Output

```text
On branch master

Untracked files:

.gitignore

nothing added to commit
```

Notice that:

- `application.log` is ignored.
- `logs/` folder is ignored.
- Only `.gitignore` is shown.

---

# Step 8: Add .gitignore

```bash
git add .gitignore
```

---

# Step 9: Commit Changes

```bash
git commit -m "Added .gitignore file"
```

### Expected Output

```text
1 file changed

create mode 100644 .gitignore
```

---

# Step 10: Push Changes

```bash
git push origin master
```

---

# Verify Ignored Files

Execute:

```bash
git status
```

Expected Output

```text
On branch master

nothing to commit, working tree clean
```

Git does not display:

- application.log
- logs/
- error.log

because they are ignored.

---

# .gitignore File

```text
*.log

logs/
```

---

# Explanation

## What is .gitignore?

The `.gitignore` file tells Git which files and folders should **not** be tracked.

---

## Ignore File Types

```text
*.log
```

Ignores every file with the `.log` extension.

Example:

```text
application.log

server.log

error.log
```

---

## Ignore Folder

```text
logs/
```

Ignores the complete **logs** folder and all files inside it.

---

# Git Commands Used

| Command | Description |
|----------|-------------|
| git status | Displays repository status |
| git add | Adds files to staging area |
| git commit | Saves changes locally |
| git push | Uploads changes to remote repository |
| mkdir | Creates a new folder |
| echo | Creates a file with content |

---

# Advantages of .gitignore

- Prevents unnecessary files from being committed.
- Keeps the repository clean.
- Protects temporary and generated files.
- Improves repository organization.
- Reduces repository size.

---

# Common Files Ignored

```text
*.log

*.class

*.tmp

node_modules/

target/

.idea/

.vscode/
```

---

# Learning Outcome

- Created a `.gitignore` file.
- Ignored `.log` files.
- Ignored the `logs` folder.
- Verified ignored files using `git status`.
- Managed repository efficiently using Git best practices.

---

# Result

Successfully implemented the `.gitignore` file to ignore unwanted log files and folders from the Git repository. Verified that ignored files were excluded from tracking while maintaining a clean working directory.
