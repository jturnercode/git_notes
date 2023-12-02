# Restore

## Restore Unstaged Changes

After making changes to a file _(before staging)_, you can revert changes by checking out latest version of file that has been modified.

> _Scenerios: Made changes to file and want to start over. Started making changes to file but want to pull new commit and do not have to stash file._

```
git restore <filename>
```

## Unstaging a Staged File

The `restore` command helps to unstage or even discard uncommitted local changes. On the one hand, the command can be used to undo the effects of git add and unstage changes you have previously added to the Staging Area.

> _Scenerio: Wrong File added to staging area and need to move back to working tree._

```
git restore --staged <filename>
```

`git reset file_name` can also be used. Restore is recommended for newer versions of git.

Restore all staged files

```
git restore . --staged
```

# Reset

Resetting your branch to exactly match the remote branch can be done in two steps.

In below example, the local master branch is reset to remote origin master.

```
git fetch origin
git reset --hard origin/master
```
