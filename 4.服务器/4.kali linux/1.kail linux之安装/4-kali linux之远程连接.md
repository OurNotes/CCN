总操作流程：
- 1、[修改SSH服务默认配置](#kail-linux-01)
- 2、[测试](#kail-linux-02)

***

# <a name="kail-linux-01" href="#" >修改SSH服务默认配置</a>

```
vim /etc/ssh/sshd_config
```
> 添加
```
PasswordAuthentication yes
PermitRootLogin yes
```

```
service ssh restart
```

# <a name="kail-linux-02" href="#" >测试</a>

使用Xshell5远程连接


