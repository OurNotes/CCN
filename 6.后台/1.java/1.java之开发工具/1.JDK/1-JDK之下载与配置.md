操作总流程：

----------

1、下载 
2、配置 
3、测试

----------
- 下载
下载地址：http://download.csdn.net/download/liulei3666825/9539509
`注：安装时jdk和jre安装路径要分开，如图：`
![](image/1-1.png)

- 配置
-环境变量加： 
1，新建变量名：JAVA_HOME，变量值：C:\Program Files\Java\jdk1.7.0
2，打开PATH，添加变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin
3，新建变量名：CLASSPATH，变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar

- 测试
在cmd输入
```
java -version
```
