操作总流程：
- 1、下载安装
- 2、测试

----------
# 下载安装
```
wget --no-check-certificate https://pypi.python.org/packages/source/s/setuptools/setuptools-1.4.2.tar.gz #下载

tar -xvf setuptools-1.4.2.tar.gz #解压

rm -rf setuptools-1.4.2.tar.gz #删除安装包

cd setuptools-1.4.2 #进入文件夹

python2.7 setup.py build #编译

python2.7 setup.py install #安装

rm -rf setuptools-1.4.2 #删除文件夹
```

# 测试
```
easy_install --help
```