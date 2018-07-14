总操作流程：
- 1、下载安装；
- 2、配置；
- 3、测试；

***

# 下载安装

[![](https://img.shields.io/badge/liquibase-3.6.2-green.svg "liquibase 3.6.2")](https://pan.baidu.com/s/178c2fxtA_UpY9akZpR5adw)
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
