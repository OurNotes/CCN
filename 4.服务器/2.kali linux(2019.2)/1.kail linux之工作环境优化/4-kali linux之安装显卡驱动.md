总操作流程：
- 1、[下载安装](#kail-linux-01)
- 2、[测试](#kail-linux-02)

***

#  <a name="kail-linux-01" href="#" >下载安装</a>

>1、配置好编译环境
```
apt-get install aptitude
aptitude install nvidia-kernel-dkms
apt-get install mesa-utils  apt-file
apt-get install -y linux-headers-$(uname -r)
apt-get install nvidia-kernel-dkms
apt-get dist-upgrade
sed 's/quiet/quiet nouveau.modeset=0/g' -i /etc/default/grub
update-grub
reboot
```

#  <a name="kail-linux-02" href="#" >测试</a>

- 要在本机上运行，在远程软件上运行不会显示的

```
glxinfo | grep direct
```
- 成功标志
```
direct rendering: Yes
```

- 或者使用：glxinfo | grep NVIDIA
