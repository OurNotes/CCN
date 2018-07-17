总操作流程：
- 1、下载
- 2、配置
- 3、测试

----------

# 下载tomcat7：
[![](https://img.shields.io/badge/官网-tomcat-red.svg "官网 tomcat")](http://tomcat.apache.org/download-70.cgi)


![](image/1-1.png)
# 配置tomcat：
环境变量加：
### 1，新建变量名：CATALINA_BASE，变量值：C:\tomcat
### 2，新建变量名：CATALINA_HOME，变量值：C:\tomcat
### 3，打开PATH，在尾部添加变量值：;%CATALINA_HOME%\lib;%CATALINA_HOME%\bin
# 测试
### 1、开启
![](image/1-2.png)
### 2、在浏览器输入http://localhost:8080/
![](image/1-3.png)