# 报错信息
```
MISCONF Redis is configured to save RDB snapshots, but is currently not able to persist
```

# 解决

>通过redis-cli连接到服务器后执行以下命令：

config set stop-writes-on-bgsave-error no