[&larr; Back](./README.md)

# Git

## Resources

- [Git Documentation](https://git-scm.com/docs)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

<br>
 
## Git Init

Run the following command in a particular project directory to initialize a new git repository:

```
git init
```

**Git Repository (Repo)** is a project directory that uses git to track changes.

_p.s._ Do not initiate a git repo inside of a repo, because git tracks a directory and all nested subdirectories. Use `git status` to verify if you are not currently inside of a repo.

<br>

## Git Workflow

A Git project can be thought of as having 3 parts:

1. **Working Directory:** where we are currently working on the project, before git tracking.
2. **Staging Area:** where you'll list changes you make to the working directory.
3. **Repository:** where git permanently stores those changes as different versions of the project.

<br>

## Git Basic Commands

- **`git status `** check the status of current changes

  This command will show us files that contain changes but are not yet tracked, as well as files added to the staging area.

- **`git add file.txt `** after making changes to the project, we add them to the staging area.

  Use the dot `.` instead of specific files to stage all changes at once.

- **`git diff file.txt `** check the difference between the working directory and the staging area.

- **`git commit -m "Style Hero" `** A commit saves the changes from the staging area to the repo as a new version.

  Every commit is identified with a message that we write in quotation marks after the `-m` flag.

  _Messages:_ Atomic Commits, Write in the present tense, Meaningful and Concise messages.

- **`git log `** view a repository's commits. Use `--oneline` flag for concise details.

<br>

## Overview

- `git init` creates a new Git repository
- `git status` inspects the contents of the working directory and staging area
- `git add` adds files from the working directory to the staging area
- `git diff` shows the difference between the working directory and the staging area in a file
- `git commit` permanently stores file changes from the staging area in the repository
- `git log` shows a list of all previous commits

<br>
