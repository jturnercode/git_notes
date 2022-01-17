# Fix Recent Changes

**Important!! Rewriting commit history may cause problems if others are using your remote repo!! Caution must be taken to understand possible consequences. Re-write of history should be ok before pushing to remote repo or if you are the only user on remote repo.**

## **Revert Un-commited File to latest version**

After making changes to a file *(without commiting)*, you can revert changes by checking out latest version of file that has been modified.

> git checkout \<file_name\>

*NOTE: Research and see if this is best practice*  



## **Amend Last Commit**

*Scenerio: *replace code in last commit, *modify last commit message or *append file to last commit.*  

Use **--amend** commit flag to modify lastest commit. This is typically used if last commit had easy changes (typos) that you want to change without having to create a new commit.  
  
*Note:*  
- *This only works on last commit, see rebase or 'Fix_Old_Commits' for more advanced options*  
- **Important!:** *See note at top of document regarding changing commit history.*

Additional amend flags:
- **--no-edit** flag keeps from overwriting the last commit's message
- **-m** flag to overwrite old message with new one  

> git commit --amend --no-edit  


Before --amend
```
4dd2cdd (HEAD -> master) adding file2.py
fa6818b Initial commit
```

After --amend. 
```
bb46bdc (HEAD -> master) adding file2.py
fa6818b Initial commit
```
*(Note: After amend, the id of last commit changes)*

**\*\*Important: Update Remote Repo\*\***  
Once a commit is amended a git push will fail because Git will see the amended commit and the remote commit as diverged content. The **--force** option must be used to push an amended commit.

> git push origin main --force 



## **Move Commit Into Aother Branch**

*Scenerio: Commit changes into master branch and intended to commit into feature branch*


