# 本页目录
- 1、[普通块代码](#Markdown-01)
- 2、[css专用块代码](#Markdown-02)
- 3、[less专用块代码](#Markdown-03)
- 4、[shell专用块代码](#Markdown-04)
- 5、[js专用块代码](#Markdown-05)
- 6、[diff专用块代码（对比）](#Markdown-06)
- 7、[json专用块代码](#Markdown-07)

***

# <a name="Markdown-01" href="#" >普通块代码</a>
- 效果展现：
```
q
e
```

- 语法：

![](image/10-1.png)

# <a name="Markdown-02" href="#" >css专用块代码</a>

- 效果展现：
```css
.php-icon:before{
    font-family: MFizz;
    content: "\f147";
}
```

- 语法：

![](image/10-2.png)

# <a name="Markdown-03" href="#" >less专用块代码</a>

- 效果展现：

```less
.directory > .header > .icon{
    &[data-path$=".atom/packages"]:before{
        font-family: "Octicons Regular";
        content: "\f0c4";
    }
}
```

- 语法：

![](image/10-3.png)

# <a name="Markdown-04" href="#" >shell专用块代码</a>

- 效果展现：

```shell
rm -rf ~/.atom/.apm
apm install --production file-icons
```

- 语法：

![](image/10-4.png)

# <a name="Markdown-05" href="#" >js专用块代码</a>

- 效果展现：

```js
atom.config.set("file-icons.revealTreeView", false);
```

- 语法：

![](image/10-5.png)

# <a name="Markdown-06" href="#" >diff专用块代码（对比）</a>

- 效果展现：

```diff
-@import "packages/file-icons/styles/icons";
-@import "packages/file-icons/styles/items";
-@{pane-tab-selector},
.icon-file-directory {
    &[data-name=".git"]:before {
-       .git-icon;
+       font-family: Devicons;
+       content: "\E602";
    }
}
```

- 语法：

![](image/10-6.png)

# <a name="Markdown-07" href="#" >json专用块代码</a>

- 效果展现：

```json
"consumedServices": {
    "file-icons.element-icons": {
        "versions": {
            "1.0.0": "consumeElementIcons"
        }
    }
}
```

- 语法：

![](image/10-7.png)