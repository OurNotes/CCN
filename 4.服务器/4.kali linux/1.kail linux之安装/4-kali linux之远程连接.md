总操作流程：
- 1、修改SSH服务默认配置
- 2、测试

***

# 修改SSH服务默认配置

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

# 测试

使用Xshell5远程连接


