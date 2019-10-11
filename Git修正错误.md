+ 如果想撤销本地存储库中一个文件的修改，可以使用git checkout指令
> `$ git status`    
> $~~~~$modified:   src/string.py     
> `$ git checkout src/string.py`  
> `$ git status`  
> $~~~~$nothing to commit, working directory clean
---
+ 假如从本地存储库中删除了一个文件，我们想要恢复这个文件
> `$ rm string.py`    
> `$ git status -s`   
> $~~~~$D string.py   
> `$ git checkout string.py`  
> `$ git status`  
> $~~~~$nothing to commit, working directory clean
---
+ 执行`git add`操作时，文件将从本地存储库移动到暂存区域，如果用户意外修改文件并将其添加到暂存区域，则可以使用git checkout命令恢复其更改
+ Git中，有一个HEAD指针总是指向最新的提交，如果要从暂存区域撤消更改，则可以使用git checkout命令，但是使用checkout命令，必须提供一个附加参数，即HEAD指针，附加的提交指针参数指示git checkout命令重置工作树
> `$ git status`  
> $~~~~$modified:   string.py  
> `$ git add string.py`  $~~~~$将文件添加到暂缓区  
> `$ git checkout head -- string.py`  $~~~~$使用`git checkout`命令恢复该文件
---
+ 用`--soft`选项后跟提交ID的Git reset命令，那么它将仅重置HEAD指针而不会破坏任何东西
+ `git/refs/heads/master`文件存储HEAD指针的提交ID，可使用`git log -1`命令验证它
> `$ cat .git/refs/heads/master`  
> $~~~~$ 44ea8e47307b47c9a80b44360e09f973e79312b0  
> `$ git log -2`  
> $~~~~$ commit 44ea8e47307b47c9a80b44360e09f973e79312b0  
> $~~~~~~~~~~~~~~~~$ add new file string.py  
> $~~~~$ commit 7d8162db36723b8523c56ad658a07808ae7fb64c  
> $~~~~~~~~~~~~~~~~$ remove/delete module.py  
> `$ git reset --soft 7d8162db36723b8523c56ad658a07808ae7fb64c`  
> `$ cat .git/refs/heads/master`  
> $~~~~$ 7d8162db36723b8523c56ad658a07808ae7fb64c  
> `$ git log -2`  
> $~~~~$ commit 7d8162db36723b8523c56ad658a07808ae7fb64c  
> $~~~~~~~~~~~~~~~~$ remove/delete module.py  
> $~~~~$ commit 6bdbf8219c60d8da9ad352c23628600faaefbe13  
> $~~~~~~~~~~~~~~~~$ renamed main.py to module.py
---
+ 使用`--hard`选项与Git重置命令，它将清除分段区域，它会将HEAD指针重置为特定提交ID的最新提交，并删除本地文件更改