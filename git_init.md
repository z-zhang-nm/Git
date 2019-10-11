+ 本地写了一部分的文件放到到github上进行版本管理
1. 进入项目所在文件夹，命令行执行`git init`
2. 把文件添加到暂存区 `git add .`
3. 把文件提交到本地仓库 `git commit -m "first commit"`
4. 在github上新建远程仓库
5. 关联到新建的远程仓库 `git remote add origin 远程仓库地址`
6. 如果远程库不为空，将远程库与本地同步合并 `git pull --rebase origin master`
7. `git diff`查看冲突文件并手动修改
8. 再次添加 `git add .`
9. `git rebase --continue`
10. `git commit --amend`修改提交信息
11. `git push -u origin master`最终推到远程仓库