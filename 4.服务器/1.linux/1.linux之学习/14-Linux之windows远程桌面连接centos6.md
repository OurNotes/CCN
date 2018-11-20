本页目录：
- 1、下载安装源
- 2、配置文件
- 3、设置防火墙
- 4、测试

***

# 下载安装源
```
su root   # 使用管理员用户进行安装

# 安装 Fedora 的源，方便后面使用 yum 命令来安装所需软件包
rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm

# 安装源的 key
rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-6

# 安装 xrdp 和 vnc-server。
yum install xrdp vnc-server

```

# 配置文件
>1、配置vncservers 
```
vi /etc/sysconfig/vncservers
```

- 在文件的末尾添加如下两行

```
VNCSERVERS="2:admin"
VNCSERVERARGS[1]="-geometry 1280x720"
```

>2、配置group文件
```
vi /etc/group
```

- 添加內容
```
admin:x:500:admin
```

> 3、配置密碼

```
su admin # 切換要被遠程的用戶

vncpasswd # 设置用户远程登录密码

```

- 密碼都一致

```
Password:******
Verify:******
```

> 4、重启xrdp 和 vcnserver 功能

```
su root

service vncserver stop
service vncserver start

service xrdp stop
service xrdp start
```

# 设置防火墙

```
vi /etc/sysconfig/iptables
```

- 添加內容

```
-A INPUT -m state --state NEW -m tcp -p tcp --dport 3389 -j ACCEPT
```

- 重启防火墙

```
service   iptables restart
```

- 设置让 xrdp 和 vncserver 随开机加载启动

```
chkconfig xrdp on

chkconfig vncserver on

```

# 测试

> 用windows远程桌面远程linux