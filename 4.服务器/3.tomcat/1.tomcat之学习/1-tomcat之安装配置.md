总操作流程：
- 1.下载安装；
- 2.配置；
- 3.测试；

----------

# 下载安装

[![](https://img.shields.io/badge/apache--tomcat-8.0.3-green.svg "apache-tomcat 8.0.3")](https://pan.baidu.com/s/1wtiv5dr0oeW56QCFuk9evQ)


上传linux

```
tar zxvf apache-tomcat-8.0.32.tar.gz #解压文件

mv apache-tomcat-8.0.32 tomcat #修改名字
```
# 配置
```
vi /etc/profile
```

```
#set tomcat environment
CATALINA_BASE=/usr/local/tomcat
PATH=$PATH:$CATALINA_BASE/bin
export PATH CATALINA_BASE
```

```
source /etc/profile #让修改生效

catalina.sh version #查看版本
```
# 测试
```
/usr/local/tomcat/bin/startup.sh
```
![](image/1-1.png)