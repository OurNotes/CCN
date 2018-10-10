操作总流程：
- 1、[查看状态](#git-01)
- 2、[添加修改的文件到索引](#git-02)
- 3、[commit 文件](#git-03)
- 4、[远程连接](#git-04)
- 5、[提交项目](#git-05)
- 6、[断开远程仓库连接](#git-06)

----------
# <a name="git-01" href="#" >查看状态</a>
```shell
git status
```
# <a name="git-02" href="#" >添加修改的文件到索引</a>
```shell
git add *
```
# <a name="git-03" href="#" >commit 文件</a>
```shell
git commit -m "修改备注"
```
# <a name="git-04" href="#" >远程连接</a>
```shell
git remote add origin https://git.oschina.net/5333/TrainingBuildingManagementSystem.git
```
# <a name="git-05" href="#" >提交项目</a>
```shell
git push -u origin master
```
# <a name="git-06" href="#" >断开远程仓库连接</a>
```shell
git remote rm origin
```