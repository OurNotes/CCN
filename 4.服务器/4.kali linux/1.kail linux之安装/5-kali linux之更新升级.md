总操作流程：
- 1、修改下载源链接
- 2、更新升级

***

# 修改下载源链接

```
vim /etc/apt/sources.list

```

```shell
deb http://http.kali.org/kali kali-rolling main non-free contrib
```

# 更新升级

```
apt-get update

apt-get upgrade
```