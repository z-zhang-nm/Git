# 执行git push时，由于代码冲突，无法成功执行的解决方法
---
1. git pull --rebase #衍合服务器最新代码
2. git status #查看有哪些冲突的文件
3. vi 冲突文件 #打开文件后搜索<<<<<<<与>>>>>>>之间的内容，就是冲突的地方，修改冲突行，保存退出
4. git add 冲突文件 #添加修改后的文件到缓存区
5. git rebase --continue #继续rebase
6. git log #如果rebase成功，表示冲突已解决，此时可以查看log
7. git commit --amend #修改最后一次提交，包括文件与注释
8. git push #重新push提交