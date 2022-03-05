# Remote Repositories



## **git remote**

After working on a local git repo, you can use the 'remote' command to add local repo to remote repo.
First create repo in your github account.  
Then use below command to link local repo to remote repo

> *git remote add \<name\> \<repository url\>*

*example: git remote add origin https://github.com/reponame*

*Note: origin is the recommended default name used primary repository on GitHub. It is not restricted and you can use your own name.*

### **Verify remote repo**

>git remote -v


### **Renaming a remote repository**
Use the git remote rename command to rename an existing remote.

The git remote rename command takes two arguments:

* An existing remote name, for example, origin
* A new name for the remote, for example, destination

> *git remote rename \<oldname\> \<newname\>*

### **Remove remote repository**

> git remote rm \<name\>


### **Changing a remote repository's URL**
The git remote set-url command changes an existing remote repository URL.

> git remote set-url origin https://github.com/USERNAME/REPOSITORY.git




## **Git clone**
Clone is used to work with exisiting Github repo.
Clone (copy) a remote repository into a local directory.
Clones can be gathered from local or remote repositories.

### **Clone to specific folder**
Clone the repository located at ＜repo_url＞ into the folder called ＜directory＞ on the local machine.

> git clone \<repo_url\> \<directory\>



### **cloning a specific tag**
Clone the repository located at ＜repo＞ and only clone the ref for ＜tag＞.

> git clone --branch <tag> <repo>

### **shallow clone**
Clone the repository located at ＜repo＞ and only clone the 
history of commits specified by the option depth=1.
An extensive commit history may cause scaling problems such as disk space usage limits and long wait times when cloning.

> git clone -depth=1 <repo>

### **git clone branch**
The -branch argument lets you specify a specific branch to clone instead of the branch the remote HEAD is pointing to, usually the main branch.

> git clone -branch new_feature git://remoterepository.git





## **Git pull**

Incorporates changes from a remote repository into the current branch.
- If the current (local) branch is behind the remote, then by default it will fast-forward the current branch to match the remote. **This will overwrite local files.**
- If the current branch and the remote have diverged, the user needs to specify how to reconcile the divergent branches with --rebase or --no-rebase (or the corresponding configuration option in pull.rebase).

>git pull <remote> <branch>

### Pulling remote repo into local repo with exising files
pulling into local directory will possibly overwrite local repo files 

*To be able to push to your remote repository, you must ascertain that all your changes to the local repository are committed.*




## **Git push**
Updates remote refs using local refs


??To push the current branch and set the remote as upstream, use:
>git push --set-upstream origin master

### push to specific branch

When the command line does not specify where to push with the \<repository\> argument, branch.*.remote configuration for the current branch is consulted to determine where to push. If the configuration is missing, it defaults to origin.

> git push origin --repo=\<repository\>






### pushing new branch???
output from creating master branch over main branch
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/.../git_notes/pull/new/master
remote:
To https://github.com/.../git_notes.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'. 


### push errors

1. error: failed to push some refs to 'https://github.com/.../git_notes.git'
Pushed to main/master branch with result above error. This is likely due to not being recognized as owner of the repo. Need to setup remote with password locally? or submit new branch so owner can merge

read
https://archaeogeek.github.io/gettingstartedwithgit/github/pullrequest.html


