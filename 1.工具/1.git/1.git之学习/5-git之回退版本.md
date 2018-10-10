本页目录：
- 1、[显示从最近到最远的提交日志](#git-01)
- 2、[回退到上一个版本](#git-02)
- 3、[指定回退某个版本](#git-03)
- 4、[查看每一次命令](#git-04)

----------
# <a name="git-01" href="#" >显示从最近到最远的提交日志</a>
- 语法：

```shell
git log 选择
```

选择：

--pretty=oneline ：如果嫌输出信息太多，看得眼花缭乱的，可以试试加上

# <a name="git-02" href="#" >回退到上一个版本</a>
- 语法：

```shell
git reset --hard HEAD^
```
# <a name="git-03" href="#" >指定回到某个版本</a>
- 语法：

```shell
git reset --hard (commit id)
```

commit id:

![](image/5-1.png)

# <a name="git-04" href="#" >查看每一次命令</a>
- 语法：

```shell
git reflog
```

- 效果展现：

![](image/5-2.png)
