总操作流程：
- 1、下载安装apr
- 2、tomcat的native的安装
- 3、tomcat的配置
- 4、看效果

***
# 下载安装

[![](https://img.shields.io/badge/官网-apr-green.svg "官网 apr")](http://apache.spd.co.il/apr/https://pan.baidu.com/s/1DY1I_ivM9HpQgyZ0YyErog)


```
yum install -y expat expat-devel
```

> 1、安装apr

```
cd ~

cd /usr/local

tar zxvf apr-1.6.5.tar.gz

mv apr-1.6.5 apr

cd apr

./configure

make && make install

```

> 2、安装apr-iconv

```
cd ~

cd /usr/local

tar zxvf apr-iconv-1.2.2.tar.gz

mv apr-iconv-1.2.2 apr-iconv

cd apr-iconv

./configure --with-apr=/usr/local/apr

make && make install
```

> 3、安装apr-util

```
cd ~

cd /usr/local

tar zxvf apr-util-1.6.1.tar.gz

mv apr-util-1.6.1 apr-util

cd apr-util

./configure --with-apr=/usr/local/apr  --with-apriconv=/usr/local/apr-iconv

make && make install
```

# tomcat的native的安装

```
cd /usr/local/tomcat/bin

tar zxvf tomcat-native.tar.gz

cd tomcat-native-1.2.21-src
cd native

./configure --with-apr=/usr/local/apr  --with-apriconv=/usr/local/apr-iconv  --with-util=/usr/local/apr-util

make && make install

```

# tomcat的配置
