总操作流程：
- 1、下载
- 2、配置
- 3、测试

***

# 1、下载

[![](https://img.shields.io/badge/官网-redis-red.svg "官网 redis")](https://github.com/MicrosoftArchive/redis/releases)

# 2、配置

>修改redis.windows.conf
```c
daemonize yes

port 6666

timeout 300
```

# 3、测试

>cmd中运行

- 1、启动服务（一个cmd窗口，不能关）
```
cd C:\Software\redis

redis-server.exe redis.windows.conf
```

- 2、客户端连接（一个cmd窗口）

```
cd C:\Software\redis

redis-cli.exe -h 127.0.0.1 -p 6666

set myKey abc

get myKey
```