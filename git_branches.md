# Git Branches  

[More Info](https://www.atlassian.com/git/tutorials/using-branches)

## Core Concepts

### Head Branch
HEAD branch is the currently active or checked out branch.  
When running `git status` you will see it listed in output.

```
git status 
```        

Output:
```
 On branch master  
 Your branch is up to date with 'origin/master'.
```

> `master` is the current local branch
> `origin/master` is the remote branch in this case


### Local & Remote Branches

Most of time we are working with **local branches** that reside on our local machine within our git repository.  
The **remote branches** reside on network server or cloud with services like Github.
Local branches are synced with remote branches.


## Branch Commands

### List Local Branches

`git branch` command is used to list, create, or delete branches

```
git branch
```

Output:
```
* master
  temp
```

> *NOTE: the active branch is noted with asterisk(\*)*


### List Local and Remote Branches

```
git branch -a  
```

Output:
```
* master  
  remotes/origin/main  
  remotes/origin/master  
```

### Create New Branch

```
git branch <branch_name>
```

Note: 
1. Branches can only be created in local repository, then pushed to remote repo.
2. After creating a new branch you must `switch` to new branch before begining work.  
**See important note in section 'Switch Between Branches'.**



### Switch Between Branches

> *NOTE: if your working directory or staging area has uncommitted changes that conflict with the branch you’re checking out, Git won’t let you switch branches. It’s best to have a clean working state when you switch branches. There are ways to get around this namely, stashing and commit amending.*


When wanting to work on a specific branch, you must first checkout or switch to that branch. `git branch` will give list of all branches with the current active branch noted with '*'.

> NOTE: It is recommended to use `switch`, as it sole purpose is to select branches.

```
git switch branch_name
```

### Checkout Branch

`checkout` can also be used, but it also has a variety of uses. Switch is recommended for simple purpose of changing current branch.

```
git checkout branch_name
```


### Delete Local Branch

Delete local branch.

```
git branch -d local_branch_name
```

Git might refuse to delete your local branch when it contains commits that *have been merged into any other local branches or pushed to a remote repository. This is a very sensible rule that protects you from inadvertently losing commit data.*  


> *NOTE:* **Use Caution with below!!**  
If you want force a delete of a branch nonetheless (e.g. because you've programmed yourself into a dead end and produced commits that aren't worth keeping) you can do so with the "-D" flag:

```
git branch -D local_branch_name
```


### Push New Branch to Repo

**UN-verified, NEED TO TEST below code**
```
git push -u <remote> <branch_name>
```
We usually use the shortname for 'remote' url, typically 'origin'  

The `-u` flag creates a tracking reference for every branch that you successfully push onto the remote repository. The local branch you push is automatically linked with the remote branch. This allows you to use commands such as git pull without any arguments.  

To check existing remote links and verify shortnames use:
```
git remote -v
```


### Delete Remote Branch

To delete a remote branch, you need to use the "git push" command:
```
git push <remote> --delete <remote-branch-name<>
```

### Rename a branch
*??*


### Summary of Feature Branch Workflow

Typically when trying to a commit to another project or working for a lead that will review your work.

1. Clone project:

```
git clone git@example.com:project-name.git
```

2. Create & cheackout new feature branch:

```
git checkout -b feature_name
```

3. Write code. Commit changes:

```
git commit -am "My feature is ready"
```

4. Push your branch to remote repo:

```
git push origin feature_name
```

5. Review your code on commits page.
6. Create a merge request.

Your team lead reviews the code and merges it to the main branch.



## Merge

### Basic Merge Steps

Suppose you are ready to merge a branch back to *main* branch.  

1. First commit any changes.
2. Make sure the *main* is the head(active) branch. Run:

```
git switch main
```

3. Run `git merge`

```
git merge <branch name>
```

4. [Optional]: Delete merged branch.

```
git branch -d <branch name>
```

[See more info on merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge)



### Merge Conflicts

See link for info on dealing with merge conficts.

https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts/resolving-a-merge-conflict-using-the-command-line


## Stash

Uses:
- Put changes that are not ready to be committed aside to checkout/switch to another branch
- Apply stashed changes back later to branch
- The above steps are needed becasue you cannot switch/checkout another branch with a dirty directory.

Official Documentation:
Use git `stash` when you want to record the current state of the working directory and the index, but want to go back to a clean working directory. The command saves your local modifications away and reverts the working directory to match the `HEAD` commit.

```
git stash
```

### Stash Untracked Files

Use `-u` flag if you want to stash untracked files:

```
git stash -u
```

### Add Stash Message

Calling `git stash` without any arguments is equivalent to `git stash push`. For quickly making a snapshot, you can omit "push". In this mode, non-option arguments are not allowed to prevent a misspelled subcommand from making an unwanted stash entry.  
If optional arguments are necessary like `-m` for message `push` is required.

To add a specific message to a stash:
```
git stash push -m 'my comment'
```
> *NOTE: in the documentation, `git stash save` has been deprecated in favor of `git stash push`.*


### Stash List
View a list of stashes with `git stash list`.

```
git stash list
```

output:
```
stash@{0}: WIP on master: dcfa333 Update: markup
```

> *NOTE: above specifies a stash id of '0' for `stash@{0}: ...`*

### Stash Show

Shows the summary of the stash diffs between existing file and stashed file.

```
git stash show -p
```
`-p` is option, will show details of stashed changes. Not including will show only files that are saved in stash.


Specify a stash id to get the diff summary.
```
git stash show stash@{n}
```


### Stash Drop

Remove a single stash entry from the list of stash entries.

```
git stash drop stash@{n}
```


### Stash Pop

Remove a single stashed state from the stash list and apply it on top of the current working tree state.

Applying the state can fail with conflicts; in this case, it is not removed from the stash list. You need to resolve the conflicts by hand and call git stash drop manually afterwards.  

```
git stash pop stash@{n}
```


### Stash Apply

Now that you have saved your Git stashes on the side, you might want to “take them out from the stack” and apply them to your current working directory.

In order to apply your Git stash to your current working directory, use the `git stash apply` command and specify the stash you want to apply.

If you don’t specify any arguments to the apply command, the top of the stack will be applied.

```
git stash apply stash@{n}
```

Or:
```
git stash apply n
```

### Create Branch from Stashed Changes

Use:
- Realize current work should be on a different branch
- First save changes to a stash
- Run `git stash branch` to create and switch to new branch
- specify stash id with `stash@{n}` syntax where `n` is id number

```
git stash branch <new branch name> stash@{n}
```