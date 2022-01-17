# Rewrite History

**Important!! Rewriting commit history may cause problems if others are using your remote repo!! Caution must be taken to understand possible consequences. Re-write of history should be ok before pushing to remote repo or if you are the only user on remote repo.**


## **git rebase -i**

*Note: cannot run rebase unless you commit or stash unstaged changes*

### Reword commit messages  

Rewrite any commit messages

> git rebase -i
>
> Select last two commits from HEAD node 
> git rebase -i HEAD~2
>
>
> Follow prompt that pops up
Rewrite pick with reword and save file
another file will popup and you will need to update the message and save file
>





### *Deleting commits*
Delete any commit

**issues with trying to remove a commit with rebase. erased current files**


$ git log --oneline
ece9dca (HEAD -> master) add rewrite_history.md
63327ad commit changes so i can rebase
006aca0 file2.py amend message
0b56530 additional info
3cf2f71 (origin/master) adding .ipynb file
fa6818b Initial commit


_pyNotes/git_notes (master)
$ git rebase -i HEAD~5
Auto-merging git_notes.ipynb
CONFLICT (content): Merge conflict in git_notes.ipynb
error: could not apply 63327ad... commit changes so i can rebase
hint: Resolve all conflicts manually, mark them as resolved with
hint: "git add/rm <conflicted_files>", then run "git rebase --continue".
hint: You can instead skip this commit: run "git rebase --skip".
hint: To abort and get back to the state before "git rebase", run "git rebase --abort".
Could not apply 63327ad... commit changes so i can rebase

 (master|REBASE 4/5)
$ git log --oneline
45b3f64 (HEAD) file2.py amend message
3cf2f71 (origin/master) adding .ipynb file
fa6818b Initial commit

