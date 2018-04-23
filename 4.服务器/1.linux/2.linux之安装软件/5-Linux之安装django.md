操作总流程：
- 1、下载安装
- 2、创建软连接
- 3、检查

----------
# 下载安装
```
wget https://www.djangoproject.com/m/releases/1.9/Django-1.9.tar.gz #下载

tar -xvzf Django-1.9.tar.gz #解压

cd Django-1.9 #进入文件夹

python2.7 setup.py build #编译

python2.7 setup.py install #安装
```

# 创建软连接
```
ln -s /usr/local/python2.7/bin/django-admin.py /usr/bin
```


# 检查
```
python -c "import django; print(django.get_version())"
```