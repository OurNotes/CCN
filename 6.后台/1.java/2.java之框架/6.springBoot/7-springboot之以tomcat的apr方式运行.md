总操作流程：
- 1、[创建tomcat的配置类](springBoot-01)
- 2、[修改properties文件](springBoot-02)
- 3、[测试](springBoot-03)

***
> 注意springboot是2。以上版本

# <a name="springBoot-01" href="#" >创建tomcat的配置类</a>

> TomcatConfig
```java
@Configuration
public class TomcatConfig {

    @Value("${tomcat.apr.protocol}")
    private String protocol;

    @Value("${tomcat.apr.acceptorThreadCount}")
    private String acceptorThreadCount;

    @Value("${tomcat.apr.minSpareThreads}")
    private String minSpareThreads;

    @Value("${tomcat.apr.maxSpareThreads}")
    private String maxSpareThreads;

    @Value("${tomcat.apr.maxThreads}")
    private String maxThreads;

    @Value("${tomcat.apr.maxConnections}")
    private String maxConnections;

    @Value("${tomcat.apr.connectionTimeout}")
    private String connectionTimeout;

    @Value("${tomcat.apr.redirectPort}")
    private String redirectPort;

    @Value("${tomcat.apr.compression}")
    private String compression;

    @Value("${tomcat.apr.address}")
    private String address;

    @Value("${tomcat.apr.maxFileSize}")
    private String maxFileSize;

    @Value("${tomcat.apr.maxRequestSize}")
    private String maxRequestSize;

    @Bean
    public ServletWebServerFactory servletContainer() {
        TomcatServletWebServerFactory tomcat = new TomcatServletWebServerFactory() {
            @Override
            protected void postProcessContext(Context context) {
                SecurityConstraint securityConstraint = new SecurityConstraint();
                securityConstraint.setUserConstraint("CONFIDENTIAL");
                SecurityCollection collection = new SecurityCollection();
                collection.addPattern("/*");
                securityConstraint.addCollection(collection);
                context.addConstraint(securityConstraint);
            }
        };
        tomcat.addAdditionalTomcatConnectors(redirectConnector());
        return tomcat;
    }

    private Connector redirectConnector() {
        Connector connector = new Connector(protocol);
        connector.setAttribute("acceptorThreadCount",acceptorThreadCount);
        connector.setAttribute("minSpareThreads",minSpareThreads);
        connector.setAttribute("maxSpareThreads",maxSpareThreads);
        connector.setAttribute("maxThreads",maxThreads);
        connector.setAttribute("maxConnections",maxConnections);
        connector.setAttribute("connectionTimeout",connectionTimeout);
        connector.setAttribute("redirectPort",redirectPort);
        connector.setAttribute("compression",compression);
        connector.setAttribute("address",address);
        connector.setAttribute("maxFileSize",maxFileSize);
        connector.setAttribute("maxRequestSize",maxRequestSize);
        return connector;
    }
}
```

# <a name="springBoot-02" href="#" >修改properties文件</a>

```c
# tomcat
tomcat.apr.acceptorThreadCount=4
tomcat.apr.minSpareThreads=50
tomcat.apr.maxSpareThreads=50
tomcat.apr.maxThreads=1000
tomcat.apr.maxConnections=10000
tomcat.apr.connectionTimeout=10000
tomcat.apr.protocol=org.apache.coyote.http11.Http11NioProtocol
tomcat.apr.redirectPort=443
tomcat.apr.compression=on
tomcat.apr.maxFileSize=300MB
tomcat.apr.maxRequestSize=500MB
tomcat.apr.address=0.0.0.0
```

# <a name="springBoot-03" href="#" >测试</a>

```
运行测试
```