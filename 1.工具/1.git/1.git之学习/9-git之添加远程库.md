操作总流程：
- 1、在项目的托管平台创建项目
- 2、关联远程库
- 3、推送master分支的所有内容
- 4、每次本地提交后，推送最新修改

----------

# 在项目的托管平台创建项目
操作流程：
![](image/9-1.png)
# 关联远程库
语法：
```
git remote add origin https://github.com/lidekai/test.git
```
# 推送master分支的所有内容
语法：
```
git push -u origin master
```
效果展现：
![](image/9-2.png)

# 每次本地提交后，推送最新修改
语法：
```
git push origin master
```
最后的效果展现：
![](image/9-3.png)