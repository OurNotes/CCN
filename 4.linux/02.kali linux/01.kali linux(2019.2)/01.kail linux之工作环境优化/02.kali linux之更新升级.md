总操作流程：
- 1、[修改下载源链接](#kail-linux-01)
- 2、[更新升级](#kail-linux-02)

***

# <a name="kail-linux-01" href="#" >修改下载源链接</a>

```
vim /etc/apt/sources.list

```

```shell
#官方源
deb http://http.kali.org/kali kali-rolling main non-free contrib
deb-src http://http.kali.org/kali kali-rolling main non-free contrib

#中科大
deb http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
deb-src http://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
 
#浙大
deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free
 
#东软大学
deb http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
deb-src http://mirrors.neusoft.edu.cn/kali kali-rolling/main non-free contrib
 
#重庆大学
deb http://http.kali.org/kali kali-rolling main non-free contrib
deb-src http://http.kali.org/kali kali-rolling main non-free contrib

# 163源
deb http://mirrors.163.com/debian/ squeeze main non-free contrib
deb http://mirrors.163.com/debian/ squeeze-updates main non-free contrib
deb http://mirrors.163.com/debian/ squeeze-lts main non-free contrib
deb-src http://mirrors.163.com/debian/ squeeze main non-free contrib
deb-src http://mirrors.163.com/debian/ squeeze-updates main non-free contrib
deb-src http://mirrors.163.com/debian/ squeeze-lts main non-free contrib
deb http://mirrors.163.com/debian-security/ squeeze/updates main non-free contrib
deb-src http://mirrors.163.com/debian-security/ squeeze/updates main non-free contrib
deb http://mirrors.163.com/debian-backports/ squeeze-backports main contrib non-free
deb-src http://mirrors.163.com/debian-backports/ squeeze-backports main contrib non-free

#阿里云kali源
deb http://mirrors.aliyun.com/kali sana main non-free contrib
deb-src http://mirrors.aliyun.com/kali sana main non-free contrib
deb http://mirrors.aliyun.com/kali-security sana/updates main contrib non-free
deb-src http://mirrors.aliyun.com/kali-security sana/updates main contrib non-free


#中科大kali源
deb http://mirrors.ustc.edu.cn/kali kali-rolling sana main non-free contrib
deb-src http://mirrors.ustc.edu.cn/kali kali-rolling sana main non-free contrib
deb http://mirrors.ustc.edu.cn/kali-security sana/updates main contrib non-free
deb-src http://mirrors.ustc.edu.cn/kali-security sana/updates main contrib non-free

#清华源：
deb http://mirrors.tuna.tsinghua.edu.cn/kali kali-rolling main contrib non-free

#debain源
deb http://mirrors.163.com/debian/ wheezy main contrib
deb http://mirrors.163.com/debian/ wheezy-proposed-updates main contrib
deb-src http://mirrors.163.com/debian/ wheezy main contrib
deb-src http://mirrors.163.com/debian/ wheezy-proposed-updates main contrib

#debian安全更新源
deb http://security.debian.org/ wheezy/updates main contrib
deb-src http://security.debian.org/ squeeze/updates main contrib non-free

#新加坡kali源
deb http://mirror.nus.edu.sg/kali/kali/ kali main non-free contrib
deb-src http://mirror.nus.edu.sg/kali/kali/ kali main non-free contrib
deb http://mirror.nus.edu.sg/kali/kali-security kali/updates main contrib non-free
deb-src http://mirror.nus.edu.sg/kali/kali-security kali/updates main contrib non-free

#Kali-Security
deb http://security.kali.org/ kali/updates main contrib non-free
deb-src http://security.kali.org/ kali/updates main contrib non-free

```

# <a name="kail-linux-02" href="#" >更新升级</a>

```
apt-get update

apt-get upgrade

apt-get dist-upgrade //可以聪明的解决相依性的问题,如果有相依性问题,需要安装/移除新的Package,就会试着去安装/移除它. (所以通常这个会被认为是有点风险的升级，可以不用执行)
```
