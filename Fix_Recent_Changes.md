# Fix Recent Changes

**Important!!**
*Rewriting commit history may cause problems if others are using your remote repo!! Caution must be taken to understand possible consequences. Re-write of history should be ok before pushing to remote repo or if you are the only user on remote repo.*


## **Unstaging a Staged File**

*Scenerio: Wrong File added to staging area and need to move back to working tree.* 

```
git restore --staged file_name
```

`git reset file_name` can also be used. Restore is recommended for newer versions of git.


Restore all staged files

```
git restore . --staged
```

## **Unmodifying a Modified File in Working Tree**

After making changes to a file *(without commiting)*, you can revert changes by checking out latest version of file that has been modified.

```
git restore file_name
```


## **Amend Last Commit**

*Scenerio: replace code in lastest commit, modify lastest commit message or append file to last commit.*  

Use `--amend` commit flag to modify lastest commit. This is typically used if last commit had easy changes (typos) that you want to change without having to create a new commit.  

```
git commit --amend
```

Note:
- This only works on lastest commit, see rebase or 'Fix_Old_Commits' for more advanced options  
- **Important!:** *See note at top of document regarding changing commit history.*


Additional amend flags:
- `--no-edit` flag keeps from overwriting the last commit's message
- `-m` flag to overwrite old message with new one  

```
git commit --amend --no-edit
```

Before `--amend --no-edit`
```
4dd2cdd (HEAD -> master) adding file2.py
fa6818b Initial commit
```

After `--amend --no-edit`
```
bb46bdc (HEAD -> master) adding file2.py
fa6818b Initial commit
```

*(Note: After amend, the id of last commit changes)*

**\*\*Important: Update Remote Repo\*\***  
Once a commit is amended a git push will fail because Git will see the amended commit and the remote commit as diverged content. The `--force` option must be used to push an amended commit.

```
git push origin main --force 
```



## **Move Commit Into Aother Branch**

*Scenerio: Commit changes into master branch and intended to commit into feature branch*

First use `cherry-pick` command to copy a specifc commit to the proper branch.  
`Cherry-pick` is used to take one or more commits from an existing branch and apply them to another. This is useful if you already committed a change on one branch, and want to implement it on another branch without merging the rest of the original branch’s history.

1. Use git log --oneline.
2. Copy commit hash in master branch you need transferred to feature branch.
3. Switch to feature branch. *(git switch feature_branch)*
4. Run below cherry pick command to copy over commit to feature branch.

```
git cherry-pick \<commit_hash\>
```

5. Check if commit was transferred. *(git log --oneline)*

Using `reset` command we will reset local repo to specified state/commit hash. The effect will be "deleting" the un-wanted commit.  

6. Switch back to master branch.
7. Run reset command with preferred flag. 

Typical reset format:

```
git reset mode commit
```

This will remove the "moved" commit from master branch. See notes on common reset flags:  
- `git reset --soft hash`: Does not touch the index file or the working tree at all (but resets the head to specified commit hash, just like all modes do). *This leaves all your changed files "Changes to be committed", as git status would put it.*  
- `git reset --hard hash`: Resets the index and working tree to specified commit hash.

**IMPORTANT!!**
- *Any changes to tracked files in the working tree since last commit are discarded.*
- *Any un-tracked files or directories in the way of writing any tracked files are simply deleted.*








