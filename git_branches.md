# Git Branches  

## **Core Concepts**

### *HEAD Branch*
HEAD branch is the currently active or checked out branch  
When running *git status* you will see it listed in output

> $ git status  
```
On branch master  
Your branch is up to date with 'origin/master'.
```

### *Local & Remote Branches*

Most of time we are working with **local branches** that reside on our local machine within our git repository.  
The **remote branches** reside on network server or cloud with services like Github.
Local branches are synced with remote branches.


## **git branch**

**git branch** command is used to list, create, or delete branches

### Create new branch

> git branch \<branch_name\>

*Note:*   
*1. Branches can only be created in local repository, then pushed to remote repo.*  
*2. After creating a new branch you must switch to new branch before begining work. See 'List branches' and 'Checkout a branch' sections.*    


### *List Branches*

> $ git branch -a  
> \* master  
> remotes/origin/main  
> remotes/origin/master  

*Note: the active branch is noted with asterisk*  


### *Switch between Branches*

When wanting to work on a specific branch, you must first checkout or switch to that branch. *git branch -a* will give list of all branches with the current active branch noted with \*.
It is recommended to use **switch**, as it sole purpose is to select branches.

> git switch \<branch_name\>

**checkout** can also be used, but it also has a variety of uses.

> git checkout \<branch_name\>



### Rename a branch
??



## *Delete Local Branch*

> git branch -d \<local-branch\>


Git might refuse to delete your local branch when it contains commits that *have been merged into any other local branches or pushed to a remote repository. This is a very sensible rule that protects you from inadvertently losing commit data.*  

**Use Caution with below!!**  
If you want force a delete of a branch nonetheless (e.g. because you've programmed yourself into a dead end and produced commits that aren't worth keeping) you can do so with the "-D" flag:

> git branch -D \<local-branch\>


## *Delete Remote Branch*

To delete a remote branch, you need to use the "git push" command:

> git push origin --delete \<remote-branch-name\>



## **Push branches**

research below

```
$ git push 
fatal: The current branch main has no upstream branch.
To push the current branch and set the remote as upstream, use

   git push --set-upstream origin main
```

## **Merge**


### *Merge Conflicts*

https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line

