# Remote Repositories


## Origin

In Git, "origin" is a shorthand name for the remote repository url (alias to url of remote repo) that a project was originally cloned from. 
More precisely, it is used instead of that original repository's URL - and thereby makes referencing much easier.

Note that origin is by no means a "magical" name, but just a standard convention. Although it makes sense to leave this convention untouched, you could perfectly rename it without losing any functionality.



## Add Remote Repo

After working on a local git repo, you can use the 'remote' command to add local repo to remote repo.
First create repo in your github account.  
Then use below command to link local repo to remote repo

```
$ git remote add <name> <repository url>
```

*example: git remote add origin http(s)://github.com/reponame.*

*Note: origin is the recommended default name used primary repository on GitHub. It is not restricted and you can use your own name.*


## List Remote Info (verbose)

Will list remote connection names and URLs.

```
$ git remote -v

> origin http://fakeurl (fetch)
> origin http://fakeurl (push)
```


## Add Second Remote Repo

If you want to save local repo to two different remote repos first add the addition remote repo location using same 'remote add' command with different shorthand name:
```
$ git remote add <different_shortname> <url>
```

example:  
By convention, the original / primary remote repo is called origin. Here’s a real example:  

*Add remote 1: GitHub*
```
$ git remote add origin git@github.com:jigarius/toggl2redmine.git
```

*Add remote 2: BitBucket*
```
$ git remote add reponame2 git@bitbucket.org:jigarius/toggl2redmine.git
```



## Renaming a Remote Repo
Use the git remote rename command to rename an existing remote.

The git remote rename command takes two arguments:

* An existing remote name, for example, origin
* A new name for the remote, for example, destination

```
$ git remote rename <oldname> <newname>
```

## Remove Remote Repo

```
$ git remote rm <name>
```


## Changing a Remote Repo's URL
The git remote set-url command changes an existing remote repository URL.

```
$ git remote set-url origin https://github.com/USERNAME/REPOSITORY.git
```



# Push & Pull

## Git pull

Incorporates changes from a remote repository into the current branch.
- If the current (local) branch is behind the remote, then by default it will fast-forward the current branch to match the remote. **This will overwrite local files.**
- If the current branch and the remote have diverged, the user needs to specify how to reconcile the divergent branches with --rebase or --no-rebase (or the corresponding configuration option in pull.rebase).

```
$ git pull <remote> <branch>
```

### Pulling remote repo into local repo with exising files
pulling into local directory will possibly overwrite local repo files 

*To be able to push to your remote repository, you must ascertain that all your changes to the local repository are committed.*



## Git push
Updates remote refs using local refs  


To push the current branch and set the remote as upstream, use:
```
$ git push --set-upstream origin master
```

### Create & Push New Remote Branch
After creating a new branch and committing changes locally.
If remote branch does not exist running `git push` will result in error.

Run below to create new branch at remote repo and push changes.

```
git push --set-upstream origin <new_branch_name>
```

### Push to Specific Branch

When the command line does not specify where to push with the \<repository\> argument, branch.*.remote configuration for the current branch is consulted to determine where to push. If the configuration is missing, it defaults to origin.

```
$ git push origin --repo=<repository>
```



### Push to multiple remotes (one at time)

Simple of it is just run the push command specifying the 'remote name' & 'branch name'

*First remote repo*
```
 $ git push origin
```
*Second remote repo*
 ```
 $ git push reponame2
```



