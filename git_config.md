# Git Install & Config

## Install

1. Download the latest Git for [Windows installer](https://git-scm.com/download/win).

2. When you've successfully started the installer, you should see the Git Setup wizard screen. Follow the Next and Finish prompts to complete the installation. The default options are pretty sensible for most users.


## Git configuration

Three different levels of configurations:  
- System – all users
- Global -  all repositories of current user
- Local – current repository

> Note: Run all below from git bash command prompt  
> *(must be installed on machine, see git website if you do not have installed on your system)*

### Configure global username:

``` 
git config --global user.name "john smith"
```

> Note: use "" (quotation marks)  when have space in text

### Configure global email:

```
git config --global user.email jsmith@prog.com
```

### Configure default editor

To Configure vscode as default editor; otherwise will open with system default.  
```
git config --global core.editor "code –wait"
```

### Configure Line Feed 

In windows end of lines are marked by \r\n(carriage return and line feed)  
In Linux and mac they are only marked by \n  
*Need to configure core.autocrlf to make sure git process files properly*

#### For windows:  

```
git config --global core.autocrlf true
```

#### For Linux/mac:  

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


### Global config file

To verify or edit global configuration, below will open ".gitconfig" file.  

```
git config --global –e
```

Should look like below in the --global file (a lot of times the LOCAL and REMOTE)


> [diff]  
> &emsp;tool = vscode  
> [difftool "vscode"]  
> &emsp;cmd = "code --wait --diff $LOCAL $REMOTE"  


### Getting Help

	1. Go to git website
	2. Git config --help
	3. Git config -h
