总操作流程
- 1、[修改服务器允许最大约束](#tomcat-01)
- 2、[修改tomcat的sever.xml文件](#tomcat-02)

***

# <a name="tomcat-01" href="#" >修改服务器允许最大约束</a>

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

# <a name="tomcat-02" href="#" >修改tomcat的sever.xml文件</a>

```
vim /usr/local/tomcat/conf/server.xml
```

```xml
<Connector port="8089"
               protocol="HTTP/1.1"
               connectionTimeout="20000"
               maxConnections="2000"
               maxThreads="500"
               acceptCount="500"
               redirectPort="8443" />
```

>其他配置
```xml
<Connector port="8089"
               protocol="HTTP/1.1"
               connectionTimeout="20000"
               maxConnections="2000"
               maxThreads="500"
               acceptCount="500"
               minSpareThreads="100"
               compression="true"
               compressionMinSize="2048"
               redirectPort="8443" />
```

```
chown 777 /usr/local/tomcat/conf/server.xml
```

