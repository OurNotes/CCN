总操作流程：
- 1、下载安装
- 2、测试

***

# 下载安装
```
apt-get install mesa-utils apt-file
apt-get dist-upgrade
apt-get install -y linux-headers-$(uname -r)
apt-get install nvidia-kernel-dkms
sed 's/quiet/quiet nouveau.modeset=0/g' -i /etc/default/grub
update-grub
reboot
```

# 测试

```
glxinfo | grep direct
```
- 成功标志
```
direct rendering: Yes
```