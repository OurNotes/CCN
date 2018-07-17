[![](https://img.shields.io/badge/参考文献-通过注解配置授权-yellow.svg "参考文献 通过注解配置授权")](https://www.imooc.com/video/16959/0)


总操作流程：
- 1、pom.xml引用包；
- 2、修改文件；
- 3、测试；

***

使用这个[![](https://img.shields.io/badge/源码-shiro--mysql-blue.svg "源码 shiro-mysql")](https://github.com/lidekai/shiro-mysql.git)在其基础上修改

# pom.xml引用包
添加
```
<aspectjweaver.version>1.9.0</aspectjweaver.version>

    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-aop</artifactId>
      <version>${spring.version}</version>
    </dependency>

        <dependency>
          <groupId>org.aspectj</groupId>
          <artifactId>aspectjweaver</artifactId>
          <version>${aspectjweaver.version}</version>
        </dependency>



```
# 修改文件

在UserController添加文件
```
   @RequiresRoles("admin")
    @RequestMapping(value = "/testRole",method = RequestMethod.GET)
    @ResponseBody
    public String testRole(){
        return "testRole success";
    }
```
# 测试

![](image/9-1.gif)