总操作流程：
- 1、[下载安装](#memcached-01)
- 2、[配置](#memcached-02)
- 3、[测试](#memcached-03)

***

# <a name="memcached-01" href="#" >下载安装</a>

> 1、安装telnet

![](image/1-1.png)

> 2、安装memcached

http://static.runoob.com/download/memcached-win64-1.4.4-14.zip



# <a name="memcached-02" href="#" >配置</a>

- 解压后，cmd管理员进入，命令：C:\Software\memcached\memcached.exe -d install

- 删除命令:C:\Software\memcached\memcached.exe -d uninstall

- 开启命令：C:\Software\memcached\memcached.exe -d start

- 关闭命令：C:\Software\memcached\memcached.exe -d start

# <a name="memcached-03" href="#" >测试</a>

```
telnet 127.0.0.1 11211
```
