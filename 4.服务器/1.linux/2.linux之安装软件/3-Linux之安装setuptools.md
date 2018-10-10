操作总流程：
- 1、[下载安装](#Linux-01)
- 2、[测试](#Linux-02)

----------
# <a name="Linux-01" href="#" >下载安装</a>
```shell
wget --no-check-certificate https://pypi.python.org/packages/source/s/setuptools/setuptools-1.4.2.tar.gz #下载

tar -xvf setuptools-1.4.2.tar.gz #解压

rm -rf setuptools-1.4.2.tar.gz #删除安装包

cd setuptools-1.4.2 #进入文件夹

python2.7 setup.py build #编译

python2.7 setup.py install #安装

cd .. #返回上一级

rm -rf setuptools-1.4.2 #删除文件夹
```

# <a name="Linux-02" href="#" >测试</a>
```shell
easy_install --help
```