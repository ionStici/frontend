[&larr; Back](./README.md)

# Git

## Table of Content

- [Git Init](#git-init)
- [Git Workflow](#git-workflow)

### External Resources

- [Git Documentation](https://git-scm.com/docs)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

<br>
 
## Git Init

Run the following command in a particular project directory to initialize a new git repository:

```
git init
```

**Git Repository (Repo):** is a project directory that uses git to track changes.

<br>

## Git Workflow

A Git project can be thought of as having 3 parts:

1. **Working Directory:** where you'll be doing all the work: creating, editing, deleting and organizing files.
2. **Staging Area:** where you'll list changes you make to the working directory.
3. **Repository:** where git permanently stores those changes as different versions of the project.

**The Git Workflow** consists of editing files in the working directory -> adding files to the staging area -> saving changes to the git repository.

<br>

### status

Check the status of changes

```
git status
```

- Files in **red** under _Untracked files_ - files on which git detected changes, but are not tracked yet.
- Files in **green** under _Changes to be commited_ - files added to the staging area.

<br>

### add

After we made changes to a project, we **add** them to the staging area.

```
git add file.txt img.png
git add .
```

Using the dot symbol `.` we add every file from the working directory to the staging area at once.

<br>

### diff

Check the differences of changes between the working directory and the staging area.

```
git diff file.txt
```

<br>

### commit

```
git commit -m "Add Header"
```

A commit stores changes from the staging area, inside the repository as a new version.

Every commit is identified with a message that we write in quotation marks after the `-m` flag.

Commit messages convention: Write in the present tense, 50 characters or less.

<br>

### log

Commits are stored chronologically in the repository and cab be viewed with:

```
git log
git log --oneline
```

<br>

### Generalizations

Git is the industry-standard version control system for web developers.

- `git init` creates a new Git repository
- `git status` inspects the contents of the working directory and staging area
- `git add` adds files from the working directory to the staging area
- `git diff` shows the difference between the working directory and the staging area in a file
- `git commit` permanently stores file changes from the staging area in the repository
- `git log` shows a list of all previous commits

<br>
