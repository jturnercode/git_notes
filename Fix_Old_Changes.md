# Fix Old Changes

**Important!!**
*Rewriting commit history may cause problems if others are using your remote repo!! Caution must be taken to understand possible consequences. Re-write of history should be ok before pushing to remote repo or if you are the only user on remote repo.*


## **git reset**

Delete the most recent local commit without destroying un-committed work you've done:
```
git reset --soft HEAD~1
```
Delete the most recent local commit and remove all commited and **un-commited** changes. :
```
git reset --hard HEAD~1
```


## **git rebase -i**

The git rebase command is used to edit one or more existing commits in your local branch history. This command can be used to combine, edit, reorder, or remove commits. When performing an interactive rebase, indicated by adding an -i flag to the command, commit subcommands can be set in the text editor. The command must also include which commits should be rebased.
*Note: Before starting, one cannot run rebase unless you commit or stash unstaged changes*

typical format:
```
git rebase -i [branch] [HEAD~#]
```

### *Rebase Against Remote*
??
By default `git rebase -i` will compare to remote origin if avaialble.
If the commits are up to date with remote, git rebase -i will show `noop`.
```
git rebase -i
```

### *View Current Branch Commits to Rebase*

Running `git rebase -i` alone may result in output with no commits listed and one line with `noop`.
(noop = no available operations?)

If want to rebase within a selected branch then run:
```
git rebase -i HEAD~#
```

This will return the last '#' of commits specified to perform a rebase.

### *Rebase Against Another Branch*

??? Try ???
```
git rebase -i another_branch
```

## **Rebase Edit**

*Scenerio:*
- *I have used "edit" to rebase **old commits**(for recent commits see alternatives like --amend or reset) that have information i want to delete. (security-wise primarily) The only way to get rid of security issues is to re-write the history.*  
- **This operation will re-write commits(new SHA) and is not recommended if bad commits have been pushed to a shared remote repo.Caution should be used!**  

Look into other alternatives like BFG Repo-Cleaner.


1. First identify the commit you would like to edit (re-write). Use tools like git log or similar to note where issue began.
```
git log -p -#
```

2. Second backup branch you want to rebase to another branch, "temp".
```
git branch temp
```

3. Then use git rebase -i HEAD~#, to go back # of commits needed to fix the problem.
```
git rebase -i HEAD~5
```

4. When the interactive window comes up (editor window), select the hash you want to re-write by placing "edit" in front of the hash. Save and close editor. You should get below meassage:
 
You can amend the commit now, with
```
git commit --amend
```
Once you are satisfied with your changes, run
```
git rebase --continue
```

5. Git should be in an "interactive rebase" state. This can be noted by command prompt or by runnig `git status`. You will also not that running `git log --oneline` will only result in history to specified commit that you selected to edit. Opening the specified file will show only commited info at that point in history.  
Modify file as needed and save.

6. Add changes to staging and `commit --amend`
```
git add filename
git commit --ammend -m "new message"
```

7. Make sure all changes are commited. Running `git status` should note that the working tree is clean. If all good run:
```
git rebase --continue
```

8. MOST likely "Merge Conflicts" will be noted. You must fix conflicts to be able to finalize rebase. Open file and fix conflicts and save (see section on resolving conflicts if needed). You will need to mark the resolved file as complete by add to staging area. Running git rebase --continue prematurely will result in below message:

You must edit all merge conflicts and then
mark them as resolved using git add


9. Add modified file to staging area and finsih rebase with `git rebase --continue`. You can modify commit message as needed.
```
git add filename
git rebase --continue
```

10. git status should not show any more changes. git log --oneline should show all old commits again with new SHA (hash) numbers from the point of the change all way back to top commit (typically HEAD).

```
$ git log --oneline

  25d4459 (HEAD -> master) add 10
  1be6a06 add 8,9
  30530ff add 6,7
  8ed0b80 add fix.notes
  c48839f 4,5 password again
  aea977d init commit
```

11. You can compare the new hashes shown above with the ones saved in "temp" branch.  
Delete "temp" branch once you are good with changes. 

```
git branch -d
```

12. If remote repo exisit, force push.
**This will re-wirite commit hashes in repo causing problems for anyone else using repo!**

```
git push origin master --force
```


