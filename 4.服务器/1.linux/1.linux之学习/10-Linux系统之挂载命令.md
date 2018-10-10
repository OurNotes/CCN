- 1、[查询系统中已经挂载的设备](#Linux-01)
- 2、[自动挂载](#Linux-02)
- 3、[挂在命令格式](#Linux-03)
- 4、[建立挂载点](#Linux-04)
- 5、[挂载光盘](#Linux-05)
- 6、[光盘卸载命令](#Linux-06)
- 7、[挂载u盘](#Linux-07)


----------

# <a name="Linux-01" href="#" >查询系统中已经挂载的设备</a>
语法：
```shell
mount
```
# <a name="Linux-02" href="#" >自动挂载</a>
语法：
```shell
mount -a
#根据配置文件/etc/fstab的内容，自动挂载
```
# <a name="Linux-03" href="#" >挂在命令格式</a>
语法：
```shell
mount [-t文件系统] [-o特殊选项] 设备文件名 挂载点
```
选项：
-t 文件系统：加入文件系统类型来指定挂载的类型，可以ext3、ext4、iso9660等文件系统
-o特殊选项：可以指定挂载的额外选项

# <a name="Linux-04" href="#" >建立挂载点</a>
```shell
mkdir/mnt/cdrom/
```

# <a name="Linux-05" href="#" >挂载光盘</a>
```shell
mount -t iso9660/dev/cdrom/mnt/cdrom/
```
# <a name="Linux-06" href="#" >光盘卸载命令</a>
语法：
```shell
umount 设备文件名或者挂载点
```
# <a name="Linux-07" href="#" >挂载u盘</a>
查看u盘设备文件名
```shell
fdisk -l
```
挂载u盘
```shell
mount -t vfat/dev/sdb1 /mnt/usb
```