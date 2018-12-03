# 本页目录
- 1、[普通代码块](#Markdown-01)
- 2、[语法高亮代码块](#Markdown-02)
- 3、添加id或者class代码块

***

# <a name="Markdown-01" href="#" >普通代码块</a>
- 效果展现：
```
q
e
```

- 语法：

![](image/10-1.png)

# <a name="Markdown-02" href="#" >语法高亮代码块</a>

- 效果展现：
```css
.php-icon:before{
    font-family: MFizz;
    content: "\f147";
}
```

- 语法：

![](image/10-2.png)

# 添加id或者class代码块
<style type="text/css">
    #myid1{color:blue}
</style>

```js {#myid1}
function add(x, y) {
  return x + y
}
```