操作总流程：
- 1、[创建分支](#git-01)
- 2、[查看分支情况](#git-02)
- 3、[修改文件，使用分支提交数据](#git-03)
- 4、[切换回主分支](#git-04)
- 5、[合并分支](#git-05)
- 6、[删除分支](#git-06)
- 7、[查看分支情况](#git-07)

----------

# <a name="git-01" href="#" >创建分支</a>
- 语法：
```
git checkout -b dev
```
# <a name="git-02" href="#" >查看分支情况</a>
- 语法：
```
git branch
```
# <a name="git-03" href="#" >修改文件，使用分支提交数据</a>
```
git add readme.txt
git commit -m "branch test"
```
# <a name="git-04" href="#" >切换回主分支</a>
- 语法:git checkout master
```
git checkout master
```
# <a name="git-05" href="#" >合并分支</a>
- 语法：
```
git merge 选项 dev
```

选项：

--no-ff：可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并

# <a name="git-06" href="#" >删除分支</a>
```
git branch -d dev
```
# <a name="git-07" href="#" >查看分支情况</a>
```
git branch
```