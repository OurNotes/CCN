本页目录：
- 1、[在没git commit或git add时的情况下，修改了文件，返回修改前的状态](#git-01)
- 2、[在git add没git commit时的情况下，返回修改前的状态](#git-02)

----------

`注：git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。`
# <a name="git-01" href="#" >在没git commit或git add时的情况下，修改了文件，返回修改前的状态</a>
- 语法：
```
git checkout -- 文件
```
# <a name="git-02" href="#" >在git add没git commit时的情况下，返回修改前的状态</a>
### 1、回退版本
- 语法：
```
git reset HEAD 文件
```
### 2、撤销
- 语法:
```
git checkout -- 文件
```