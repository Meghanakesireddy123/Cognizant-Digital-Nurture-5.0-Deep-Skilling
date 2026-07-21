# Hands-On Git 4: Merge Conflict Resolution

## Objective

The objective of this hands-on exercise is to understand Git Merge Conflicts and learn how to resolve conflicts when multiple developers modify the same file in different branches. This exercise demonstrates conflict identification, comparison, resolution using a merge tool, and updating the repository after successful conflict resolution.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand Merge Conflicts in Git.
- Create and switch Git branches.
- Modify files in different branches.
- Compare changes between branches.
- Resolve merge conflicts manually.
- Use P4Merge for 3-way merge.
- Update the `.gitignore` file.
- Maintain a clean Git repository.

---

# Software Requirements

- Git Bash
- GitHub / GitLab
- P4Merge Tool
- Windows
- Existing Git Repository

---

# Project Name

GitDemo

---

# Scenario

Two developers modify the same file (`hello.xml`) in different branches.

When both branches are merged, Git cannot automatically decide which version should be kept, resulting in a Merge Conflict.

This exercise demonstrates the complete conflict resolution process.

---

# Step 1: Verify Master Branch Status

```bash
git checkout master
```

```bash
git status
```

### Expected Output

```text
On branch master

nothing to commit, working tree clean
```

---

# Step 2: Create a New Branch

```bash
git branch GitWork
```

Switch to the branch.

```bash
git checkout GitWork
```

---

# Step 3: Create hello.xml

```bash
echo "<message>Hello from GitWork Branch</message>" > hello.xml
```

Verify:

```bash
cat hello.xml
```

---

# Step 4: Check Status

```bash
git status
```

---

# Step 5: Add and Commit

```bash
git add hello.xml
```

```bash
git commit -m "Added hello.xml in GitWork branch"
```

---

# Step 6: Switch Back to Master

```bash
git checkout master
```

---

# Step 7: Modify hello.xml in Master

```bash
echo "<message>Hello from Master Branch</message>" > hello.xml
```

Verify:

```bash
cat hello.xml
```

---

# Step 8: Commit Changes

```bash
git add hello.xml
```

```bash
git commit -m "Added hello.xml in Master branch"
```

---

# Step 9: View Commit History

```bash
git log --oneline --graph --decorate --all
```

### Expected Output

```text
* abc1234 Added hello.xml in Master branch

| * xyz4567 Added hello.xml in GitWork branch

|/

* def8901 Initial Commit
```

---

# Step 10: Compare Branch Differences

```bash
git diff master GitWork
```

---

# Step 11: Visual Comparison (P4Merge)

```bash
git difftool master GitWork
```

P4Merge displays differences between both branches visually.

---

# Step 12: Merge GitWork into Master

```bash
git merge GitWork
```

### Expected Output

```text
Auto-merging hello.xml

CONFLICT (content): Merge conflict in hello.xml

Automatic merge failed.
```

---

# Step 13: View Merge Conflict

Open the file.

```bash
notepad hello.xml
```

Git inserts conflict markers.

```xml
<<<<<<< HEAD

<message>Hello from Master Branch</message>

=======

<message>Hello from GitWork Branch</message>

>>>>>>> GitWork
```

---

# Step 14: Resolve Conflict

Edit the file manually.

Final Version

```xml
<message>

Hello from Master Branch

Hello from GitWork Branch

</message>
```

Save the file.

---

# Step 15: Add Resolved File

```bash
git add hello.xml
```

---

# Step 16: Commit Merge

```bash
git commit -m "Resolved merge conflict in hello.xml"
```

---

# Step 17: Update .gitignore

Open `.gitignore`

```bash
notepad .gitignore
```

Add

```text
*.bak
```

Save.

---

# Step 18: Commit .gitignore

```bash
git add .gitignore
```

```bash
git commit -m "Updated .gitignore"
```

---

# Step 19: View Branches

```bash
git branch
```

Expected Output

```text
* master

GitWork
```

---

# Step 20: Delete Branch

```bash
git branch -d GitWork
```

Expected Output

```text
Deleted branch GitWork
```

---

# Step 21: View Final Git History

```bash
git log --oneline --graph --decorate
```

Expected Output

```text
* Merge Commit

* Updated .gitignore

* Resolved merge conflict

* Initial Commit
```

---

# Git Commands Used

| Command | Description |
|----------|-------------|
| git branch | Creates and lists branches |
| git checkout | Switches branches |
| git add | Adds files to staging area |
| git commit | Saves changes locally |
| git merge | Merges branches |
| git diff | Displays file differences |
| git difftool | Opens graphical comparison |
| git log | Displays commit history |
| git branch -d | Deletes merged branch |
| git status | Displays repository status |

---

# Merge Conflict Workflow

```text
Master Branch

        │

        ├─────────────┐

        │             │

        │         GitWork Branch

        │             │

Modify hello.xml  Modify hello.xml

        │             │

        └────── Merge ──────┐

                             │

                     Merge Conflict

                             │

                  Manual Resolution

                             │

                      Commit Changes

                             │

                      Delete Branch
```

---

# Explanation

## What is a Merge Conflict?

A Merge Conflict occurs when the same file is modified differently in two branches and Git cannot automatically determine which version should be retained.

---

## git merge

Merges changes from one branch into another.

Example:

```bash
git merge GitWork
```

---

## git diff

Displays differences between branches.

```bash
git diff master GitWork
```

---

## P4Merge

P4Merge is a graphical tool that provides side-by-side comparison and 3-way merge functionality to resolve conflicts easily.

---

## Conflict Markers

Git inserts special markers into conflicted files.

```text
<<<<<<< HEAD

=======

>>>>>>> GitWork
```

These markers help identify conflicting changes.

---

## .gitignore

The `.gitignore` file prevents unnecessary files from being tracked.

Example:

```text
*.bak
```

---

# Advantages of Merge Conflict Resolution

- Supports collaborative development.
- Prevents accidental code overwrites.
- Ensures code consistency.
- Improves version control.
- Maintains project stability.

---

# Learning Outcome

- Created and managed Git branches.
- Generated a merge conflict.
- Compared branch differences.
- Resolved conflicts manually.
- Used a 3-way merge tool.
- Updated the `.gitignore` file.
- Deleted merged branches.
- Verified commit history after conflict resolution.

---

# Result

Successfully implemented Git Merge Conflict Resolution by creating conflicting changes in different branches, resolving the conflict manually, committing the merged changes, updating the `.gitignore` file, and maintaining a clean Git repository using Git best practices.
