# Restore


## Unstaging a Staged File

> *Scenerio: Wrong File added to staging area and need to move back to working tree.* 

The `restore` command helps to unstage or even discard uncommitted local changes. On the one hand, the command can be used to undo the effects of git add and unstage changes you have previously added to the Staging Area.

```
git restore --staged file_name
```

`git reset file_name` can also be used. Restore is recommended for newer versions of git.


Restore all staged files

```
git restore . --staged
```

## Restore a Modified File in Working Tree

After making changes to a file *(before staging)*, you can revert changes by checking out latest version of file that has been modified.

```
git restore file_name
```










