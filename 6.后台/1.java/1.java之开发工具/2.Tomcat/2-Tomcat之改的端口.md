操作总流程：
- 1、找到要修改的配置文件
- 2、修改端口
- 3、重启tomcat
- 4、测试

----------
# 找到要修改的配置文件
打开tomcat所在的conf文件夹的server.xml文件

# 修改端口
找到等代码：
Connector port="8080"......
将8080改为自己想改的端口，这里我改为2222保存退出；

# 重启tomcat

![](image/2-1.png)
# 测试
在浏览器输入：http://localhost:2222/

成功标准：

![](image/2-2.png)