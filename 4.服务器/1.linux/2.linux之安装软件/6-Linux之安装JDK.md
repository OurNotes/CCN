操作总流程：
- 1、创建目录
- 2、下载解压
- 3、设置环境变量
- 4、检查

----------
# 创建目录
```
mkdir /usr/local/java #创建目录

cd /usr/local/java #进入文件夹
```

# 下载解压
```
wget http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.tar.gz?AuthParam=1501507734_d383060f75863f03e420e46809663ad4 #下载

 mv jdk-8u144-linux-x64.tar.gz?AuthParam=1501507734_d383060f75863f03e420e46809663ad4 jdk-8u144-linux-x64.tar.gz #改名字
 
 tar -zxvf jdk-8u144-linux-x64.tar.gz #解压
```

# 设置环境变量
vi /etc/profile
```
#set java environment
JAVA_HOME=/usr/local/java/jdk1.8.0_144
JRE_HOME=/usr/local/java/jdk1.8.0_144/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH


source /etc/profile #让修改生效
```

# 检查
```
java -version
```