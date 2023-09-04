[&larr; Back](./README.md)

# Git Branching

Create **branches** to experiment with versions of a project. We can work with a branch only, and not affecting the **main** branch until we decide to merge our changes. Initially, the git repo has only the **main** branch.

- `git branch ` will show in which branch we are - `* main ` the asterisk is showing the current branch.

- `git branch branch_name ` create and name a new branch.

  Initially, both branches **main** and **branch_name** are identical, they share the same commit history.

- `git checkout branch_name ` switch between branches. Future commits belong to the active branch.

- `git merge branch_name ` merge a branch into the **main** branch.

- `git branch -d branch_name ` delete a branch that has merged. Use `-D` if the branch never merged into _main_.

<br>

## Overview

- `git branch ` list all branches
- `git branch branch_name ` create a new branch
- `git checkout branch_name ` switch from one branch to another
- `git merge branch_name ` merge changes from a branch to main
- `git branch -d branch_name ` delete a branch

<br>

## Merge Conflict

The merge is successful if **main** had no changes since we made a commit on **branch_name**. If **main** had a commit before we merged the branches, git doesn't know which changes to keep if they overlap. This is called a **merge conflict**.

You've made commits on separate branches that alter the same line on conflicting ways. Now, when you try to merge **branch_name** into **main**, git will ask which changes of the file to keep. Output:

```
CONFLICT (content): Merge conflict in text.txt
Automatic merge failed; fix conflicts and then commit the result.
```

We must fix the merge conflict. Open the conflicting file. Git uses markings to indicate the branches.

```
<<<<<<< HEAD
main version of line
=======
branch_name version of line
>>>>>>> branch_name
```

Here, git asks us which version of the file to keep. After we decide, we need to delete the unwanted content along the special git markup.

Now, add to the staging area and commit again. For your commit message now, type “Resolve merge conflict” to indicate the purpose of the commit.

<br>
