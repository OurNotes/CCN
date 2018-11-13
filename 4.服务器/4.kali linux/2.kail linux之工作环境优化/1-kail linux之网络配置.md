总操作流程：
- 1、自动获得ip地址
- 2、建立临时的ip配置
  - 2.1、指定ip地址
  - 2.2、指定网关
  - 2.3、其他网段添加静态路由
- 3、固定的ip配置

***

# 自动获得ip地址

```shell
dhclient eth0
```

# 建立临时的ip配置

### 1、指定ip地址

```shell
ifconfig eth0 192.168.1.10/24  # 指定ip地址

ifconfig etho # 查询ip

```

### 2、指定网关（联网的）
```shell
route add default gw 192.168.1.10 # 指定网关

netstat -nr # 查询是否生效
```


### 3、添加静态路由（上网）

- 应用场景

```
kail linux下有三层交换机，三层交换机有多个网段，每个网段有自己不同的ip地址。
```

![](image/1-1.png)

> 1、命令添加

```shell
# net后面的是网关 ；/24是添加网络地址；/32是添加主机地址；  gw是添加网段地址
route add -net 192.168.1.10/24 gw 192.168.1.100 eth0

route -n # 查询路由
```

> 2、手动添加dnf服务器

```shell
vi /etc/resolv.conf
```

```shell
nameserver 8.8.8.8
nameserver 114.114.114.114
```

#  固定的ip配置

> 1、修改网卡的配置文件

- 进入配置文件

```shell
vi /etc/network/interfaces
```

- 编辑配合文件

```shell
# The primary network interface
auto eth0
allow hotplup eth0 
iface eth0 inet static                          # 设定静态
address 192.168.1.10                            # 设置ip地址
netmask 255.255.255.0                           # 设置子网掩码
network 192.168.1.1                             # 设置网关
broadcast 192.168.1.2                           # 设置网络地址
gateway 192.168.1.3                             # 设置广播地址
dns-nameservers 192.168.1.4 192.168.1.5         # 设置dns服务器

```

- 使配置

```shell
reboot #重启
```

