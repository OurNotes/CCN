本页目录：
- 1、下载子目录（单个）
- 2、下载子目录（多个）

***

# 下载子目录（单个）

- 项目：https://github.com/golang/protobuf
    - 下载的子目录：proto

```
git init
git config core.sparsecheckout true
echo 'proto' >> .git/info/sparse-checkout
git remote add origin https://github.com/golang/protobuf.git
git pull origin master
```

# 下载子目录（多个）
- 项目：https://github.com/golang/protobuf
    - 下载的子目录：ptypes
    - 下载的子目录：jsonpb
```
git init
git config core.sparsecheckout true
echo 'ptypes' >> .git/info/sparse-checkout
echo 'jsonpb' >> .git/info/sparse-checkout
git remote add origin https://github.com/golang/protobuf.git
git pull origin master
```
