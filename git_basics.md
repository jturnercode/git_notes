
# Git Basics

## **Git Help**

Access common git commands
> git help

Pull up doc for a specific command
> git \<command\> --help

Check git version
> git --version


## **git init**

Typically if you are not cloning a remote project to a current local directory, the first step would be to initial a git repository locally. 

First create a folder on local machine that will hold files 
Initialize a directory
>git init

*Note: We can also create directory and initialize at same time*
>git init directory_name

The init command will also create a .git folder which holds all files that git uses to track history. There is no need to touch any of these files.


## **Git Workflow**

-- add info --  
Put diagram describing workflow
working dir to index(staging area) to head (commit)  




## **git status**  

The **status** command is one of the most used commands that let you know state of the local git repo. It also provides helpful information on possible next steps while working within local repository.  

>git status



## git add  

**---- todo ----**



## **git commit**  

Add changes to head

> git commit -m "message"

*Note: below command can add & commit with one line but not recommended. Use with caution*
> git commit -am "message"






## **Git log**

Show commited logs

> git log


*typical output:*
```
commit 1111cddb57fe93f0ef4ed114b126dd04b1919b81 (HEAD -> master)
Author: Thor <thor@gmail.com>
Date:   Thu Jan 13 17:58:24 2022 -0600

    adding file2.py

commit 1111c8869dd0ff5badc0116118b4b1eba355059a
Author: Iron Man <iman@gmail.com>
Date:   Thu Jan 13 17:58:06 2022 -0600

    adding file.py
```

Show in compact form

> git log --oneline

```
4dd2cdd (HEAD -> master) adding file2.py
42a5c88 adding file.py
0b56530 additional info
3cf2f71 (origin/master) adding .ipynb file
fa6818b Initial commit
```

*See 'Pretty Formats' in git log --help for many more options*

*To exit a huge log, press 'q' + enter*


