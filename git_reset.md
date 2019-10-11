+ Git分为三个区：
1. 工作区（Working Directory）：没有修改或修改后未使用git add的文件
2. 暂存区（Staged）：新增或修改后的文件调用git add后都会被添加到暂存区
3. 提交区（Commit）：所有添加到暂存区里的文件通过git commit之后会被统一添加到提交区，作为一次提交
![三区之间的关系](../images/relationship.webp)