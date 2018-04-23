操作总流程：
- 1、下载安装
- 2、做软连接
- 3、更新

----------


# 下载安装
```
wget https://pypi.python.org/packages/source/p/pip/pip-1.3.1.tar.gz --no-check-certificate #下载

tar -xzvf pip-1.3.1.tar.gz #解压

cd pip-1.3.1 #进入文件夹

python setup.py build #编译

python setup.py install #安装
```

# 做软链接
```
ln -s /usr/local/python2.7/bin/pip /usr/bin/
```

# 更新
```
 pip install --upgrade pip
```