总操作流程：
- 1、[下载安装](#memcached-01)
- 2、[测试](#memcached-02)

***

# <a name="memcached-01" href="#" >下载安装</a>


> 1、安装libevent

```
yum install libevent libevent-devel 

rpm -qa |grep libevent
```
> 2、安装memcached

```
yum install memcached

rpm -qa |grep memcached
```

# <a name="memcached-02" href="#" >测试</a>

```
memcached -h 
```

