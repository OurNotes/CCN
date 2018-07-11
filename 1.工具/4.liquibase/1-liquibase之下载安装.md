总操作流程：
- 1、下载安装；
- 2、配置；
- 3、测试；

***

# 下载安装
[![](https://img.shields.io/badge/官网-liquibase-green.svg "官网 liquibase")](http://www.liquibase.org/download/index.html)
# 配置
### 1、配置环境变量
新建：
```
变量名：LIQUIBASE_HOME
变量值：安装的路径
```

path后添加：
```
;%LIQUIBASE_HOME%
```
### 2、添加包
在liquibase的lib文件夹下添加slf4j-api-xxxx.jar包

# 测试
```
liquibase --version
```
![](image/1-1.png)
