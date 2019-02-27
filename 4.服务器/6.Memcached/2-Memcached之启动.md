总操作流程：
- 1、启动
- 2、查看

***

# 启动

```
yum install -y telnet

memcached  -d -u root -l 192.168.81.133 -p 2222 -c 128 -m 100 -P myPid 
```

# 查看

```
ps -ef|grep memcached

telnet 192.168.81.133 2222
```

