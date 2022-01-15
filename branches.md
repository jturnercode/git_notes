# Branches


## **Core Concepts**

### *HEAD Branch*
HEAD branch is the currently active or checked out branch  
When running *git status* you will see it listed in output

> $ git status  
> On branch master  
> Your branch is up to date with 'origin/master'.

### *Local & Remote Branches*

Most of time we are working with **local branches** that reside on our local machine within our git repository.  
The **remote branches** reside on network server or cloud with services like Github.
Local branches are synced with remote branches.


## **git branch**
**branch** command is used to list, create, or delete branches


### Create new branch

> git branch \<branch_name\>
*Note: branches can only be created in local repository, then pushed to remote repo*


### List all branches

> $ git branch -a  
> \* master  
> remotes/origin/main  
> remotes/origin/master  

*Note: the active branch is noted with astrek*


### Rename a branch

