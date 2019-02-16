操作总目录：
- 1、修改配置文件
- 2、测试

***

# 修改配置文件

```
vim /etc/sysconfig/network-scripts/ifcfg-eth0
```

```
DEVICE="eth0"
BOOTPROTO="static"
HWADDR="F8:C5:5F:E6:60:D8"
IPADDR=10.10.2.4
NETMASK=255.255.255.0
GATWAY=10.10.2.3
DNS1=10.10.2.1
DNS2=10.10.2.2
NM_CONTROLLED="yes"
ONBOOT="yes"
TYPE="Ethernet"
UUID="93e3d29a-8302-4861-b562-07f166b00481"
```

```
service network restart
```

# 测试

>ssh连接测试