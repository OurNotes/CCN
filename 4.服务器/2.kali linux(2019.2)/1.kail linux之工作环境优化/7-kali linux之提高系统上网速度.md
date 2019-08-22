总操作流程：
- 1、编辑有线的
- 2、编辑无线的

-----------

# 编辑有线的

> 1、编辑tcp_ecn
```shell
echo 0 > /proc/sys/net/ipv4/tcp_ecn 
```
>  2、编辑blacklist-libnfc.conf
```
vim /etc/modprobe.d/blacklist-libnfc.conf
```
- 加入
```
blacklist ipv6
```



> 3、编辑dnsmasq.conf
```
sudo apt-get install dnsmasq
gedit /etc/dnsmasq.conf
```
- 加入
```shell
resolv-file=/etc/resolv.dnsmasq.conf
```

> 4、编辑resolv.conf
```
sudo cp /etc/resolv.conf /etc/resolv.dnsmasq.conf
vim /etc/resolv.conf
```

- 加入

```shell
nameserver 127.0.0.1
```
- 重启

```shell
sudo /etc/init.d/dnsmasq restart
```
> 5、该dhclient.conf

```
gedit /etc/dhcp/dhclient.conf
```

>6、改provider

```shell
gedit /etc/ppp/peers/provider
```

- usepeerdns前加入#
```
#usepeerdns
```

- 停止avahi-daemon

```
sudo /etc/init.d/avahi-daemon stop 
```

- 加入

```shell
prepend domain-name-servers 127.0.0.1;
```

# 编辑无线的

[![](https://img.shields.io/badge/参考文献-csdn-yellow.svg "参考文献 csdn")](https://blog.csdn.net/u012236241/article/details/89285203)

> 1、

```shell
iwconfig

sudo rmmod iwlwif

sudo modprobe iwlwifi 11n_disable=1

echo "options iwlwifi 11n_disable=1" >> /etc/modprobe.d/iwlwifi.conf
```

> 2、关闭ipv6

```

    sudo su
    echo "#disable ipv6" >> /etc/sysctl.conf
    echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
    echo "net.ipv6.conf.default.disable_ipv6 = 1" >> /etc/sysctl.conf
    echo "net.ipv6.conf.lo.disable_ipv6 = 1" >> /etc/sysctl.conf
```

- 开启bbr

```shell
apt install --install-recommends linux-generic-hwe-16.04
sudo modprobe tcp_bbr
echo "tcp_bbr" | sudo tee --append /etc/modules-load.d/modules.con
echo "net.core.default_qdisc=fq" | sudo tee --append /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" | sudo tee --append /etc/sysctl.conf
sudo sysctl -p
sysctl net.ipv4.tcp_available_congestion_control
sysctl net.ipv4.tcp_congestion_control
 lsmod | grep bbr
```