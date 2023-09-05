[&larr; Back](./README.md)

# Git Backtracking

## Table of Content

- [HEAD and Checkout](#head-and-checkout)

<br>

## HEAD and Checkout

**HEAD** is a reference to the current active branch.

**`checkout`** can be used to create branches, switch to new branches, restore files, and undo history.

- `git checkout 0321e26 ` when we checkout a particular commit, HEAD is "detached" from any branch, and it will now point to that particular commit, where you can inspect it.

- `git switch master ` reattach HEAD to a branch.

### New changes while in detached HEAD

Suppose you want to go back to an old commit and make some new changes:

- `git checkout 0321e26 ` checkout the old commit. Now in detached HEAD state.

- `git switch -c branch_name ` while in detached HEAD, make a new branch and switch to it.

  HEAD is now back to pointing at a branch reference.

- Now on the new branch, commit your new changes.

- What we did? We went back to an old commit and made a new branch based on it.

### Reference relatively previous commits

`git checkout HEAD~1 ` reference previous commits relative to a particular commit.

- `HEAD~1 ` refers to the commit before HEAD
- `HEAD~2 ` refers to 2 commits before HEAD

### Discard Changes

Restore a file in your working directory to look exactly as it did right after the last commit.

`git checkout HEAD file.txt ` this will revert file.txt's changes back to HEAD.

<br>

## Restore

- `git restore file.txt ` restore a file to the contents in the HEAD. This restores using HEAD as the default source.

- `git restore --source HEAD~1 file.txt ` restore the contents of a file to its state from the commit prior to HEAD.

<br>

## Backtracking

- `git show HEAD ` logs information about the most recent commit in the currently checked-out brach.

- `git reset HEAD file.txt ` this removes the file from the staging area.

- `git reset 5d69206 ` rewind to a previous commit. HEAD is now set to the specified previous commit.

  As input we use the first 7 SHA characters of a previous commit.

  The commit that came after the one you reset to are gone, this changes the project's repository history.

<br>

## Overview

- `git checkout HEAD file.txt ` discard changes in the working directory
- `git reset HEAD file.txt ` unstage file changes
- `git reset commit_SHA ` resets to a previous commit in your commit history.

<br>
