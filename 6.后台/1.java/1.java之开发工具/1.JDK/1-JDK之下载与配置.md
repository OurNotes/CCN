操作总流程：
- 1、[下载](#java-01) 
- 2、[配置](#java-02) 
- 3、[测试](#java-03) 

----------
# <a name="java-01" href="#" >下载</a>
[![](https://img.shields.io/badge/JDK-11.0.1-green.svg "JDK 11.0.1")](https://pan.baidu.com/s/1kwzu0YBNNkPla7U9mHYGpQ)


`注：安装时jdk和jre安装路径要分开，如图：`

![](image/1-1.png)

# <a name="java-02" href="#" >配置</a>
- 环境变量加： 
### 1，新建变量名：JAVA_HOME，变量值：C:\Program Files\Java\jdk1.7.0
### 2，打开PATH，添加变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin
### 3，新建变量名：CLASSPATH，变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar

# <a name="java-03" href="#" >测试</a>
在cmd输入
```shell
java -version
```
