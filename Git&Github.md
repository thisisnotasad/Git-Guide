# Complete Git, GitHub & VS Code Guide

## What is Git?

Git is a version control system that tracks changes in your files. Think of it as a save system for your code that remembers every version you've ever created.

## What is GitHub?

GitHub is an online platform where you can store your Git projects (called repositories) and collaborate with others. It's like Google Drive but specifically designed for code.

## VS Code Setup for Git

### Essential Extensions

1. **GitLens** - Shows who changed what and when
2. **Git Graph** - Visual representation of your project history
3. **GitHub Pull Requests** - Manage GitHub directly from VS Code

### VS Code Git Interface

- **Source Control panel** (Ctrl+Shift+G) - Shows all file changes
- **Timeline view** - See file change history
- **Git indicators** - File status shown with letters (M=Modified, U=Untracked, D=Deleted)

## Essential Git Commands

### Initial Setup (Do Once)

```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Check your settings
git config --list
```

### Starting a Project

#### Option 1: Start from scratch

```bash
# Create a new folder and initialize Git
mkdir my-project
cd my-project
git init
```

#### Option 2: Copy existing project from GitHub

```bash
# Clone (download) a repository
git clone https://github.com/username/repository-name.git
cd repository-name
```

### Daily Workflow Commands

#### Check Status

```bash
# See what files have changed
git status
```

Shows which files are modified, added, or deleted.

#### Add Files for Tracking

```bash
# Add specific file
git add filename.txt

# Add all files in current folder
git add .

# Add all files with specific extension
git add *.js
```

#### Save Changes (Commit)

```bash
# Save changes with a message
git commit -m "Add login feature"

# Add and commit in one step
git commit -am "Fix navigation bug"
```

#### View History

```bash
# See commit history
git log

# Compact view
git log --oneline

# See changes in files
git log -p
```

### Working with Branches

#### What are branches?

Branches let you work on different features without affecting the main code. Like working on separate copies of your project.

```bash
# See all branches
git branch

# Create new branch
git branch feature-login

# Switch to a branch
git checkout feature-login

# Create and switch in one command
git checkout -b feature-payment

# Switch back to main branch
git checkout main

# Delete a branch
git branch -d feature-login
```

### Connecting to GitHub

#### Add GitHub as remote

```bash
# Connect your local project to GitHub
git remote add origin https://github.com/username/repository-name.git

# Check remote connections
git remote -v
```

#### Upload Changes

```bash
# Send changes to GitHub (first time)
git push -u origin main

# Send changes to GitHub (after first time)
git push

# Push new branch to GitHub
git push -u origin feature-login
```

#### Download Changes

```bash
# Get latest changes from GitHub
git pull

# Get changes but don't merge automatically
git fetch
```

### Handling Conflicts

When two people change the same lines, Git creates a conflict:

```bash
# After pulling, if conflicts exist:
# 1. Open conflicted files in VS Code
# 2. Choose which version to keep
# 3. Remove conflict markers (<<<<<<< ======= >>>>>>>)
# 4. Add and commit the resolved files
git add .
git commit -m "Resolve merge conflict"
```

### Useful Commands for Mistakes

#### Undo Changes

```bash
# Undo changes to a file (before adding)
git checkout -- filename.txt

# Unstage a file (after adding, before committing)
git reset HEAD filename.txt

# Undo last commit but keep changes
git reset --soft HEAD~1

# Undo last commit and lose changes (careful!)
git reset --hard HEAD~1
```

#### View Differences

```bash
# See what changed in a file
git diff filename.txt

# See staged changes
git diff --staged

# Compare branches
git diff main feature-login
```

## VS Code Git Workflow

### Visual Interface

1. **Make changes** to your files
2. **Source Control panel** shows changed files with M, U, D indicators
3. **Stage changes** by clicking + next to files
4. **Write commit message** in the text box
5. **Commit** by clicking checkmark or Ctrl+Enter
6. **Push** by clicking sync button or three dots menu

### Useful VS Code Features

- **Inline blame** - See who changed each line
- **Git timeline** - View file change history
- **Diff viewer** - Compare versions side by side
- **Merge conflict resolver** - Visual tool for resolving conflicts

## GitHub Workflow

### Creating Repository

1. Go to GitHub.com
2. Click "New repository"
3. Name it, choose public/private
4. Don't initialize if you already have local code

### Pull Requests

Pull requests let you propose changes to a project:

1. **Create branch** for your feature
2. **Make changes** and commit
3. **Push branch** to GitHub
4. **Create Pull Request** on GitHub
5. **Review and merge** when approved

### Issues

Track bugs and feature requests:

- Create issues for bugs or features
- Reference issues in commits: "Fix login bug (#123)"
- Close issues automatically: "Closes #123"

## Common Workflows

### Solo Developer

```bash
# Daily workflow
git status                 # Check what changed
git add .                  # Stage all changes
git commit -m "message"    # Save changes
git push                   # Upload to GitHub
```

### Team Collaboration

```bash
# Start new feature
git pull                   # Get latest changes
git checkout -b feature-x  # Create feature branch
# ... make changes ...
git add .
git commit -m "Add feature X"
git push -u origin feature-x
# Create Pull Request on GitHub
```

### Syncing with Team

```bash
# Regular sync
git checkout main
git pull                   # Get team's changes
git checkout feature-x
git merge main            # Bring team changes to your branch
```

## Best Practices

### Commit Messages

- Use present tense: "Add feature" not "Added feature"
- Be specific: "Fix login validation" not "Fix bug"
- Keep first line under 50 characters

### When to Commit

- Commit small, logical changes
- Don't commit broken code
- Commit before switching branches

### Branch Naming

- Use descriptive names: `feature-user-authentication`
- Use prefixes: `feature/`, `bugfix/`, `hotfix/`
- Use kebab-case: `feature-login-page`

### File Management

- Use `.gitignore` to exclude files you don't want to track
- Common exclusions: `node_modules/`, `.env`, `*.log`

## Troubleshooting

### Common Issues

#### "Repository not found"

- Check if repository URL is correct
- Verify you have access permissions

#### "Permission denied"

- Set up SSH keys or use personal access token
- Check GitHub credentials

#### "Your branch is ahead/behind"

- `git pull` to get latest changes
- `git push` to send your changes

#### "Merge conflict"

- Use VS Code's merge conflict resolver
- Manually edit files to resolve conflicts
- Add and commit resolved files

### Getting Help

```bash
# Get help for any command
git help <command>
git help commit

# Short help
git <command> --help
```

## Quick Reference

### Daily Commands

- `git status` - Check file changes
- `git add .` - Stage all changes
- `git commit -m "message"` - Save changes
- `git push` - Upload to GitHub
- `git pull` - Download from GitHub

### Branch Commands

- `git branch` - List branches
- `git checkout -b name` - Create and switch branch
- `git checkout main` - Switch to main branch
- `git merge branch-name` - Merge branch into current

### Viewing Commands

- `git log --oneline` - Compact history
- `git diff` - See changes
- `git show` - See last commit details

This guide covers everything you need to know to start using Git, GitHub, and VS Code together effectively. Practice these commands regularly, and they'll become second nature!
