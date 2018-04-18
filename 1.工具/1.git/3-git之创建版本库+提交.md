操作总流程：
- 1、创建文件夹
- 2、[目录变成Git可以管理的仓库](#index-1)
- 3、[文件添加到仓库](#index-2)
- 4、[把文件提交到仓库](#index-3)

----------

# <span id="index-1">目录变成Git可以管理的仓库</span>
```
git init
```
`注：新建一个文件夹在里面进行“Git Bash Here”对文件夹初始化`

效果展现：
![](image/3-1.png)
# <span id="index-2">文件添加到仓库</span>
创建learngit目录，
创建readme.txt文件，添加内容如下
```
Git is a version control system.
Git is free software.
```
`注：readme.txt文件放到learngit目录下，用Notepad++编写readme.txt文件（UTF-8 without BOM格式）`
命令如下：
```
git add readme.txt
```
`注:进入到存放文件的地方执行命令`

# <span id="index-3">把文件提交到仓库</span>
```
git commit -m "wrote a readme file"
```
效果展现：
![image](image/3-2.png)