总操作流程：
- 1、[创建Java项目](redis-01)
- 2、[导入Jedis驱动包](redis-02)
- 3、[写Jedis链接redis代码](redis-03)
- 4、[测试](redis-04)

***

> 注意：本教程使用idea开发工具操作

# <a name="redis-01" href="#" >创建Java项目</a>

>1、创建项目

![](image/3-1.png)

![](image/3-2.png)

![](image/3-3.png)

![](image/3-4.png)

>2、创建包

![](image/3-5.png)

![](image/3-6.png)

>3、创建类

![](image/3-7.png)

![](image/3-8.png)

>4、测试

```java
package com.person.jedis;

/**
 * @ClassName: JedisTest
 * @Description: 测试Java项目是否成功
 * @Author : DK_Li
 * @Date: 2019/01/16
 */
public class JedisTest {
    public static void main(String[] args) {
        System.out.println("1111111111");
    }
}

```

![](image/3-9.png)

# <a name="redis-02" href="#" >导入Jedis驱动包</a>

[![](https://img.shields.io/badge/Jedis-2.9.0-green.svg "Jedis 2.9.0")](https://pan.baidu.com/s/1qfDtD5M3Zinuq5RHP2clAw)

![](image/3-10.png)

# <a name="redis-03" href="#" >写Jedis链接redis代码</a>

```java
package com.person.jedis;

import redis.clients.jedis.Jedis;

/**
 * @ClassName: JedisTest
 * @Description: 连接到 redis 服务
 * @Author : DK_Li
 * @Date: 2019/01/16
 */
public class JedisTest {
    public static void main(String[] args) {
        //连接本地的 Redis 服务
        Jedis jedis = new Jedis("localhost");
        System.out.println("连接成功");
        //查看服务是否运行
        System.out.println("服务正在运行: "+jedis.ping());
    }
}

```


