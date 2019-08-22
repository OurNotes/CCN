总操作流程：
- 1、下载安装
- 2、测试

***

# 下载安装

>1、配置好编译环境
```
apt-get install aptitude
aptitude install nvidia-kernel-dkms
apt-get install mesa-utils apt-file
apt-get install -y linux-headers-$(uname -r)
apt-get install nvidia-kernel-dkms
apt-get dist-upgrade
sed 's/quiet/quiet nouveau.modeset=0/g' -i /etc/default/grub
update-grub
reboot
```

# 测试

- 要在本机上运行，在远程软件上运行不会显示的

```
glxinfo | grep direct
```
- 成功标志
```
direct rendering: Yes
```