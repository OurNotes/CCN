总操作流程：
- 1、[修改下载源链接](#kail-linux-01)
- 2、[更新升级](#kail-linux-02)

***

# <a name="kail-linux-01" href="#" >修改下载源链接</a>

```
vim /etc/apt/sources.list

```

```shell
deb http://http.kali.org/kali kali-rolling main non-free contrib
```

# <a name="kail-linux-02" href="#" >更新升级</a>

```
apt-get update

apt-get upgrade
```