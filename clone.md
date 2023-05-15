
# Git clone
Clone is used to work with exisiting Github repo.
Clone (copy) a remote repository into a local directory.
Clones can be gathered from local or remote repositories.


## Clone

Basic command to clone a repo to local machine.
```
$ git clone <repo_url>
```

## Clone to Specific Folder
Clone the repository located at `＜repo_url＞` into the folder called `＜directory＞` on the local machine. If the `<directory>` does not exisit it will be created. 

```
$ git clone <repo_url> <directory>
```

## Clone Branches

`git clone` does not clone branches in repo.

Running `git branch -a` should show only one local branch for an initial clone of a directory.

Use below to checkout remote branch:

```
$ git checkout --track <origin/branch_name>
```


## Cloning a Specific Tag
Clone the repository located at ＜repo＞ and only clone the ref for ＜tag＞.

```
$ git clone --branch <tag> <repo>
```

## Shallow Clone
Clone the repository located at ＜repo＞ and only clone the 
history of commits specified by the option depth=1.
An extensive commit history may cause scaling problems such as disk space usage limits and long wait times when cloning.

```
$ git clone -depth=1 <repo>
```

## Clone Branch Excluding Head Branch
The -branch argument lets you specify a specific branch to clone instead of the branch the remote HEAD is pointing to, usually the main branch.

```
$ git clone -branch new_feature git://remoterepository.git
```

