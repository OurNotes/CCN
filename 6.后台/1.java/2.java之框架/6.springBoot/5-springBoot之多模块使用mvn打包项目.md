总操作流程：
- 1、[打包成jar文件](springBoot-01)
- 2、[打包成war文件](springBoot-02)

***

# <a name="springBoot-01" href="#" >打包成jar文件</a>

- 1、删除的pom.xml的：

```xml
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```

- 2、给web的pom.xml添加：

```xml
    <packaging>jar</packaging>
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <mainClass>net.person.test.TestApplication</mainClass>
                </configuration>
            </plugin>
        </plugins>
    </build>
```

- 3、cmd输入命令

```
cd D:\test

D:

mvn -Dmaven.test.skip -U clean install package 

```

- 4、测试

```
java -jar D:\test\web\target\web-0.0.1-SNAPSHOT.jar
```

使用postman测试接口

# <a name="springBoot-02" href="#" >打包成war文件</a>

- 1、在web模块的src/main下创建文件夹和文件

```
webapp/WEB-INF/web.xml
```

- 2、改web模块的pom.xml
```xml
<packaging>war</packaging>
```

- 3、cmd输入命令

```
cd D:\test

D:

mvn -Dmaven.test.skip -U clean install package
```

- 4、测试

```
java -jar D:\test\web\target\web-0.0.1-SNAPSHOT.war
```

使用postman测试接口