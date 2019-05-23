总操作流程：
- 1、配置环境的搭建
- 2、下载安装redis
- 3、配置reids
- 4、测试

***

# 配置环境的搭建

```
yum -y  install  rubygems  

rpm -qa |grep ruby
rpm -e --nodeps ruby-1.8.7.374-5.el6.x86_64
rpm -e --nodeps ruby-libs-1.8.7.374-5.el6.x86_64
rpm -e --nodeps rubygems-1.3.7-5.el6.noarch
rpm -e --nodeps ruby-rdoc-1.8.7.374-5.el6.x86_64
rpm -e --nodeps ruby-irb-1.8.7.374-5.el6.x86_64

tar -zxvf ruby-2.6.3.tar.gz
mv ruby-2.6.3 ruby
chown 777 ruby
cd /ruby/ruby-2.6.3
chown 777 ruby-2.6.3
./configure --with-openssl=/usr/local/openssl --with-zlib=/usr/local/zlib-1.2.8

make && make install
ruby -v
```