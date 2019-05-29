总操操作流程：
- 1、下载离线包
- 2、安装
- 3、测试

***

#下载离线包

[![](https://img.shields.io/badge/百度云-rpm-green.svg "百度云 rpm")](https://pan.baidu.com/s/14PWi8TVHpCVzM7RPUM8Axw)

密钥：pgdq

# 安装

```c
rpm -ivh ppl-*
rpm -ivh cloog-ppl-*
rpm -ivh mpfr-*
rpm -ivh cpp-*
rpm -ivh libstdc++-devel-*
rpm -ivh glibc-headers-*
rpm -ivh kernel-devel-*
rpm -Uvh glibc-devel-2.12-1.107.el6.x86_64.rpm --nodeps --force
rpm -Uvh gcc-4.8.5-36.el7.x86_64.rpm --nodeps --force
rpm -Uivh kernel-headers-2.6.32-754.14.2.el6.x86_64.rpm --nodeps --force
rpm -Uvh gcc-c++-4.8.5-36.el7_6.2.x86_64.rpm --nodeps --force
```

# 测试

```c
rpm -qa | grep gcc
```