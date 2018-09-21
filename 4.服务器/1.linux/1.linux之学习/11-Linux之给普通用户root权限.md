操作总流程：
- 1、[切换到root](#Linux-01)
- 2、[编辑修改配置文件](#Linux-02)
- 3、[切换到普通用户](#Linux-03)

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
[![](https://img.shields.io/badge/参考文献-用户获得root权限-yellow.svg "参考文献 用户获得root权限")](http://blog.csdn.net/tropicofcancer9/article/details/53926920)
