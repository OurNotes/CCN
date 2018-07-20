总操作流程：
- 1、下载安装；
- 2、创建Oracle数据库；
- 3、配置Oracle；
- 4、在navicat上使用；

***

# 下载安装
### 1、下载
[![](https://img.shields.io/badge/Oracle_win64-11gR2-green.svg "Oracle_win64 11gR2")](https://pan.baidu.com/s/1EBKkDBTzpgWdY68etnZrWw)

### 2、安装
解压点击exe文件安装

![](image/1-1.png)

![](image/1-2.png)

![](image/1-3.png)

![](image/1-4.png)


# 创建Oracle数据库
![](image/1-5.png)

![](image/1-6.png)

![](image/1-7.png)

![](image/1-8.png)

![](image/1-9.png)

# 配置Oracle
### 1、修改listener.ora文件

![](image/1-10.png)

```
	(SID_DESC =
		(SID_NAME=ORCL)
		(ORACLE_HOME=D:\Oracle11gR2\app\admin\product\11.2.0\dbhome_1)
	)
```

```
	  (CONNECT_DATA=(SERVER=DEDICATED)(SID=myOracle))
```
### 2、启动Oracle服务

控制面板 > 系统和安全 > 管理工具 > 服务

![](image/1-11.png)

# 在navicat上使用

![](image/1-12.png)