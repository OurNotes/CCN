操作总流程：
- 1、[下载安装](#Linux-01)
- 2、[做软连接](#Linux-02)
- 3、[更新](#Linux-03)

----------


# <a name="Linux-01" href="#" >下载安装</a>
```shell
wget https://pypi.python.org/packages/source/p/pip/pip-1.3.1.tar.gz --no-check-certificate #下载

tar -xzvf pip-1.3.1.tar.gz #解压

rm -rf pip-1.3.1.tar.gz #删除安装包

cd pip-1.3.1 #进入文件夹

python setup.py build #编译

python setup.py install #安装

cd .. #返回上一级

rm -rf pip-1.3.1 #删除文件夹
```

# <a name="Linux-02" href="#" >做软链接</a>
```shell
ln -s /usr/local/python2.7/bin/pip /usr/bin/
```

# <a name="Linux-03" href="#" >更新</a>
```shell
 pip install --upgrade pip
```