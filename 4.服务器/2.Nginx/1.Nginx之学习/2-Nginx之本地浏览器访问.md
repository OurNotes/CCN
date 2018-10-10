总操作流程：
- 1、[修改配置](#Nginx-01)
- 2、[测试](#Nginx-02)

----------

# <a name="Nginx-01" href="#" >修改配置</a>
```shell
vim /etc/sysconfig/iptables
```
放在icmp-host-prohibited上面
```shell
-A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -j ACCEPT
```

```shell
service iptables restart #重启
```
# <a name="Nginx-02" href="#" >测试</a>
浏览器输入ip：192.168.23.131

![](image/2-1.png)
