总操作流程：
- 1、下载安装apr
- 2、tomcat的native的安装
- 3、tomcat的配置
- 4、看效果

***
# 下载安装


```shell
yum -y install gcc gcc-c++ autoconf libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel libxml2 libxml2-devel zlib zlib-devel glibc glibc-devel glib2 glib2-devel bzip2 bzip2-devel ncurses ncurses-devel curl curl-devel e2fsprogs e2fsprogs-devel krb5-devel libidn libidn-devel openssl openssl-devel nss_ldap openldap openldap-devel openldap-clients openldap-servers libxslt-devel libevent-devel ntp libtool-ltdl bison libtool vim-enhanced 
```

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

./configure --prefix=/usr/local/apr

make && make install

```

> 2、安装apr-iconv

```
cd ~

cd /usr/local

tar zxvf apr-iconv-1.2.2.tar.gz

mv apr-iconv-1.2.2 apr-iconv

cd apr-iconv

./configure --prefix=/usr/local/apr-iconv --with-apr=/usr/local/apr

make && make install
```

> 3、安装apr-util

```
cd ~

cd /usr/local

tar zxvf apr-util-1.6.1.tar.gz

mv apr-util-1.6.1 apr-util

cd apr-util

./configure --prefix=/usr/local/apr-util --with-apr=/usr/local/apr  --with-apriconv=/usr/local/apr-iconv

make && make install
```


> 4、安装PCRE库

[![](https://img.shields.io/badge/pcre-8.36-green.svg "pcre 8.36")](https://pan.baidu.com/s/1JHv_Hl-8SPWbpghayqgZyw)

```shell
cd ~ 

cd /usr/local

tar -zxvf pcre-*

cd pcre-8.35

./configure --prefix=/usr/local/pcre

make && make install

cd ..

rm -rf pcre-8.35
```

> 5、安装zlib库

[![](https://img.shields.io/badge/zlib-1.2.8-green.svg "zlib 1.2.8")](https://pan.baidu.com/s/1fifNwLYSFjMmfoC2bPjuvg)

```shell
cd ~ 

cd /usr/local

tar -zxvf zlib-*

cd zlib-1.2.8

./configure --prefix=/usr/local/zlib

make && make install

cd ..

rm -rf zlib-1.2.8
```

> 6、安装openssl

[![](https://img.shields.io/badge/openssl-1.0.1-green.svg "openssl 1.0.1")](https://pan.baidu.com/s/1byGEoY7wTBfVchWT69djeA)

```shell
cd ~ 

cd /usr/local

tar -zxvf openssl-*

cd openssl-1.1.1

./config --prefix=/usr/local/openssl -fPIC

make && make install

cd ..

rm -rf openssl-1.1.1

cd ~

mv /usr/bin/openssl /usr/bin/openssl.bak

mv /usr/include/openssl /usr/include/openssl.bak

ln -s /usr/local/openssl/bin/openssl /usr/bin/openssl
 
ln -s /usr/local/openssl/include/openssl /usr/include/openssl

ln -s /usr/local/openssl/lib/libssl.so.1.1 /usr/lib64/libssl.so.1.1

ln -s /usr/local/openssl/lib/libcrypto.so.1.1 /usr/lib64/libcrypto.so.1.1

echo “/usr/local/openssl/lib” >> /etc/ld.so.conf
 
ldconfig -v

openssl version
```

# tomcat的native的安装

```
cd /usr/local/tomcat/bin

tar zxvf tomcat-native.tar.gz

cd tomcat-native-1.2.21-src
cd native

./configure --with-apr=/usr/local/apr

make && make install

```

# tomcat的配置

> 1、修改catalina.sh

```shell
vim /usr/local/tomcat/bin/catalina.sh
```

```shell
# OS specific support.  $var _must_ be set to either true or false.
JAVA_OPTS="-server -Xms512m -Xmx1024m -Xss1024K -XX:MetaspaceSize=512m -XX:MaxMetaspaceSize=512m -XX:MaxNewSize=32m"
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/apr/lib export LD_LIBRARY_PATH
```

> 2、修改server.xml

```
vim /usr/local/tomcat/conf/server.xml
```

```xml
<Connector port="8089"
               protocol="org.apache.coyote.http11.Http11AprProtocol"
               connectionTimeout="20000"
               maxConnections="2000"
               maxThreads="500"
               acceptCount="500"
               minSpareThreads="100"
               compression="true"
               compressionMinSize="2048"
               redirectPort="8443" />
```
