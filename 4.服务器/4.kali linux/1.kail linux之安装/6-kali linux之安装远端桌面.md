总操作流程：
- 1、[下载安装](#kail-linux-01)
- 2、[配置](#kail-linux-02)
- 3、[测试](#kail-linux-03)

***

# <a name="kail-linux-01" href="#" >下载安装</a>

```
apt-get install xrdp

apt-get install vnc4server
```

# <a name="kail-linux-02" href="#" >配置</a>

```
nano /etc/xrdp/xrdp.ini
```

>将原来max_bpp=32改成max_bpp=16

```
service xrdp restart
service xrdp-sesman restart
vncserver #设置密码
```

# <a name="kail-linux-01" href="#" >测试</a>