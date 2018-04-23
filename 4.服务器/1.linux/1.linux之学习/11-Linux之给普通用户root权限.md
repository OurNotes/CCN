操作总流程：
- 1、切换到root
- 2、编辑修改配置文件
- 3、切换到普通用户

----------
# 切换到root
```
su
```
成功标准：
![](image/11-1.png)

# 编辑修改配置文件
```
visudo 或者 vi /etc/sudoers
```
修改内容：
在“root  ALL=(ALL)   ALL”这一行下面，再加入：
```
#Give dk a root authority
dk    ALL=(ALL)       ALL
```
# 切换到普通用户
```
su dk
```

[参考资料](http://blog.csdn.net/tropicofcancer9/article/details/53926920)