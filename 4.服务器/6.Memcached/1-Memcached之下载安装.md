总操作流程：
- 1、下载安装
- 2、测试

***

# 下载安装


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

# 测试

```
memcached -h 
```

