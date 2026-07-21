# Hands-On Git 5: Clean Up and Push to Remote Repository

## Objective

The objective of this hands-on exercise is to understand how to clean up a Git repository, synchronize the local repository with the remote repository, and push the latest changes to GitHub or GitLab. This exercise demonstrates the final workflow after completing development and merge activities.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Verify the repository status.
- Check available branches.
- Synchronize the local repository with the remote repository.
- Push committed changes to the remote repository.
- Verify that changes are reflected remotely.
- Maintain a clean Git repository.

---

# Software Requirements

- Git Bash
- GitHub / GitLab
- Windows
- Existing Git Repository

---

# Project Name

GitDemo

---

# Scenario

After completing all development activities and resolving merge conflicts, developers should clean up the repository, synchronize with the latest remote changes, and push their completed work to the remote repository.

This exercise demonstrates the final Git workflow.

---

# Step 1: Open Existing Repository

Navigate to the repository.

```bash
cd GitDemo
```

---

# Step 2: Verify Master Branch

```bash
git checkout master
```

---

# Step 3: Verify Repository Status

```bash
git status
```

### Expected Output

```text
On branch master

nothing to commit, working tree clean
```

This confirms that the local repository is clean.

---

# Step 4: Display Available Branches

```bash
git branch
```

### Expected Output

```text
* master
```

To display both local and remote branches:

```bash
git branch -a
```

---

# Step 5: Pull Latest Changes from Remote Repository

```bash
git pull origin master
```

### Expected Output

```text
Already up to date.
```

If new commits are available, Git automatically downloads and merges them into the local repository.

---

# Step 6: Push Local Changes to Remote Repository

```bash
git push origin master
```

### Expected Output

```text
Enumerating objects...

Counting objects...

Writing objects...

To https://github.com/username/GitDemo.git

master -> master
```

The latest commits are successfully uploaded to the remote repository.

---

# Step 7: Verify Remote Repository

Open your GitHub or GitLab repository.

Verify that:

- Latest commits are visible.
- Updated files are available.
- Commit history matches the local repository.
- Branch status is synchronized.

---

# Git Commands Used

| Command | Description |
|----------|-------------|
| git checkout master | Switches to the master branch |
| git status | Displays repository status |
| git branch | Lists local branches |
| git branch -a | Lists local and remote branches |
| git pull | Downloads latest changes from remote repository |
| git push | Uploads local commits to the remote repository |

---

# Git Workflow

```text
Working Directory

↓

Staging Area

↓

Local Repository

↓

git pull

↓

Synchronize with Remote

↓

git push

↓

Remote Repository (GitHub / GitLab)
```

---

# Explanation

## git checkout

Switches the current working branch.

Example:

```bash
git checkout master
```

---

## git status

Displays the current status of the repository, including modified, staged, and committed files.

Example:

```bash
git status
```

---

## git branch

Lists all available branches.

Example:

```bash
git branch
```

---

## git pull

Downloads and merges the latest changes from the remote repository into the current branch.

Example:

```bash
git pull origin master
```

---

## git push

Uploads local commits to the remote repository.

Example:

```bash
git push origin master
```

---

# Best Practices

- Always check `git status` before pushing.
- Pull the latest changes before pushing.
- Resolve conflicts before committing.
- Keep the master branch clean.
- Delete unnecessary branches after merging.

---

# Advantages of Synchronizing with Remote Repository

- Keeps the repository up to date.
- Enables team collaboration.
- Prevents version conflicts.
- Maintains project consistency.
- Ensures all developers work with the latest code.

---

# Learning Outcome

- Verified repository status.
- Listed available branches.
- Pulled the latest changes from the remote repository.
- Successfully pushed local commits.
- Verified synchronization between local and remote repositories.
- Followed Git best practices for repository maintenance.

---

# Result

Successfully cleaned up the Git repository, synchronized the local repository with the remote repository using `git pull`, pushed the latest changes using `git push`, and verified that all updates were reflected in the remote repository.
