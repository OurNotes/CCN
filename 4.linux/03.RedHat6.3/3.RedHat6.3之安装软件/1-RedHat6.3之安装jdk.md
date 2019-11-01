总操纵流程：
- 1、[下载安装](#RedHat6.3-01)
- 2、[配置](#RedHat6.3-02)
- 3、[测试](#RedHat6.3-03)

***
# <a name="RedHat6.3-01" href="#" >下载安装</a>

[![](https://img.shields.io/badge/3dmax--2017-含注册机-green.svg "3dmax-2017 含注册机")](https://pan.baidu.com/s/1u8NjcrluxCDvoyUis9OmXg)

提取密钥：2k2o

```shell
cd /usr/local
mkdir /usr/local/java
chmod 0777 java
tar -zxvf jdk-8u191-linux-x64.tar.gz
mv jdk1.8.0_191 jdk
chmod 0777 jdk
#将jdk移到java文件夹下
```

# <a name="RedHat6.3-02" href="#" >配置</a>
vim /etc/profile
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

# <a name="RedHat6.3-03" href="#" >测试</a>
```shell
java -version
```
