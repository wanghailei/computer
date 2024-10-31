# Study Git

## Cancel changes

To cancel changes to the HEAD in Git and revert back to the last committed state, you can use one of the following commands, depending on the type of changes you want to undo:

### Discard uncommitted changes to tracked files

If you’ve made changes to files but haven’t committed them yet, and you want to discard all those changes:

```bash
git restore .
```

### Undo staged changes (but keep working directory changes)

If you’ve staged files for commit (added them with git add), but you want to unstage them without discarding the changes:

```bash
git reset HEAD
```

### Undo commits (keep changes in working directory)

If you want to undo the last commit but keep the changes in your working directory, use:

```bash
git reset --soft HEAD^
```

### Discard commits (lose changes)**

If you want to completely discard the last commit and lose all changes:

```bash
git reset --hard HEAD^
```

### Discard untracked files

If you want to remove untracked files (files not added to Git) from the working directory:

```bash
git clean -fd
```

### Track Files

**Tracked Files**: Files that have been added to the repository using `git add` and committed using git commit. Git keeps track of their state (unmodified, modified, staged).

- **Unmodified**: No changes since the last commit.
- **Modified**: The file has been edited but not yet staged for commit.
- **Staged**: Changes to the file have been added to the staging area, ready to be committed.

**Untracked Files**: Files that exist in your working directory but have not been added to Git’s version control system (not yet tracked). These files have not been staged for a commit, so Git doesn’t track changes made to them. Untracked files could include newly created files or files ignored by .gitignore.

**How to Track Files: When you create or modify a file, it’s initially untracked. You need to add it to Git with `git add <file>` to make Git start tracking it. After this, Git will monitor the file’s changes.