总操作流程：
- 1、下载
- 2、配置
- 3、测试

*** 

# 下载

[![](https://img.shields.io/badge/百度云-jdk-green.svg "百度云 jdk")](https://pan.baidu.com/s/14RvLo-ZZX1ocE0AcSdIvVA)

密钥：ttyv

# 配置

> 1、解压

```shell

cd /usr/local

mkdir /usr/local/java

chmod 0777 java

tar -zxvf jdk-8u191-linux-x64.tar.gz

mv jdk1.8.0_191 jdk

chmod 0777 /usr/local/java/jdk

```

> 2、环境变量配置

```
vim /etc/profile
```

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

> 3、通知系统java的位置

```shell
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk/bin/javaws" 1
```

> 4、设置默认JDK

```shell
sudo update-alternatives --set java /usr/local/java/jdk/bin/java
sudo update-alternatives --set javac /usr/local/java/jdk/bin/javac
sudo update-alternatives --set javaws /usr/local/java/jdk/bin/javaws
```



# 测试

```shell
java -version

```