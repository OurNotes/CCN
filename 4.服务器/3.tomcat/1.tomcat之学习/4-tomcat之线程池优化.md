总操作流程
- 1、修改服务器允许最大约束
- 2、修改tomcat的sever.xml文件

***

# 修改服务器允许最大约束

```
ulimit -a #查询服务器允许最大约束
```

```
vim /etc/security/limits.conf
```

```
*               soft    core            65535
*               hard    rss             65535
```

# 修改tomcat的sever.xml文件

```xml
<Connector port="8089"
               protocol="HTTP/1.1"
               connectionTimeout="20000"
               maxConnections="2000"
               maxThreads="500"
               acceptCount="500"
               redirectPort="8443" />
```

