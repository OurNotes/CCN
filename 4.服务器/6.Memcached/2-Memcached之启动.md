总操作流程：
- 1、[启动](#memcached-01)
- 2、[查看](#memcached-02)
- 3、[测试](#memcached-03)

***

# <a name="memcached-01" href="#" >启动</a>

```
yum install -y telnet

memcached  -d -u root -l 192.168.81.133 -p 2222 -c 128 -m 100 -P myPid 
```

# <a name="memcached-02" href="#" >查看</a>

```
ps -ef|grep memcached
```

# <a name="memcached-03" href="#" >测试</a>

```
telnet 192.168.81.133 2222

```

```
set runoob 0 900 9
memcached

get runoob

quit
```

