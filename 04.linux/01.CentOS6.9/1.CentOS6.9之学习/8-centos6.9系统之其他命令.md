本页目录
- 1、[切换所在目录](#Linux-01)
- 2、[复制](#Linux-02)
- 3、[剪切或改名](#Linux-03)
- 4、[将原文件生成链接文件](#Linux-04)
- 5、[帮助命令](#Linux-05)
- 6、 [选择帮助](#Linux-06)
- 7、 [详细命令帮助](#Linux-07)
- 8、 [.zip格式压缩](#Linux-08)
- 9、 [.zip格式解压缩](#Linux-09)
- 10、 [gz格式压缩](#Linux-10)
- 11、 [.bz2格式压缩](#Linux-11)
- 12、 [.bz2格式解压缩](#Linux-12)
- 13、 [打包命令tar](#Linux-13)
- 14、 [解打包命令](#Linux-14)
- 15、 [.tar.gz压缩格式](#Linux-15)
- 16、 [.tar.bz2压缩格式](#Linux-16)

# <a name="Linux-01" href="#" >切换所在目录</a>

语法：
```shell
cd  [目录]
```
简化操作：
```
cd ~ 进入当前用户的家目录
cd - 进入上次目录
cd .. 进入上一级目录
cd . 进入当前目录

```

# <a name="Linux-02" href="#" >复制</a>
语法：
```shell
cp  [选项]  [原文件或目录]  [目标目录]
```
选项：
- r 复制目录
- 连带文件属性复制
- d 若源文件是链接文件，则复制链接属性
- a 相当于 -pdr


# <a name="Linux-03" href="#" >剪切或改名</a>
语法：
```shell
mv  [原文件或目录]  [目标目录]
```

# <a name="Linux-04" href="#" >将原文件生成链接文件</a>
```shell
ln -s  [原文件]  [目标文件]
```
-s 创建软链接

# <a name="Linux-05" href="#" >帮助命令</a>
语法：
获取指定命令的帮助
```shell
man 命令  
```
例子：查看ls的帮助命令
```shell
man ls
```
! [](image/8-1.png)

### 1、
```shell
man -f 命令
相当于
whatis 命令
```
### 2、
```shell
man -k 命令
相当于
apropos 命令
```

# <a name="Linux-06" href="#" >选择帮助</a>
语法：
获取命令选择帮助
```shell
命令 --help
```
例子：
```
ls -help
```

# <a name="Linux-07" href="#" >详细命令帮助</a>
语法：
```shell
info 命令
```
-回车：进入子帮助页面（带有*号标记）
-u:进入上层页面
-n:进入下一个帮助小节
-p:进入上一个帮助小节
-q:退出
# <a name="Linux-08" href="#" >.zip格式压缩</a>
语法：
压缩文件
```shell
zip 压缩文件名 源文件
```
压缩目录
```shell
zip -r 压缩文件名 源目录
```
# <a name="Linux-09" href="#" >.zip格式解压缩</a>
语法：
```shell
unzip 压缩文件
```
# <a name="Linux-10" href="#" >gz格式压缩</a>
语法：
```shell
gzip 源文件
gzip -c 源文件 > 压缩文件
gzip -r 目录
```
# <a name="Linux-11" href="#" >.bz2格式压缩</a>
语法：
```shell
bzip2 源文件
bzip2 -k 源文件
```
- .bz2格式解压缩
语法：
```shell
bzip2 -d 压缩文件
bunzip2 压缩文件
```
# 打包命令tar
语法：
```shell
tar -cvf 打包文件名 源文件
```
选项
-c 打包
-v 显示过程
-f 指定打包后的文件

# <a name="Linux-12" href="#" >解打包命令</a>
语法：
```shell
tar -xvf 打包文件名
```
选项
-x 解打包

# <a name="Linux-13" href="#" >.tar.gz压缩格式</a>
### 1、语法：
```shell
tar -zcvf 压缩包名.tar.gz源文件
```
选项
-z 压缩为.tar.gz格式
### 2、语法：
```shell
tar -zxvf 压缩包名.tar.gz
```
选项
-x 解压缩为.tar.gz格式

# <a name="Linux-14" href="#" >.tar.bz2压缩格式</a>
### 1、语法：
```shell
tar -zcvf 压缩包名.tar.bz2源文件
```
选项
-z 压缩为.tar.bz2格式
### 2、语法：
```shell
tar -zxvf 压缩包名.tar.bz2
```
选项
-x 解压缩为.tar.bz2格式