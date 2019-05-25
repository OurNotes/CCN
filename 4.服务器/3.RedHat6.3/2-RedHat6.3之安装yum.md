总操作流程：
- 1、[下载包](#RedHat6.3-01)
- 2、[安装](#RedHat6.3-02)
- 3、[测试](#RedHat6.3-03)

***

# <a name="RedHat6.3-01" href="#" >下载包</a>

- 163

[![](https://img.shields.io/badge/163-包-red.svg "163 包")](http://mirrors.163.com/centos/6/os/x86_64/Packages/)


- 百度云

[![](https://img.shields.io/badge/百度云-包-red.svg "百度云 包")](https://pan.baidu.com/s/12jZRpgjPEGVTj7U6IceFSw)


# <a name="RedHat6.3-02" href="#" >安装</a>

>1、安装

```
rpm -Uvh python-urlgrabber-3.9.1-11.el6.noarch.rpm

rpm -ivh yum-* 
```

>2、切换源
```
cd /etc/yum.repos.d
cp rhel-source.repo rhel-source.repo_bak
vim /etc/yum.repos.d/rhel-source.repo
```

```c
# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client.  You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the 
# remarked out baseurl= line instead.
#
#

[base]
name=CentOS-6 - Base - 163.com
baseurl=http://mirrors.163.com/centos/6/os/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os
gpgcheck=0
gpgkey=http://mirrors.163.com/centos/RPM-GPG-KEY-CentOS-6

#released updates 
[updates]
name=CentOS-6 - Updates - 163.com
baseurl=http://mirrors.163.com/centos/6/updates/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates
gpgcheck=0
gpgkey=http://mirrors.163.com/centos/RPM-GPG-KEY-CentOS-6

#additional packages that may be useful
[extras]
name=CentOS-6 - Extras - 163.com
baseurl=http://mirrors.163.com/centos/6/extras/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras
gpgcheck=0
gpgkey=http://mirrors.163.com/centos/RPM-GPG-KEY-CentOS-6

#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-6 - Plus - 163.com
baseurl=http://mirrors.163.com/centos/6/centosplus/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus
gpgcheck=0
enabled=0
gpgkey=http://mirrors.163.com/centos/RPM-GPG-KEY-CentOS-6

#contrib - packages by Centos Users
[contrib]
name=CentOS-6 - Contrib - 163.com
baseurl=http://mirrors.163.com/centos/6/contrib/$basearch/
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib
gpgcheck=0
enabled=0
gpgkey=http://mirrors.163.com/centos/RPM-GPG-KEY-CentOS-6

```

>3、清理
```
/usr/bin/python2.6 /usr/bin/yum makecache
/usr/bin/python2.6 /usr/bin/yum clean all
```

# <a name="RedHat6.3-03" href="#" >测试</a>
```
/usr/bin/python2.6 /usr/bin/yum update
```
