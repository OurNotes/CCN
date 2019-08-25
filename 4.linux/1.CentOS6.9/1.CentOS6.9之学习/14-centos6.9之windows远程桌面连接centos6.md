本页目录：
- 1、[下载安装源](#Linux-01)
- 2、[配置文件](#Linux-02)
- 3、[设置防火墙](#Linux-03)
- 4、[测试](#Linux-04)

***

# <a name="Linux-01" href="#" >下载安装源</a>
```shell
su root   # 使用管理员用户进行安装

# 安装 Fedora 的源，方便后面使用 yum 命令来安装所需软件包
rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

# 安装源的 key
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6

# 安装 xrdp 和 vnc-server。
yum install xrdp vnc-server

```

# <a name="Linux-02" href="#" >配置文件</a>
>1、配置vncservers 
```shell
vim /etc/sysconfig/vncservers
```

- 在文件的末尾添加如下两行

```shell
VNCSERVERS="2:admin"
VNCSERVERARGS[1]="-geometry 1280x720"
```

>2、配置group文件
```shell
vim /etc/group
```

- 添加內容
```shell
admin:x:500:admin
```

> 3、配置密碼

```shell
su admin # 切換要被遠程的用戶

vncpasswd # 设置用户远程登录密码

```

- 密碼都一致

```shell
Password:******
Verify:******
```

> 4、重启xrdp 和 vcnserver 功能

```shell
su root

service vncserver stop
service vncserver start

service xrdp stop
service xrdp start
```

# <a name="Linux-03" href="#" >设置防火墙</a>

```shell
vim /etc/sysconfig/iptables
```

- 添加內容

```shell
-A INPUT -m state --state NEW -m tcp -p tcp --dport 3389 -j ACCEPT
```

- 重启防火墙

```shell
service   iptables restart
```

- 设置让 xrdp 和 vncserver 随开机加载启动

```shell
chkconfig xrdp on

chkconfig vncserver on

```

# <a name="Linux-04" href="#" >测试</a>

> 用windows远程桌面远程linux