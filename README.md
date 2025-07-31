# Comprehensive Git Commands Guide

This guide covers essential Git commands, their usage, and practical examples to help you manage your projects effectively. Each command includes a clear explanation, syntax, and real-world scenarios to show how and when to use it. Whether you're working solo or with a team, this guide is designed to be your go-to reference for Git commands.

## 1. Setup and Configuration

### `git config`

**Purpose**: Set or view Git configuration settings like your name and email, which appear in commits.

**Usage**:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
git config --list  # View all settings
```

**Example**:
Set your identity for commits:

```bash
git config --global user.name "Alice Smith"
git config --global user.email "alice@example.com"
```

Check settings:

```bash
git config --list
```

**When to Use**:

- First time setting up Git.
- Changing your email or name for commits.

## 2. Initializing a Repository

### `git init`

**Purpose**: Create a new Git repository in the current directory.

**Usage**:

```bash
git init
```

**Example**:
Start a new project:

```bash
mkdir my-website
cd my-website
git init
```

This creates a `.git` folder to track your project.

**When to Use**:

- Starting a new project from scratch.

### `git clone`

**Purpose**: Download a repository from a remote source (e.g., GitHub).

**Usage**:

```bash
git clone <repository-url>
```

**Example**:
Clone a GitHub project:

```bash
git clone https://github.com/alice/my-app.git
cd my-app
```

**When to Use**:

- Working on an existing project hosted online.

## 3. Checking Repository Status

### `git status`

**Purpose**: Show the current state of your working directory and staged files.

**Usage**:

```bash
git status
```

**Example**:
After editing `index.html`:

```bash
git status
```

Output:

```yaml
Changes not staged for commit:
  modified:   index.html
