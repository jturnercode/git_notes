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