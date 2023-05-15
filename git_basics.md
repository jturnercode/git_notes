
# Git Basics

## git Workflow

Git has three main states that your files can reside in: modified, staged, and committed:
- Modified means that you have changed the file but have not committed it to your database yet.
- Staged means that you have marked a modified file in its current version to go into your next commit snapshot.
- Committed means that the data is safely stored in your local database.

This leads us to the three main sections of a Git project: the working tree, the staging area, and the Git directory.  
<--- **add diagram describing workflow** --->


### Working Tree (Working Directory)
Typically noted as the working directory, is where all working files and folders live.


### Staging Area (Index)
The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit. Its technical name in Git parlance is the “index”, but the phrase “staging area” works just as well.


### Git Directory

The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.

The basic Git workflow goes something like this:  

1. You modify files in your working tree.
2. You selectively stage just those changes you want to be part of your next commit, which adds only those changes to the staging area.
3. You do a commit, which takes the files as they are in the staging area and stores that snapshot permanently to your Git directory.  

git compresses files very well and does not store duplicate content.  


## git help
Access common git commands.

```
git help
```


Pull up doc for a specific command.
```
git <command> --help
```

## git version  
Check git version
 ```
 git --version
 ```


## git init  
Typically if you are not cloning a remote project to a current local directory, the first step would be to initial a git repository locally. 

First create a folder on local machine that will hold files.   
Initialize a directory

```
git init
```

> *Note: We can also create directory and initialize at same time*
```
git init <directory_name>
```

The init command will create a .git folder which holds all files that git uses to track history. There is no need to touch any of these files.

## Ignoring Files

The `.gitignore` file stores a list of files, file types, or directories git should ignore while staging or commiting; ie git status will not track changes if listed in file.  

Rules:  
- Use `#` to add notes in file.
- Use `*` as a wildcard for describing general file names or types.
- File should be named `.gitignaore` and at min be placed inside root of file system where repo is initiated.

Example contents of `.gitignore`:
```
# ignore Logs folder
Logs/

# ignore these file
File1.txt
image.jpg

# ignore all .txt files
*.txt
```
> Note: To get .gitignore templates for different languages, go to github/gitignore repository; download file for language as a starting point

##  git status  

The `status` command is one of the most used commands that let you know state of the local git repo. It also provides helpful information on possible next steps while working within local repository.  

```
git status
```

For summarized version:

```
git status -s
```

## git add  

Use `add` command to move files to staging area (also called index)

Add all files
```
git add .
```

Add a specific file(s)
```
git add file1.txt file2.txt
```


## git commit 

Add changes to head

```
git commit -m "message"
```

> *Note: Below command will add & commit all files in working tree with one line. This is not not recommended, use with caution!*

```
git commit -am "message"
```

## Renaming files  
Rename file for git; updates directory and staging area at same time

> *Important to do it this way to keep commit history of renamed files*

```
git mv file_A.txt file_B.txt
```
Remember to commit file rename change as needed.


## Removing files  

To remove files from local directory and staging area  
```
git rm file_name
```

Then commit this change to update repository  
```
git commit –m "deleted file_name"
```

## Untrack Committed File  

File that has been wrongly committed but don't want to remove from directory.

```
$ git rm --cached <filename>
```


## Untrack Committed Folder

```
$ git rm -r --cached <folder>
```

## git log

Show commited logs history in console.

```
git log
```

> *TIP! To exit a huge log, press 'q' + enter*

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

Show in compact form:

```
git log --oneline
```

```
4dd2cdd (HEAD -> master) adding file2.py
42a5c88 adding file.py
0b56530 additional info
3cf2f71 (origin/master) adding .ipynb file
fa6818b Initial commit
```
> *Extra: See 'Pretty Formats' in git log --help for many more options*


To view differences between each commit while using the log command, use the `--patch` or `-p` option:


```
git log -p -3
```
> *Note: The "-3" denotes it will show only the last 3 commits.* 



## git show

Use `git show` to inspect a single commit.

```
git show <commit_hash>
```
[More ways to review commits here](https://git-scm.com/book/en/v2/Git-Tools-Revision-Selection)