```

**When to Use**:

- Check which files have changed before staging or committing.
- Verify what’s staged or untracked.

## 4. Staging Changes

### `git add`

**Purpose**: Add changes to the staging area for the next commit.

**Usage**:

```bash
git add <file-name>  # Stage a specific file
git add .            # Stage all changes
git add *.js         # Stage files with a specific extension
```

**Example**:
Stage a single file:

```bash
git add style.css
```

Stage all changes:

```bash
git add .
```

**When to Use**:

- After editing files, to prepare them for a commit.
- Selectively stage specific files or all changes.

## 5. Committing Changes

### `git commit`

**Purpose**: Save staged changes to the repository with a message.

**Usage**:

```bash
git commit -m "Your commit message"
git commit -am "Message"  # Add and commit tracked files in one step
```

**Example**:
Commit staged files:

```bash
git add index.html style.css
git commit -m "Add homepage layout and styles"
```

Add and commit in one step:

```bash
git commit -am "Update navigation bar"
```

**When to Use**:

- Save a logical set of changes (e.g., a new feature or bug fix).
- Use `-am` for quick commits of already-tracked files.

## 6. Viewing History

### `git log`

**Purpose**: Display the commit history of the repository.

**Usage**:

```bash
git log                    # Full commit history
git log --oneline          # One-line summary
git log --graph --oneline --all  # Graphical branch view
git log --author="Name"    # Commits by a specific author
git log -n 5               # Last 5 commits
```

**Example**:
View concise history:

```bash
git log --oneline
```

Output:

```yaml
abc1234 Add homepage
def5678 Fix login bug
```

**When to Use**:

- Review past commits.
- Find a specific commit or track contributions.

## 7. Working with Branches

### `git branch`

**Purpose**: List, create, or delete branches.

**Usage**:

```bash
git branch                 # List all branches
git branch <branch-name>   # Create a new branch
git branch -d <branch-name>  # Delete a merged branch
git branch -D <branch-name>  # Force delete a branch
```

**Example**:
Create a new branch:

```bash
git branch feature-login
```

Delete a merged branch:

```bash
git branch -d feature-login
```

**When to Use**:

- Create branches for new features or bug fixes.
- Clean up old branches after merging.

### `git checkout`

**Purpose**: Switch to a branch or commit.

**Usage**:

```bash
git checkout <branch-name>   # Switch to a branch
git checkout -b <branch-name>  # Create and switch to a new branch
git checkout <commit-hash>   # Switch to a specific commit
```

**Example**:
Switch to a branch:

```bash
git checkout feature-login
```

Create and switch:

```bash
git checkout -b feature-payment
```

**When to Use**:

- Work on a specific feature or experiment.
- Review a past commit (detached HEAD state).

### `git merge`

**Purpose**: Combine changes from one branch into the current branch.

**Usage**:

```bash
git merge <branch-name>
```

**Example**:
Merge a feature into `main`:

```bash
git checkout main
git merge feature-login
```

**When to Use**:

- Integrate completed features or fixes into the main branch.
- Resolve conflicts if they arise during merging.

## 8. Remote Repositories

### `git remote`

**Purpose**: Manage connections to remote repositories (e.g., GitHub).

**Usage**:

```bash
git remote -v                     # List remote connections
git remote add <name> <url>       # Add a new remote
git remote set-url origin <new-url>  # Change remote URL
```

**Example**:
Add a GitHub repository:

```bash
git remote add origin https://github.com/alice/my-app.git
```

Check remotes:

```bash
git remote -v
```

**When to Use**:

- Link a local repository to GitHub.
- Update or troubleshoot remote connections.

### `git push`

**Purpose**: Upload local commits to a remote repository.

**Usage**:

```bash
git push origin <branch-name>        # Push a branch
git push -u origin <branch-name>     # Push and set upstream
git push origin --delete <branch-name>  # Delete a remote branch
```

**Example**:
Push to `main`:

```bash
git push origin main
```

Push a new branch:

```bash
git push -u origin feature-login
```

**When to Use**:

- Share your changes with others.
- Create pull requests on GitHub.

### `git pull`

**Purpose**: Fetch and merge changes from a remote repository.

**Usage**:

```bash
git pull origin <branch-name>
```

**Example**:
Update `main` with remote changes:

```bash
git pull origin main
```

**When to Use**:

- Sync your local repository with the latest team changes.
- Before starting work to avoid conflicts.

### `git fetch`

**Purpose**: Download changes from a remote without merging.

**Usage**:

```bash
git fetch origin
```

**Example**:
Fetch updates without merging:

```bash
git fetch origin
```

**When to Use**:

- Check remote changes before merging.
- Review updates without affecting your local work.

## 9. Undoing Changes

### `git reset`

**Purpose**: Undo commits or unstage files.

**Usage**:

```bash
git reset HEAD <file>         # Unstage a file
git reset --soft HEAD~1       # Undo last commit, keep changes
git reset --hard HEAD~1       # Undo last commit, discard changes
git reset --hard              # Reset to last commit, discard all changes
```

**Example**:
Unstage a file:

```bash
git reset HEAD style.css
```

Undo last commit:

```bash
git reset --soft HEAD~1
```

**When to Use**:

- Fix a mistaken commit or staging.
- **Warning**: `--hard` deletes changes permanently.

### `git revert`

**Purpose**: Create a new commit that undoes a previous commit.

**Usage**:

```bash
git revert <commit-hash>
```

**Example**:
Undo a commit with hash `abc123`:

```bash
git revert abc123
```

**When to Use**:

- Safely undo changes in a shared repository without rewriting history.

### `git checkout`

**Purpose**: Discard unstaged changes in a file.

**Usage**:

```bash
git checkout -- <file-name>
```

**Example**:
Revert changes in `index.html`:

```bash
git checkout -- index.html
```

**When to Use**:

- Discard unwanted changes before staging.

## 10. Stashing Changes

### `git stash`

**Purpose**: Temporarily save uncommitted changes.

**Usage**:

```bash
git stash          # Save changes
git stash pop      # Apply and remove stashed changes
git stash list     # List all stashes
```

**Example**:
Save work and switch branches:

```bash
git stash
git checkout main
# Later:
git checkout feature-login
git stash pop
```

**When to Use**:

- Pause work to switch branches or handle urgent fixes.
- Resume work later without committing.

## 11. Comparing Changes

### `git diff`

**Purpose**: Show differences between files, commits, or branches.

**Usage**:

```bash
git diff                    # Changes in working directory
git diff --staged           # Staged changes
git diff main feature-login  # Compare branches
```

**Example**:
Check changes in `style.css`:

```bash
git diff style.css
```

**When to Use**:

- Review changes before staging or committing.
- Compare branches to understand differences.

## 12. Tagging

### `git tag`

**Purpose**: Mark a specific commit (e.g., for a release).

**Usage**:

```bash
git tag <tag-name>           # Create a tag
git push origin <tag-name>   # Push tag to remote
```

**Example**:
Tag a release:

```bash
git tag v1.0.0
git push origin v1.0.0
```

**When to Use**:

- Mark stable versions or milestones.

## 13. Resetting Repository History

### Clear All History

**Purpose**: Start a fresh repository with no commit history.

**Usage**:

```bash
cd my-project
rm -rf .git
git init
echo "Fresh start" > README.md
git add README.md
git commit -m "Initial commit"
git remote add origin <repository-url>
git push -u --force origin main
```

**Example**:
Reset a repository:

```bash
cd my-app
rm -rf .git
git init
echo "New project start" > README.md
git add README.md
git commit -m "Initial commit"
git remote add origin https://github.com/alice/my-app.git
git push -u --force origin main
```

**When to Use**:

- Remove all history for a clean start.
- **Warning**: This is destructive and should be used cautiously.

## 14. Getting Help

### `git help`

**Purpose**: Access documentation for any Git command.

**Usage**:

```bash
git help <command>
git <command> --help
```

**Example**:
Get help for `commit`:

```bash
git help commit
```

**When to Use**:

- Learn more about a command’s options.
- Troubleshoot issues.

## Best Practices for Commands

- **Commit Often**: Use `git commit` for small, logical changes (e.g., “Add login button”).
- **Clear Messages**: Write descriptive commit messages in present tense.
- **Use Branches**: Create branches (`git checkout -b`) for features or fixes.
- **Check Status**: Run `git status` frequently to avoid mistakes.
- **Pull Before Pushing**: Always `git pull` to avoid conflicts.

## Quick Reference

| Task                | Command                              |
|---------------------|--------------------------------------|
| Initialize repo     | `git init`                           |
| Clone repo          | `git clone <url>`                    |
| Check status        | `git status`                         |
| Stage changes       | `git add .` or `git add <file>`      |
| Commit changes      | `git commit -m "message"`            |
| View history        | `git log --oneline`                  |
| Create branch       | `git checkout -b <branch-name>`      |
| Merge branch        | `git merge <branch-name>`            |
| Push to remote      | `git push origin <branch-name>`      |
| Pull from remote    | `git pull origin <branch-name>`      |
| Undo changes        | `git checkout -- <file>` or `git reset` |
| Stash changes       | `git stash` and `git stash pop`      |
| View differences    | `git diff`                           |
