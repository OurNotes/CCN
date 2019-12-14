总操作流程：
- 1、[下载安装](#kail-linux-01)
- 2、[测试](#kail-linux-02)

***

#  <a name="kail-linux-01" href="#" >下载安装</a>

>1、安装nvidia驱动
```
apt-get install -y linux-headers-$(uname -r)

apt-get install aptitude
aptitude install nvidia-kernel-dkms

apt-get install mesa-utils  apt-file nvidia-kernel-dkms nvidia-driver nvidia-xconfig mesa-utils

sed 's/quiet/quiet nouveau.modeset=0/g' -i /etc/default/grub
update-grub
reboot
```

- 成功标准

```
glxinfo | grep -i "direct rendering" 

direct rendering: Yes  # 成功
```

> 2、屏蔽nouveau

```
vim /etc/modprobe.d/nvidia-blacklists-nouveau.conf
```

```
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off
```

- 使用命令lsmod | grep -i nouveau 没有东西代表屏蔽成功了

> 3、修改BusID

```
lspci |grep NVIDIA
```

- 出现

```
01:00.0 VGA compatible controller: NVIDIA Corporation GP107 [GeForce GTX 1050 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)
```

- 下载文件
```
wget https://gist.githubusercontent.com/jamesmacwhite/90d3fb1e0f3c0e238a5a08984718fd13/raw/9bf0d205f2adac8d4f25f824f2bc3c42caaaec09/nvidia-x11-xorg.conf -O /etc/X11/xorg.conf

wget https://gist.githubusercontent.com/jamesmacwhite/580c798531ff12289c8635d70a78df62/raw/3439083dd04e53484af12f55f6b185e80ef44a57/optimus.desktop -O /usr/share/gdm/greeter/autostart/optimus.desktop

cp /usr/share/gdm/greeter/autostart/optimus.desktop /etc/xdg/autostart/optimus.desktop

vim /etc/X11/xorg.conf
```

- 将查询到的01:00.0改成01:00:0到BusID值上

> 4、安装cuda

```
apt-get install ocl-icd-libopencl1 nvidia-cuda-toolkit
```

#  <a name="kail-linux-02" href="#" >测试</a>

-要在本机上运行，在远程软件上运行不会显示的

> 1、测试一
```
glxinfo | grep -i "direct rendering"
```
- 成功标志
```
direct rendering: Yes
```

> 2、测试二
```
glxinfo | grep NVIDIA
```

> 3、测试三

```
nvidia-smi
```
