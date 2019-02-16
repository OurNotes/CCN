操作流程：
- 1、[查看版本](#Linux-01)
- 2、[安装前准备，安装相关库](#Linux-02)
- 3、[下载安装](#Linux-03)
- 4、[修改python软链接指向](#Linux-04)
- 5、[查看版本](#Linux-05)
- 6、[修改yum使用的python版本](#Linux-06)
- 7、[修改环境变量](#Linux-07)

----------
# <a name="Linux-01" href="#" >查看版本</a>
```shell
python -V
```
# <a name="Linux-02" href="#" >安装前准备，安装相关库</a>
```shell
yum install gcc gcc-c++ autoconf automake

yum install openssl openssl-devel

yum install readline-devel sqlite-devel -y
#这里如果不安装readline-devel，后面编译的python将没有删除功能
#这里如果不安装sqlite-devel，后面的iPython将报错(WARNING: IPython History requires SQLite, your history will not be saved)
```

# <a name="Linux-03" href="#" >下载安装</a>
```shell
wget https://www.python.org/ftp/python/2.7.11/Python-2.7.11.tgz #下载

tar -xvzf Python-2.7.11.tgz #解压

rm -rf Python-2.7.11.tgz #删除安装包

cd Python-2.7.11 #进入文件夹里

./configure --prefix=/usr/local/python2.7 #配置

make #编译

make install #安装

cd .. #返回上一级目录

rm -rf Python-2.7.11 #删除文件夹
```

# <a name="Linux-04" href="#" >修改python软链接指向</a>
```shell
mv /usr/bin/python /usr/bin/python2.6.6.old #移动

ln -s /usr/local/python2.7/bin/python /usr/bin/python #创建链接
```
# <a name="Linux-05" href="#" >查看版本</a>
```shell
python -V
```

# <a name="Linux-06" href="#" >修改yum使用的python版本</a>
```shell
yum list #查看yun是否正常运行

vi /usr/bin/yum #修改文件
```

### 将文件头部的#!/usr/bin/python改为
```shell
#!/usr/bin/python2.6
```

# <a name="Linux-07" href="#" >修改环境变量（永久的）</a>
```shell
echo $PATH #查看路径
```

```shell
vi /etc/profile
```

### 在最尾部添加
```shell
PATH=$PATH:/usr/local/python2.7/bin
export PATH
```

```shell
source /etc/profile #使修改生效
```