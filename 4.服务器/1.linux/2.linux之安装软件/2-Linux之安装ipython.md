操作总流程：
- 1、[下载安装](#Linux-01)
- 2、[做软链接](#Linux-02)
- 3、[测试](#Linux-03)

----------


# <a name="Linux-01" href="#" >下载安装</a>
```shell
wget -c http://www.dwhd.org/script/tar_gz_bz2/ipython-3.0.0.tar.gz #下载

tar xf ipython-3.0.0.tar.gz #解压

rm -rf ipython-3.0.0.tar.gz #删除安装包

cd ipython-3.0.0 #进入文件夹里

/usr/local/python2.7/bin/python2.7 setup.py build #编译(路径是python的安装路径）

/usr/local/python2.7/bin/python2.7 setup.py install #安装(路径是python的安装路径）

cd .. #返回上一级

rm -rf ipython-3.0.0 #删除文件夹
```
# <a name="Linux-02" href="#" >做软链接</a>
```shell
ln -sv /usr/local/python2.7/bin/ipython /usr/bin/
```
# <a name="Linux-03" href="#" >测试</a>
```shell
ipython -c "print 'hello'"
```