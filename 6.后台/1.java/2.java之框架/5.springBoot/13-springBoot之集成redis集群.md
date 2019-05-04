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

>RedisChannelManager

```java
@Component
public class RedisChannelManager {
    private Logger log = LoggerFactory.getLogger(RedisChannelManager.class);

    @Autowired
    private SyniRedisTemplate redisTemplate;

    /**
     * key：userId
     * value：channel
     */
    private Map<String, String> channelMap = null;

    public RedisChannelManager() {
        channelMap = new ConcurrentHashMap<String, String>();
    }

    public synchronized void putChannel(String userId, String channel) {
        if(channelMap != null) {
            channelMap.put(userId, channel);
        }
    }

    public synchronized void removeChannel(String userId) {
        if(channelMap != null) {
            channelMap.remove(userId);
        }
    }

    public synchronized void destroy() {
        log.info("RedisChannelManager destroy.");
        if(channelMap != null) {
            List<String> channels = new ArrayList<String>(channelMap.values());
            //取消所有订阅的消息通道
            if(channels != null && channels.size() > 0) {
                for (String channel : channels) {
                    log.info("RedisChannelManager: close channel={}", channel);
                    redisTemplate.publish(channel, "syni_cmd_close");
                }
                channels.clear();
                channels = null;
            }
            channelMap.clear();
            channelMap = null;
        }
    }
}

```

>RedisMQTask

```java
public class RedisMQTask implements Runnable {

    private static final Logger log = LoggerFactory.getLogger(RedisMQTask.class);

    private JedisCluster jedisCluster;
    private JedisPubSub jedisPubSub;
    private String channels;

    public RedisMQTask(JedisCluster jedisCluster, JedisPubSub jedisPubSub, String channels) {
        this.jedisCluster = jedisCluster;
        this.jedisPubSub = jedisPubSub;
        this.channels = channels;
    }

    @Override
    public void run() {
        // 监听channel通道的消息
        if(jedisCluster != null) {
            jedisCluster.subscribe(jedisPubSub, channels);
        }
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

>SyniRedisTemplate

```java
@Component
public class SyniRedisTemplate {

    public static final String CHANNEL_FORWARD_PREFIX = "syni:channel";
    public static final String USER_FORWARD_CACHE_PREFIX = "syni:user";//缓存前缀
    public static final String MESSAGE_QUEUE_KEY = "syni:message:queue";

    private static final Logger log = LoggerFactory.getLogger(SyniRedisTemplate.class);

    @Autowired
    private JedisCluster jedisCluster;

    @Autowired
    private RedisProperties redisProperties;

    public static final String KEY_SPLIT = ":"; //用于隔开缓存前缀与缓存键值

    /**
     * 设置缓存
     *
     * @param prefix 缓存前缀（用于区分缓存，防止缓存键值重复）
     * @param key    缓存key
     * @param value  缓存value
     */
    public void set(String prefix, String key, String value) {
        jedisCluster.set(prefix + KEY_SPLIT + key, value);
        log.debug("RedisUtil:set cache key={},value={}", prefix + KEY_SPLIT + key, value);
    }

    /**
     * 设置缓存，并且自己指定过期时间
     *
     * @param prefix
     * @param key
     * @param value
     * @param expireTime 过期时间
     */
    public void setWithExpireTime(String prefix, String key, String value, int expireTime) {
        jedisCluster.setex(prefix + KEY_SPLIT + key, expireTime, value);
        log.debug("RedisUtil:setWithExpireTime cache key={},value={},expireTime={}", prefix + KEY_SPLIT + key, value,
                expireTime);
    }

    /**
     * 设置缓存，并且由配置文件指定过期时间
     *
     * @param prefix
     * @param key
     * @param value
     */
    public void setWithExpireTime(String prefix, String key, String value) {
        int EXPIRE_SECONDS = redisProperties.getExpireSeconds();
        jedisCluster.setex(prefix + KEY_SPLIT + key, EXPIRE_SECONDS, value);
        log.debug("RedisUtil:setWithExpireTime cache key={},value={},expireTime={}", prefix + KEY_SPLIT + key, value,
                EXPIRE_SECONDS);
    }

    /**
     * 获取指定key的缓存
     *
     * @param prefix
     * @param key
     */
    public String get(String prefix, String key) {
        String value = jedisCluster.get(prefix + KEY_SPLIT + key);
        log.debug("RedisUtil:get cache key={},value={}", prefix + KEY_SPLIT + key, value);
        return value;
    }

    /**
     * 删除指定key的缓存
     *
     * @param prefix
     * @param key
     */
    public void deleteWithPrefix(String prefix, String key) {
        jedisCluster.del(prefix + KEY_SPLIT + key);
        log.debug("RedisUtil:delete cache key={}", prefix + KEY_SPLIT + key);
    }

    public void delete(String key) {
        jedisCluster.del(key);
        log.debug("RedisUtil:delete cache key={}", key);
    }

    /**
     * 发布消息到redis通道
     *
     * @param channel
     * @param message
     */
    public boolean publish(String channel, String message) {
        boolean flag = false;
        try {
            jedisCluster.publish(channel, message);
            flag = true;
        } catch (Exception e) {
            log.error("RedisUtil:publish message error={}", e.getMessage());
        } finally {

        }
        return flag;
    }

    /**
     * 订阅redis通道消息
     *
     * @param jedisPubSub 监听处理类
     * @param channels    监听的消息通道
     */
    public boolean subscribe(JedisPubSub jedisPubSub, String channels) {
        boolean flag = false;
        try {
            new Thread(new RedisMQTask(jedisCluster, jedisPubSub, channels)).start();
//            jedisCluster.subscribe(jedisPubSub, channels);
            flag = true;
        } catch (Exception e) {
            log.error("RedisUtil:subscribe message error={}", e.getMessage());
        } finally {

        }
        return flag;
    }

    public long putMessage(String message) {
        return jedisCluster.lpush(MESSAGE_QUEUE_KEY, message);
    }

    public List<String> brpopMessage() {
        /**
         * brpop支持多个列表(队列)
         * brpop指令是支持队列优先级的，比如这个例子中MESSAGE_QUEUE_KEY的优先级大于testKey（顺序决定）。
         * 如果两个列表中都有元素，会优先返回优先级高的列表中的元素，所以这儿优先返回MESSAGE_QUEUE_KEY
         * 0表示不限制等待，会一直阻塞在这儿
         */
//        return jedisCluster.brpop(0, MESSAGE_QUEUE_KEY, "syni:message:tqueue");
        return jedisCluster.brpop(0, MESSAGE_QUEUE_KEY);

    }

    public String popMessage() {
        return jedisCluster.rpop(MESSAGE_QUEUE_KEY);
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