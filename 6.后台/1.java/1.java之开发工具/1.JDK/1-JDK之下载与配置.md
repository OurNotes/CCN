操作总流程：
- 1、下载 
- 2、配置 
- 3、测试

----------
# 下载
[![](https://img.shields.io/badge/JDK-1.8.0_91-green.svg "JDK 1.8.0_91")](https://pan.baidu.com/s/1zGjYRJ-6E3LIYHrhH0XGeQ)


`注：安装时jdk和jre安装路径要分开，如图：`

![](image/1-1.png)

# 配置
- 环境变量加： 
### 1，新建变量名：JAVA_HOME，变量值：C:\Program Files\Java\jdk1.7.0
### 2，打开PATH，添加变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin
### 3，新建变量名：CLASSPATH，变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar

# 测试
在cmd输入
```
java -version
```
