总操作流程：
- 1、[下载](#java-01) 
- 2、[配置](#java-02) 
- 3、[测试](#java-03) 

----------

# <a name="java-01" href="#" >下载tomcat7</a>
[![](https://img.shields.io/badge/官网-tomcat-red.svg "官网 tomcat")](http://tomcat.apache.org/download-70.cgi)


![](image/1-1.png)
# <a name="java-02" href="#" >配置tomcat</a>
环境变量加：
### 1，新建变量名：CATALINA_BASE，变量值：C:\tomcat
### 2，新建变量名：CATALINA_HOME，变量值：C:\tomcat
### 3，打开PATH，在尾部添加变量值：;%CATALINA_HOME%\lib;%CATALINA_HOME%\bin
# <a name="java-03" href="#" >测试</a>
### 1、开启
![](image/1-2.png)
### 2、在浏览器输入http://localhost:8080/
![](image/1-3.png)

- 如果提示错误：Unable to open the service 'Tomcat7'。cmd进入bin文件夹下运行命令。
```
service.bat install
```
