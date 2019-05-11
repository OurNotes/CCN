总操作流程：
- 1、创建文件
- 2、调用
- 3、测试

[![](https://img.shields.io/badge/源码-springboot--redis-blue.svg "源码 springboot-redis")](https://github.com/lidekai/springboot-redis.git)

>注意：要用tomcat运行

>还有配合redis的集群配置使用[![](https://img.shields.io/badge/参考文献-redis之集群配置-yellow.svg "参考文献 redis之集群配置")](https://github.com/OurNotes/CCN/blob/master/6.%E5%90%8E%E5%8F%B0/1.java/1.java%E4%B9%8B%E5%BC%80%E5%8F%91%E5%B7%A5%E5%85%B7/8.redis/2-redis%E4%B9%8B%E9%9B%86%E7%BE%A4%E9%85%8D%E7%BD%AE.md)

***

# 创建文件

>总的pom.xml

```xml
<!-- redis的驱动包 -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-redis</artifactId>
            <version>1.4.6.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>redis.clients</groupId>
            <artifactId>jedis</artifactId>
            <version>2.9.0</version>
        </dependency>
        <dependency>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-redis</artifactId>
            <version>2.1.5.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-pool2</artifactId>
            <version>2.5.0</version>
        </dependency>
```

>JedisClusterConfig

```java
@Configuration
@ConditionalOnClass({JedisCluster.class})
@EnableConfigurationProperties(RedisProperties.class)
public class JedisClusterConfig {
    @Autowired
    private RedisProperties redisProperties;

    @Bean
    public JedisCluster getJedisCluster() {
        String[] serverArray = redisProperties.getClusterNodes().split(",");
        Set<HostAndPort> nodes = new HashSet<HostAndPort>();
        for (String ipPort: serverArray) {
            String[] ipPortPair = ipPort.split(":");
            nodes.add(new HostAndPort(ipPortPair[0].trim(),Integer.valueOf(ipPortPair[1].trim())));
        }
        return new JedisCluster(nodes, redisProperties.getCommandTimeout());
    }
}

```

>RedisProperties

```java
@Component
@ConfigurationProperties(prefix = "spring.redis.cache")
public class RedisProperties {

    private int expireSeconds;
    private String clusterNodes;
    private Integer commandTimeout;

    public RedisProperties() {

    }

    public int getExpireSeconds() {
        return expireSeconds;
    }

    public void setExpireSeconds(int expireSeconds) {
        this.expireSeconds = expireSeconds;
    }

    public String getClusterNodes() {
        return clusterNodes;
    }

    public void setClusterNodes(String clusterNodes) {
        this.clusterNodes = clusterNodes;
    }

    public Integer getCommandTimeout() {
        return commandTimeout;
    }

    public void setCommandTimeout(Integer commandTimeout) {
        this.commandTimeout = commandTimeout;
    }
}
```

>RedisUtil

```java
@Configuration
@ConditionalOnClass({JedisCluster.class})
@EnableConfigurationProperties(RedisProperties.class)
public class JedisClusterConfig {
    @Autowired
    private RedisProperties redisProperties;

    @Bean
    public JedisCluster getJedisCluster() {
        String[] serverArray = redisProperties.getClusterNodes().split(",");
        Set<HostAndPort> nodes = new HashSet<HostAndPort>();
        for (String ipPort: serverArray) {
            String[] ipPortPair = ipPort.split(":");
            nodes.add(new HostAndPort(ipPortPair[0].trim(),Integer.valueOf(ipPortPair[1].trim())));
        }
        return new JedisCluster(nodes, redisProperties.getCommandTimeout());
    }
}

```

>application-redis.properties
```c
# redis
spring.redis.cache.clusterNodes=127.0.0.1:6666,127.0.0.1:6667,127.0.0.1:6668,127.0.0.1:6669,127.0.0.1:6670,127.0.0.1:6671
spring.redis.cache.commandTimeout=5000
```
# 调用

```java
@Autowired
private SyniRedisTemplate syniRedisTemplate;
```

```java
System.out.println(syniRedisTemplate.get("key","2"));
```
# 测试

运行测试