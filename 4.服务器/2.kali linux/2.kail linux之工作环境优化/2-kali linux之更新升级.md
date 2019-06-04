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

```

# <a name="kail-linux-02" href="#" >更新升级</a>

```
apt-get update

apt-get upgrade
```
