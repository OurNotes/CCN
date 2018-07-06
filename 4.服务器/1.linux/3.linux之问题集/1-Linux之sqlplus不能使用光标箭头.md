总操作流程：
- 1、下载安装；
- 2、修改配置文件；

***

# 下载安装
### 1、下载
[下载](https://pan.baidu.com/s/1XEg3UF5Eh124khS06pYbhg)
```
cd /usr/local/src
chmod  0777 /usr/local/src #给目录写权限
```
- 上传
![](image/1-1.png)
### 2、安装
```
# 安装readline
yum install readline*

tar -xzvf rlwrap-0.42.tar.gz  #解压

rm -rf rlwrap-0.42.tar.gz #删除包

cd rlwrap-0.42

./configure --prefix=/usr/local/rlwrap # 配置

make  #编译

make install  #安装

```
# 修改配置文件
### 1、切换到oracle用户，编辑bash_profile文件
```
su dk

cd ~

vi .bash_profile
```
- 添加内容:
```
# rlwrap的环境变量
export PATH=$PATH:/usr/local/rlwrap/bin
alias sqlplus='rlwrap sqlplus'
alias rman='rlwrap rman'
```
### 2、 是修改生效
```
source .bash_profile
```
### 3、查看是否安装成功
```
rlwrap -v
```