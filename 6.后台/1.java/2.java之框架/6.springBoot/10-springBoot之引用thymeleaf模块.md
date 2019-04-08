总操作流程：
- 1、修改pom.xml
- 2、修改application.properties
- 3、写代码
- 3、测试

***
- 项目目录结构

![](image/10-1.png)

# 修改pom.xml
```xml
	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<thymeleaf.version>3.0.11.RELEASE</thymeleaf.version>
		<thymeleaf-layout-dialect.version>2.0.0</thymeleaf-layout-dialect.version>
	</properties>
```

```xml
		<!-- thymeleaf的驱动包 -->
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-thymeleaf</artifactId>
		</dependency>
```

# 修改application.properties

```js
#thymeleaf
spring.thymeleaf.prefix=classpath:/templates/
spring.thymeleaf.suffix=.html
spring.thymeleaf.mode=HTML5
spring.thymeleaf.encoding=UTF-8
spring.thymeleaf.cache=false
spring.resources.chain.strategy.content.enabled=true
spring.resources.chain.strategy.content.paths=/**
```

# 写代码

> index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

<h2 >拦截测试</h2>
<a href="/user/toAdd">跳转到添加页面</a>
</body>
</html>
```

>add.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>add</h1>
</body>
</html>
```

>UserController

```java
@Controller
@RequestMapping("/user")
public class UserController {

    @RequestMapping("/toIndex")
    public  String toIndex(){
        return "index";
    }

    @RequestMapping("/toAdd")
    public  String toAdd(){
        return "user/add";
    }

}

```
# 测试

运行使用浏览器测试