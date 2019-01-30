总操作流程：
- 1、[下载安装](redis-01)
- 2、[配置](redis-02)
- 3、[测试](redis-03)

***

# <a name="redis-01" href="#" >下载安装</a>

[![](https://img.shields.io/badge/官网-Redis-red.svg "官网 Redis")](https://github.com/MicrosoftArchive/redis/releases)

# <a name="redis-02" href="#" >配置</a>

>1、环境变量加： 

- REDIS_HOME：C:\software\Redis
- 打开PATH，添加变量值:%REDIS_HOME%

>2、设置成windows下的服务
```
cd C:\software\Redis #进入安装目录

redis-server --service-install redis.windows-service.conf --loglevel verbose
```

![](iamge/1-1.png)

# <a name="redis-03" href="#" >测试</a>

开启服务：redis-server --service-start

停止服务：redis-server --service-stop

![](iamge/1-2.png)
