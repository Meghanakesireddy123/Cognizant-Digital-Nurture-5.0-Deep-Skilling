# Hands-On Git 3: Branching and Merging

## Objective

The objective of this hands-on exercise is to understand Git Branching and Merging. This exercise demonstrates how to create a new branch, make changes independently, compare differences, merge changes into the master branch, and delete the branch after successful merging.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand Git Branching.
- Create and switch branches.
- Commit changes in a branch.
- Compare branches.
- Merge a branch into the master branch.
- View Git history.
- Delete merged branches.

---

# Software Requirements

- Git Bash
- GitHub / GitLab
- P4Merge (Optional)
- Windows
- Existing Git Repository

---

# Project Name

GitDemo

---

# Scenario

In a software development team, developers create separate branches to work on new features without affecting the main project.

Once development is completed, the feature branch is merged into the master branch.

This exercise demonstrates the complete Git Branching and Merging workflow.

---

# Step 1: Open Existing Repository

Navigate to the repository.

```bash
cd GitDemo
```

---

# Step 2: Check Current Branch

```bash
git branch
```

### Expected Output

```text
* master
```

The `*` symbol indicates the currently active branch.

---

# Step 3: Create a New Branch

```bash
git branch GitNewBranch
```

---

# Step 4: View All Branches

```bash
git branch
```

### Expected Output

```text
* master

GitNewBranch
```

To view both local and remote branches:

```bash
git branch -a
```

---

# Step 5: Switch to the New Branch

```bash
git checkout GitNewBranch
```

### Expected Output

```text
Switched to branch 'GitNewBranch'
```

---

# Step 6: Create a New File

```bash
echo Branch Development > branch.txt
```

Verify the file:

```bash
cat branch.txt
```

---

# Step 7: Check Repository Status

```bash
git status
```

Output

```text
Untracked files:

branch.txt
```

---

# Step 8: Add File to Staging Area

```bash
git add branch.txt
```

---

# Step 9: Commit Changes

```bash
git commit -m "Added branch.txt in GitNewBranch"
```

### Expected Output

```text
1 file changed

create mode 100644 branch.txt
```

---

# Step 10: Verify Status

```bash
git status
```

Expected Output

```text
On branch GitNewBranch

nothing to commit, working tree clean
```

---

# Step 11: Switch Back to Master Branch

```bash
git checkout master
```

---

# Step 12: Compare Branch Differences

Display command-line differences:

```bash
git diff master GitNewBranch
```

---

# Step 13: Compare Using P4Merge (Optional)

```bash
git difftool master GitNewBranch
```

This opens P4Merge and visually compares the files in both branches.

---

# Step 14: Merge Branch

```bash
git merge GitNewBranch
```

### Expected Output

```text
Updating ...

Fast-forward

branch.txt
```

---

# Step 15: View Git History

```bash
git log --oneline --graph --decorate
```

### Expected Output

```text
* abc1234 Added branch.txt in GitNewBranch

* def5678 Initial Commit
```

The graph shows the branch merge history.

---

# Step 16: Delete Branch

```bash
git branch -d GitNewBranch
```

### Expected Output

```text
Deleted branch GitNewBranch
```

---

# Step 17: Verify Branches

```bash
git branch
```

Expected Output

```text
* master
```

---

# Git Commands Used

| Command | Description |
|----------|-------------|
| git branch | Displays all local branches |
| git branch -a | Displays local and remote branches |
| git checkout | Switches between branches |
| git add | Adds files to staging |
| git commit | Saves changes locally |
| git diff | Displays branch differences |
| git difftool | Opens graphical comparison tool |
| git merge | Merges branches |
| git log | Displays commit history |
| git branch -d | Deletes a branch |

---

# Git Branching Workflow

```text
master

│

├──────────────┐

│              │

│      GitNewBranch

│              │

│        Development

│              │

└──────────────┘

↓

Merge into master

↓

Delete Branch
```

---

# Explanation

## Git Branch

A branch is an independent line of development used to implement features without affecting the main codebase.

---

## git checkout

Switches the working directory to another branch.

Example:

```bash
git checkout GitNewBranch
```

---

## git diff

Displays differences between two branches.

Example:

```bash
git diff master GitNewBranch
```

---

## git merge

Combines the changes from one branch into another.

Example:

```bash
git merge GitNewBranch
```

---

## git log --oneline --graph --decorate

Displays a compact graphical representation of the commit history.

---

## git branch -d

Deletes a branch after it has been successfully merged.

---

# Advantages of Branching

- Safe feature development.
- Parallel development.
- Easy collaboration.
- Simplified code review.
- Faster bug fixing.
- Maintains stable master branch.

---

# Learning Outcome

- Created a new Git branch.
- Switched between branches.
- Added and committed changes.
- Compared branches.
- Merged changes into the master branch.
- Viewed commit history.
- Deleted the merged branch.

---

# Result

Successfully implemented Git Branching and Merging by creating a feature branch, making independent changes, comparing branch differences, merging the feature branch into the master branch, reviewing the commit history, and deleting the merged branch using Git best practices.
