操作总流程：
- 1、[创建目录](#Linux-01)
- 2、[下载解压](#Linux-02)
- 3、[设置环境变量](#Linux-03)
- 4、[检查](#Linux-04)

----------
# <a name="Linux-01" href="#" >创建目录</a>
```shell
mkdir /usr/local/java #创建目录

cd /usr/local/java #进入文件夹

chown 777 java
```

# <a name="Linux-02" href="#" >下载解压</a>
[![](https://img.shields.io/badge/jdk-1.8.0_144-green.svg "源代码 1.8.0_144")](https://pan.baidu.com/s/1hY4AuGNuZjrCDdZx7ZmmKg)

```
 tar -zxvf jdk-8u144-linux-x64.tar.gz #解压
 
 mv jdk-1.8.0_144 jdk
 
 chown 777 jdk
```

# <a name="Linux-03" href="#" >设置环境变量</a>
vi /etc/profile
```shell
#set java environment
JAVA_HOME=/usr/local/java/jdk
JRE_HOME=/usr/local/java/jdk/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH
```

```shell
source /etc/profile #让修改生效
```

# <a name="Linux-04" href="#" >检查</a>
```shell
java -version
```
