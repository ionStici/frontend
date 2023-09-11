[&larr; Back](./README.md)

# Forking a Repository

**Forking a Repository on GitHub** - making a copy of a repo into your own account so that you can modify the project freely.

To fork a GitHub repository - **click `Fork` on the repo page**.

## Get Updates

To get updates from the main project into our forked repository, copy the parent's project url, then in the project's terminal run:

```
git remote add upstream <url>
```

After the upstream is set to the parent repo, when we want to update the repo, use the command:

```
git fetch upstream
```

Then, our forked repo will become up to date with the parent repo.

<br>
