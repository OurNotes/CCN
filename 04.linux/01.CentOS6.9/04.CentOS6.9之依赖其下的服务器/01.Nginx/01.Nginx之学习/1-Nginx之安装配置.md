总操作流程：
- 1.[下载安装](#Nginx-01)
- 2.[配置](#Nginx-02)
- 3.[测试](#Nginx-03)

***

# <a name="Nginx-01" href="#" >下载安装</a>

```shell
yum -y install gcc gcc-c++ autoconf libjpeg libjpeg-devel libpng libpng-devel freetype freetype-devel libxml2 libxml2-devel zlib zlib-devel glibc glibc-devel glib2 glib2-devel bzip2 bzip2-devel ncurses ncurses-devel curl curl-devel e2fsprogs e2fsprogs-devel krb5-devel libidn libidn-devel openssl openssl-devel nss_ldap openldap openldap-devel openldap-clients openldap-servers libxslt-devel libevent-devel ntp libtool-ltdl bison libtool vim-enhanced 
```

> 1、安装PCRE库

[![](https://img.shields.io/badge/pcre-8.36-green.svg "pcre 8.36")](https://pan.baidu.com/s/1JHv_Hl-8SPWbpghayqgZyw)

```shell
cd ~ 

cd /usr/local

tar -zxvf pcre-*

cd pcre-8.35

./configure --prefix=/usr/local/pcre-8.35

make && make install

cd ..

pcre-config --version
```

> 2、安装zlib库

[![](https://img.shields.io/badge/zlib-1.2.8-green.svg "zlib 1.2.8")](https://pan.baidu.com/s/1fifNwLYSFjMmfoC2bPjuvg)

```shell
cd ~ 

cd /usr/local

tar -zxvf zlib-*

cd zlib-1.2.8

./configure --prefix=/usr/local/zlib-1.2.8

make && make install

cd ..

```

> 3、安装openssl

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

> 4、安装nginx

[![](https://img.shields.io/badge/nginx-1.15.8-green.svg "nginx 1.15.8")](https://pan.baidu.com/s/127WhEf1xIMF3hsrzYs9KXg)

```shell
cd ~ 

cd /usr/local

tar -zxvf nginx-*

mv nginx-1.15.8 nginx

cd nginx

./configure --with-pcre=/usr/local/pcre-8.35 --with-zlib=/usr/local/zlib-1.2.8

make && make install

/usr/local/nginx/sbin/nginx -v
```

# <a name="Nginx-02" href="#" >配置</a>

> 1、资源配置

```
cd ~ 

mkdir -p /usr/local/nginx/source/html/dist

vim /usr/local/nginx/conf/nginx.conf


```

```
    server {
        listen       81;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

        location / {
            root   /usr/local/nginx/source/html/dist;
            index  index.html;

            add_header Access-Control-Allow-Origin *;
            add_header Access-Control-Allow-Methods 'GET, POST, OPTIONS';
            add_header Access-Control-Allow-Headers 'DNT,X-Mx-ReqToken,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization';

            if ($request_method = 'OPTIONS') {
                return 204;
            }
        }
```

> 2、防火墙配置

```shell
vim /etc/sysconfig/iptables
```

放在icmp-host-prohibited上面

```shell
-A INPUT -m state --state NEW -m tcp -p tcp --dport 81 -j ACCEPT
```

```shell
service iptables restart #重启
```

>3、创建配置日记文件并且授读写执行权
```
mkdir -p /usr/local/nginx/logs
chown 777 /usr/local/nginx/logs

cd ~
cd /usr/local/nginx/logs

touch error.log
touch access.log

chown 777 error.log
chown 777 access.log

```

# <a name="Nginx-03" href="#" >测试</a>

> 1、上传项目到指定路径

> 2、开启服务器

```
cd ~

cd /usr/local/nginx/sbin

./nginx
```

- 其他命令
```
cd ~

cd /usr/local/nginx/sbin

./nginx -s stop #停止

 pkill nginx # 强制关闭

```

> 3、看效果

通过ip地址+端口查看
