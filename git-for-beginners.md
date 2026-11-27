# Git for Beginners: A Hands-on Tutorial

## Introduction

Git is a tool for tracking changes to files. It lets you save checkpoints, compare versions, and collaborate with other people. This tutorial walks through the basics using a terminal.

## What you need

- Git installed on your computer. Check with `git --version`.
- A terminal (such as Terminal on macOS/Linux or Git Bash on Windows).

## 1. Configure your name and email

Git records who made each commit. Set your name and email once on your computer:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

To check these settings:

```bash
git config --global --list
```

Use the email address you want associated with your commits. If you use GitHub, you can use a GitHub-provided private email address.

## 2. Create a project and start tracking it

Make a practice folder, move into it, and initialize a Git repository:

```bash
mkdir git-practice
cd git-practice
git init
```

A repository is a project folder whose history is tracked by Git. `git init` starts tracking the current folder; it does not upload anything to the internet.

## 3. Create a file and check its status

Create a small file using your editor, or run:

```bash
echo "Hello, Git!" > hello.txt
git status
```

Git should show `hello.txt` as an untracked file. `git status` is a useful command to run often: it tells you what Git sees and suggests next steps.

## 4. Stage and commit your first change

Staging selects which changes will go into the next commit. Stage the file, check the status, and commit it:

```bash
git add hello.txt
git status
git commit -m "Add greeting file"
```

A commit is a saved checkpoint with a message describing the change. Use short, specific messages, such as `Add greeting file` or `Fix spelling in introduction`.

## 5. Make another change

Append a line to the file, then review what changed:

```bash
echo "I am learning Git." >> hello.txt
git diff
```

`git diff` shows unstaged edits compared with the last commit. Stage and commit the new change:

```bash
git add hello.txt
git commit -m "Add learning note"
```

## 6. Review your history

See the recent commits in a compact format:

```bash
git log --oneline
```

Each line represents a commit. The short identifier at the start can be used to refer to that commit.

## 7. Ignore files Git should not track

Some files are generated or specific to your computer and should not be committed. Add their names or patterns to a file called `.gitignore`. For example:

```gitignore
# Temporary files
*.tmp

# Operating-system files
.DS_Store
Thumbs.db
```

Git ignores matching untracked files. A `.gitignore` rule does not automatically stop tracking a file that was already committed.

## 8. Connect to GitHub (optional)

To publish a local repository, first create an empty repository on GitHub. Then copy its HTTPS or SSH URL and add it as a remote named `origin`:

```bash
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git remote -v
```

Replace the example URL with the URL for your repository. Push the current branch to GitHub:

```bash
git branch -M main
git push -u origin main
```

You may be prompted to authenticate. Follow GitHub's current sign-in instructions; a GitHub account password is not used as a Git HTTPS password.

## 9. A simple daily workflow

For a project you already initialized, a typical cycle is:

```bash
git status                 # See what changed
git diff                   # Review edits
git add path/to/file       # Stage a specific file
git diff --staged          # Review what is staged
git commit -m "Describe change"
git push                   # Share commits with the remote, if configured
```

Prefer staging specific files (for example, `git add README.md`) rather than `git add .` until you are comfortable checking exactly what will be committed.

## Quick reference

| Command | What it does |
| --- | --- |
| `git init` | Start a repository in the current folder |
| `git status` | Show changed, staged, and untracked files |
| `git diff` | Show unstaged changes |
| `git add <file>` | Stage a file's changes for the next commit |
| `git diff --staged` | Show staged changes |
| `git commit -m "message"` | Save staged changes as a commit |
| `git log --oneline` | Show a compact commit history |
| `git push` | Send commits to a configured remote |
| `git pull` | Fetch and integrate changes from a configured remote |

## Beginner tips

- Run `git status` before and after staging changes.
- A commit only includes staged changes.
- Commits save history locally; `git push` shares commits with a remote such as GitHub.
- Read a command before running it, especially commands copied from the internet. This tutorial sticks to basic, non-destructive commands.
- If you are unsure what to do, pause and inspect `git status` and `git diff` before making more changes.
