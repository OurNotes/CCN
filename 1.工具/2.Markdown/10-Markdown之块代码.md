# 本页目录
- 1、[普通块代码](#Markdown-01)
- 2、[css专用块代码](#Markdown-02)
- 3、[less专用块代码](#Markdown-03)
- 4、[shell专用块代码](#Markdown-04)
- 5、[js专用块代码](#Markdown-05)
- 6、[diff专用块代码（对比）](#Markdown-06)
- 7、[json专用块代码](#Markdown-07)
- 8、[xml专用块代码](#Markdown-08)
- 9、[html专用块代码](#Markdown-09)
- 10、[java专用块代码](#Markdown-10)
- 11、[vue专用块代码](#Markdown-11)
- 12、[sql专用块代码](#Markdown-12)
- 13、[properties专用块代码](#Markdown-13)

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

# <a name="Markdown-08" href="#" >xml专用块代码</a>

- 效果展现：

```xml
<!DOCTYPE web-app PUBLIC
 "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
 "http://java.sun.com/dtd/web-app_2_3.dtd" >
<web-app>
  <display-name>Archetype Created Web Application</display-name>
    
    <!-- 配置Struts2框架的核心调度器 -->
    <filter>
        <filter-name>struts2</filter-name>
        <filter-class>org.apache.struts2.dispatcher.filter.StrutsPrepareAndExecuteFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>struts2</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
    
    <!-- 默认主界面 -->
    <welcome-file-list>
        <welcome-file>index.jsp</welcome-file>
    </welcome-file-list>
</web-app>
```

- 语法：

![](image/10-8.png)

# <a name="Markdown-09" href="#" >html专用块代码</a>

- 效果展现：

```html
<%@ page contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<body>
    <h2>第一页</h2>
    <form action="toShow">
         <input type="submit" value="提交">
    </form>
</body>
</html>
```

- 语法：

![](image/10-9.png)

# <a name="Markdown-10" href="#" >java专用块代码</a>

- 效果展现：

```java
package com.person.controller;

import com.opensymphony.xwork2.ActionSupport;

public class UserController extends ActionSupport{
    private static final long serialVersionUID = 1L; 
    public String showUser() {
        System.out.println("111111111");
        return SUCCESS;  
    }
}
```

- 语法：

![](image/10-10.png)

# <a name="Markdown-11" href="#" >vue专用块代码</a>

- 效果展现：

```vue
<template>
  <div>content page</div>
</template>
```

- 语法：

![](image/10-11.png)

# <a name="Markdown-12" href="#" >sql专用块代码</a>

- 效果展现：

```sql
CREATE DATABASE /*!32312 IF NOT EXISTS*/`ssm` /*!40100 DEFAULT CHARACTER SET latin1 */;

USE `ssm`;

DROP TABLE IF EXISTS `test`;

CREATE TABLE `test` (
  `testID` varchar(11) NOT NULL,
  `testName` varchar(20) NOT NULL,
  `testSex` varchar(20) NOT NULL,
  `testAge` varchar(11) NOT NULL,
  PRIMARY KEY (`testID`)
) ENGINE=InnoDB DEFAULT CHARSET=latin1;

insert  into `test`(`testID`,`testName`,`testSex`,`testAge`) values ('1','1','1','1');
insert  into `test`(`testID`,`testName`,`testSex`,`testAge`) values ('2','2','2','2');
insert  into `test`(`testID`,`testName`,`testSex`,`testAge`) values ('3','3','3','3');
insert  into `test`(`testID`,`testName`,`testSex`,`testAge`) values ('4','4','4','4');
```

- 语法：

![](image/10-12.png)

# <a name="Markdown-13" href="#" >properties专用块代码</a>

- 效果展现：

```properties
#配置根Logger 后面是若干个Appender
log4j.rootLogger=DEBUG,A1,R
#log4j.rootLogger=INFO,A1,R

# ConsoleAppender 输出
log4j.appender.A1=org.apache.log4j.ConsoleAppender
log4j.appender.A1.layout=org.apache.log4j.PatternLayout
log4j.appender.A1.layout.ConversionPattern=%-d{yyyy-MM-dd HH:mm:ss,SSS} [%c]-[%p] %m%n

# File 输出 一天一个文件,输出路径可以定制,一般在根路径下
log4j.appender.R=org.apache.log4j.DailyRollingFileAppender
log4j.appender.R.File=log.txt
log4j.appender.R.MaxFileSize=500KB
log4j.appender.R.MaxBackupIndex=10
log4j.appender.R.layout=org.apache.log4j.PatternLayout
log4j.appender.R.layout.ConversionPattern=%d{yyyy-MM-dd HH:mm:ss,SSS} [%t] [%c] [%p] - %m%n
```

- 语法：

![](image/10-13.png)