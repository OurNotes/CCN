操作流程：
- 1、创建分支，修改文件，用分支提交
- 2、切换到主分支，修改文件（与分支的不一样），提交
- 3、合并起来（有冲突），查看冲突部分
- 4、改冲突部分
- 5、再次提交
- 6、查看分支的合并情况--日志
- 7、删除分支

----------
# 创建分支，修改文件，用分支提交
```
git checkout -b feature1 #创建分支
```
修改readme.txt文件:
```
Creating a new branch is quick AND simple.
```
```
git add readme.txt #添加到索引库中
git commit -m "AND simple" #提交
```
# 切换到主分支，修改文件（与分支的不一样），提交
```
git checkout master #切换到主分支
```
修改readme.txt文件:
```
Creating a new branch is quick & simple.
```
```
git add readme.txt #添加到索引库中
git commit -m "& simple" #提交
```
# 合并分支（有冲突），查看冲突部分
```
git merge feature1 #合并分支
git diff HEAD -- readme.txt #查看冲突部分
```
# 改冲突部分

![](image/12-1.png)

# 再次提交
```
git add readme.txt
git commit -m "conflict fixed"
```
# 查看分支的合并情况--日志
```
git log --graph --pretty=oneline --abbrev-commit
```
# 删除分支
```
git branch -d feature1
```