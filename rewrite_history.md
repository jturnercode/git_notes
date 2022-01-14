


## git commit --amend

Replace the **last commit** by amending a new commit. This will overwrite the last commit in history. *Note: this only works on last commit, see rebase for more advanced options*

- This is typically used if last commit had easy changes (typos) that you want to change without having to create a new commit. 

First commit changes you want to amend and then run below command
- **--no-edit** flag keeps from overwriting the last commit's message
- **-m** flag to overwrite old message with new one
> git commit --amend --no-edit


Before --amend
```
4dd2cdd (HEAD -> master) adding file2.py
fa6818b Initial commit
```

After --amend. *Note: id of last commit changes*
```
bb46bdc (HEAD -> master) adding file2.py
fa6818b Initial commit
```