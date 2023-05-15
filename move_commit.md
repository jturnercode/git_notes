# Move Commit Into Aother Branch

> *Scenerio: Commit changes into master branch and intended to commit into feature branch*

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

> **IMPORTANT!!**  
> *Any changes to tracked files in the working tree since last commit are discarded.*
> *Any un-tracked files or directories in the way of writing any tracked files are simply deleted.*