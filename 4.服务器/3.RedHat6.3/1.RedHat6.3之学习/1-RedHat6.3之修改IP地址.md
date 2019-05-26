操作总目录：
- 1、[修改配置文件](#RedHat6.3-01)
- 2、[测试](#RedHat6.3-02)

***

# <a name="RedHat6.3-01" href="#" >修改配置文件</a>

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

route add default  gw 10.10.2.3

vim /etc/resolv.conf
```

```
nameserver 202.106.0.20
nameserver 202.106.196.115
```

# <a name="RedHat6.3-02" href="#" >测试</a>

>ssh连接测试