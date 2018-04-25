[参考文献](https://blog.csdn.net/m0_37886429/article/details/75009382)

总操作流程：
- 1、删除原来的yum；
- 2、下载安装；
- 3、检查；

----------

# 删除原来的yum
```
rpm -qa yum #查看是否安装过yum

rpm -qa | grep yum | xargs rpm -e --nodeps  #将所有的组件卸载掉

rpm -qa yum #查查是否卸载成功
```
# 下载安装CentOS 6
[各版本](https://blog.csdn.net/weicaijiang/article/details/78699206)
```
uname -r #查看系统版本

#下载
wget http://mirror.centos.org/centos/6/os/x86_64/Packages/yum-3.2.29-81.el6.centos.noarch.rpm
wget http://mirror.centos.org/centos/6/os/x86_64/Packages/yum-metadata-parser-1.1.2-16.el6.x86_64.rpm
wget http://mirror.centos.org/centos/6/os/x86_64/Packages/yum-plugin-fastestmirror-1.1.30-40.el6.noarch.rpm

rpm -ivh yum-*     #安装

```
# 检查
```
rpm -qa yum    #查看是否已经安装上
```