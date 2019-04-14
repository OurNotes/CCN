总操作流程：
- 1、修改配置文件
- 2、写代码
- 3、测试

***

> 在springBoot之集成ssm的源码基础上修改

# 修改配置文件

> 1、修改pom.xml
```xml
		<dependency>
			<groupId>com.googlecode.xmemcached</groupId>
			<artifactId>xmemcached</artifactId>
			<version>2.4.6</version>
		</dependency>
```

> 2、修改application.properties
```c
#memcached
memcached.servers=127.0.0.1:8888
memcached.poolSize=10
memcached.sanitizeKeys=false
memcached.openCache=true
```

# 写代码

> 1、添加XMemcachedConfig的java文件

- XMemcachedConfig
```Java
@Configuration
public class XMemcachedConfig {


    private XMemcachedProperties xMemcachedProperties;

    @Autowired
    public void setxMemcachedProperties(XMemcachedProperties xMemcachedProperties) {
        this.xMemcachedProperties = xMemcachedProperties;
    }

    @Bean
    public MemcachedClientBuilder getXMBuilder(){
        MemcachedClientBuilder memcachedClientBuilder = null;
        try{
            String servers = xMemcachedProperties.getServers();
            System.out.println("servers="+servers);
            memcachedClientBuilder = new XMemcachedClientBuilder(servers);
            // 开启/关闭failure模式
            memcachedClientBuilder.setFailureMode(false);
            memcachedClientBuilder.setSanitizeKeys(xMemcachedProperties.isSanitizeKeys());
            memcachedClientBuilder.setConnectionPoolSize(xMemcachedProperties.getPoolSize());
            memcachedClientBuilder.setCommandFactory(new BinaryCommandFactory());
            memcachedClientBuilder.setOpTimeout(3000);
            memcachedClientBuilder.setSessionLocator(new KetamaMemcachedSessionLocator());

            // 诸多XMemcached配置
            return memcachedClientBuilder;
        }catch(Exception e){
            e.printStackTrace();
        }
        return null;
    }

    @Bean
    public MemcachedClient getXMClient(MemcachedClientBuilder memcachedClientBuilder){
        MemcachedClient memcachedClient = null;
        try{
            memcachedClient = memcachedClientBuilder.build();
            return memcachedClient;
        }catch(Exception e){
            e.printStackTrace();
        }
        return null;

    }
}

```

- XMemcachedProperties

```java
@Component
@ConfigurationProperties(prefix = "memcached")
public class XMemcachedProperties {
    private String servers;
    private int poolSize;
    private boolean sanitizeKeys;
    private boolean openCache;

    public boolean isOpenCache() {
        return openCache;
    }

    public void setOpenCache(boolean openCache) {
        this.openCache = openCache;
    }

    public String getServers() {
        return servers;
    }

    public void setServers(String servers) {
        this.servers = servers;
    }

    public int getPoolSize() {
        return poolSize;
    }

    public void setPoolSize(int poolSize) {
        this.poolSize = poolSize;
    }

    public boolean isSanitizeKeys() {
        return sanitizeKeys;
    }

    public void setSanitizeKeys(boolean sanitizeKeys) {
        this.sanitizeKeys = sanitizeKeys;
    }
}
```

- 2、添加XMemcached接口 


# 测试

 
