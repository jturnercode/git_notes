# Git Config

## Git configuration

Three different levels of configurations:
	1. System – all users
	2. Global -  all repositories of current user
	3. Local – current repository

*Run all below from git bash command prompt*  
(must be installed on machine, see git website if you do not have installed on your system)

### Configure global email and username:

``` 
git config --global user.name "john smith"
git config --global user.email jsmith@prog.com
```

> Note: use "" (quotation marks)  when have space in text


### Configure default editor

To Configure vscode as default editor; otherwise will open with system default.  
```
git config --global core.editor "code –wait"
```


To edit global config file ".gitconfig"  

```
git config --global –e
```

### Config Line Feed 

In windows end of lines are marked by \r\n(carriage return and line feed)  
In Linux and mac they are only marked by \n  
*Need to configure core.autocrlf to make sure git process files properly*

For windows:  

```
git config --global core.autocrlf true
```

For Linux/mac:  

```
git config –global core.autocrlf input
``` 

### Configure diff tool

Diff tools help compare changes with local git repo. Below command set vscode as default diff tool.

For windows:  

```
git config --global diff.tool vscode
```

This tells git how to open vscode for diff comparing purposes via git cmd line  

```
git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"
```

### *Verify configuration changes*

```
git config --global -e
```

Should look like this in the --global file (a lot of times the LOCAL and REMOTE)


> [diff]  
> &emsp;tool = vscode  
> [difftool "vscode"]  
> &emsp;cmd = "code --wait --diff $LOCAL $REMOTE"  


### *Getting Help*

	1. Go to git website
	2. Git config --help
	3. Git config -h
