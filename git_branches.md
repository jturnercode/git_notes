# Git Branches  

List, create, or delete branches

If **--list** is given, or if there are no non-option arguments, existing branches are listed; the current branch will be highlighted in green and marked with an asterisk. Any branches checked out in linked worktrees will be highlighted in cyan and marked with a plus sign. 

Option **-r** causes the remote-tracking branches to be listed, and option **-a** shows both local and remote branches.

> git branch --list

-----
got remote and local main and master branches

**look at git branch --list -r -a**

-----


### Rename Branches

???


## switch branches


## *Delete Local Branch*

> git branch -d \<local-branch\>


Git might refuse to delete your local branch when it contains commits that *have been merged into any other local branches or pushed to a remote repository. This is a very sensible rule that protects you from inadvertently losing commit data.*  

**Use Caution with below!!**  
If you want force a delete of a branch nonetheless (e.g. because you've programmed yourself into a dead end and produced commits that aren't worth keeping) you can do so with the "-D" flag:

> git branch -D \<local-branch\>

## *Delete Remote Branch*

To delete a remote branch, you need to use the "git push" command:

> git push origin --delete \<remote-branch-name\>
