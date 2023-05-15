# Search for Text in all Commits

> **Scenerio:**  
> *Need to check if any sensative info is located in any commit within repo*

Use the -G flag with log command:  

```
git log -G <regex-pattern> -i
```

`-i` will ignore case.

Will return log of commits that contains string. You can use github or "-p" to confirm.

[More info from here](https://www.w3docs.com/learn-git/git-log.html)