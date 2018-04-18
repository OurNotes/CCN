操作总流程：
- 1、查看状态；
- 2、添加修改的文件到索引
- 3、commit 文件
- 4、远程连接
- 5、提交项目
- 6、断开远程仓库连接

----------
# 查看状态；
```
git status
```
# 添加修改的文件到索引
```
git add *
```
# commit 文件
```
git commit -m "修改备注"
```
# 远程连接
```
git remote add origin https://git.oschina.net/5333/TrainingBuildingManagementSystem.git
```
# 提交项目
```
git push -u origin master
```
# 断开远程仓库连接
```
git remote rm origin
```