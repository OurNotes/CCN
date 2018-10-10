操作总流程：
- 1、[下载安装](#Linux-01)
- 2、[创建软连接](#Linux-01)
- 3、[检查](#Linux-01)

----------
# <a name="Linux-01" href="#" >下载安装</a>
```shell
wget https://www.djangoproject.com/m/releases/1.9/Django-1.9.tar.gz #下载

tar -xvzf Django-1.9.tar.gz #解压

cd Django-1.9 #进入文件夹

python2.7 setup.py build #编译

python2.7 setup.py install #安装
```

# <a name="Linux-02" href="#" >创建软连接</a>
```shell
ln -s /usr/local/python2.7/bin/django-admin.py /usr/bin
```


# <a name="Linux-03" href="#" >检查</a>
```shell
python -c "import django; print(django.get_version())"
```