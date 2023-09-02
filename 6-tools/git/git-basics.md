[&larr; Back](./README.md)

# Git

## Table of Content

- [Git Init]()

### External Resources

- [Git Documentation](https://git-scm.com/docs)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

<br>
 
## Git Init

Run the following command in a particular project directory to initialize a new git repository:

```
git init
```

**Git Repository (Repo):** a project directory that uses git to track changes.

## Git Workflow

A Git project can be thought of as having 3 parts:

1. **Working Directory:** where you'll be doing all the work: creating, editing, deleting and organizing files.
2. **Staging Area:** where you'll list changes you make to the working directory.
3. **Repository:** where git permanently stores those changes as different versions of the project.

**The Git Workflow** consists of editing files in the working directory -> adding files to the staging area -> saving changes to the git repository.

<br>

##

**Check the status of changes**

```
git status
```

- Files in **red** under _Untracked files_ - files on which git detected changes, but are not tracked yet.
- Files in **green** under _Changes to be commited_ - files added to the staging area.

<br>

**Add changes to the staging area**

After we made changes to a project, we **add** them to the staging area.

```
git add file.txt img.png
git add .
```

Using the dot symbol `.` we add all files from the working directory to the staging area at once.

<br>
