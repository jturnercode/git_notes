# Git Branches  

## **Core Concepts**

### *HEAD Branch*
HEAD branch is the currently active or checked out branch  
When running *git status* you will see it listed in output

```
$ git status  

On branch master  
Your branch is up to date with 'origin/master'.
```
- 'master' is the current local branch
- 'origin/master' is the remote branch in this case


### *Local & Remote Branches*

Most of time we are working with **local branches** that reside on our local machine within our git repository.  
The **remote branches** reside on network server or cloud with services like Github.
Local branches are synced with remote branches.


## **git branch**

`git branch` command is used to list, create, or delete branches


### *List Branches*

List local branches

```
$ git branch

* master
  temp
```
*Note: the active branch is noted with asterisk* 


List all branches (local and remote), use -a flag
```
 $ git branch -a  
 
 * master  
   remotes/origin/main  
   remotes/origin/master  
```


### *Create new branch*

```
git branch branch_name
```

Note: 
1. Branches can only be created in local repository, then pushed to remote repo.
2. After creating a new branch you must 'switch' to new branch before begining work. **See important note in 'Switch between Branches'



## **Switch between Branches**

**Note if your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git won’t let you switch branches. It’s best to have a clean working state when you switch branches. There are ways to get around thisnamely, stashing and commit amending.**

<!-- TODO: Add link to stash section -->

When wanting to work on a specific branch, you must first checkout or switch to that branch. *git branch* will give list of all branches with the current active branch noted with '*'.
It is recommended to use *switch*, as it sole purpose is to select branches.

```
git switch branch_name
```

*checkout* can also be used, but it also has a variety of uses.

```
git checkout branch_name
```


## **Delete Local Branch**

```
git branch -d local_branch_name
```

Git might refuse to delete your local branch when it contains commits that *have been merged into any other local branches or pushed to a remote repository. This is a very sensible rule that protects you from inadvertently losing commit data.*  


**Use Caution with below!!**  
If you want force a delete of a branch nonetheless (e.g. because you've programmed yourself into a dead end and produced commits that aren't worth keeping) you can do so with the "-D" flag:

```
git branch -D local_branch_name
```

## **Delete Remote Branch**

To delete a remote branch, you need to use the "git push" command:

```
git push origin --delete remote-branch-name
```


## **Push branches**

**research below!**
update branch?
```
$ git push 

fatal: The current branch main has no upstream branch.
To push the current branch and set the remote as upstream, use

   git push --set-upstream origin main
```

## **Merge**


### *Merge Conflicts*

https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line


### Rename a branch
??

## **git stash**

Uses:
- Put changes that are not ready to be committed aside to checkout/switch to another branch
- Apply stashed changes back later to branch
- The above steps are needed becasue you cannot switch/checkout another branch with a dirty directory.

Official Documentation:
Use git `stash` when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the `HEAD` commit.

```
git stash
```

Use `-u` flag if you want to stash untracked files:

```
git stash -u
```

To add a specific message to a stash:
```
git stash push -m 'my comment'
```


### *List Stashed Changes*
The modifications stashed away by this command can be listed with `git stash list`

```
$ git stash list

stash@{0}: WIP on master: dcfa333 Update: markup
```
Note above specifies a stash index of '0' for *stash@{0}: ...*

### *Restore Stashed Changes*

Use `apply` to restore specific stash to working directory. Need to specify stash index. Use `git stash list` to view all stash records by index.

```
$ git stash apply stash_index
```

### *Show Stashed Changes*

```
git stash show -p stash_index
```
`-p` is option, will show details of stashed changes. Not including will show only files that are saved in stash.


### *Create Branch from Stashed Changes*

Use:
- Realize current work should be on a different branch
- First save changes to a stash
- Run `git stash branc` to create and switch to new branch

```
git stash branch branch_name stash_index
```