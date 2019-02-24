总操作流程：
- 1、下载安装
- 2、配置
- 3、测试

***

# 下载安装

```
apt-get install xrdp

apt-get install vnc4server
```

# 配置

```
nano /etc/xrdp/xrdp.ini
```

>将原来max_bpp=32改成max_bpp=16

```
service xrdp restart
service xrdp-sesman restart
vncserver #设置密码
```





# 测试