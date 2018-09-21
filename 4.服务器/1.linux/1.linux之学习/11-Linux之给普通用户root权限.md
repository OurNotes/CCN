操作总流程：
- 1、[切换到root](#Linux-01)
- 2、[编辑修改配置文件](#Linux-02)
- 3、[切换到普通用户](#Linux-03)

----------
# <a name="Linux-01" href="#" >切换到root</a>
```
su
```
成功标准：

![](image/11-1.png)

# <a name="Linux-02" href="#" >编辑修改配置文件</a>
```
visudo 或者 vi /etc/sudoers
```
修改内容：
在“root  ALL=(ALL)   ALL”这一行下面，再加入：
```
#Give dk a root authority
dk    ALL=(ALL)       ALL
```
# <a name="Linux-03" href="#" >切换到普通用户</a>
```
su dk
```
[![](https://img.shields.io/badge/参考文献-用户获得root权限-yellow.svg "参考文献 用户获得root权限")](http://blog.csdn.net/tropicofcancer9/article/details/53926920)
