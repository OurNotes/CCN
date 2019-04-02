总操作流程：
- 1、创建tomcat的配置类
- 2、修改properties文件
- 3、测试

***
> 注意springboot是2。以上版本

# 创建tomcat的配置类

> 1、TomcatProperties

```java
@Configuration
@ConfigurationProperties(prefix="tomcat.apr")
@PropertySource(value="classpath:application.properties")
public class TomcatProperties {
    private String acceptorThreadCount;
    private String minSpareThreads;
    private String maxSpareThreads;
    private String maxThreads;
    private String maxConnections;
    private String connectionTimeout;
    private String protocol;
    private String redirectPort;
    private String compression;
    private String address;
    private String maxFileSize;
    private String maxRequestSize;

    public TomcatProperties() {
    }

    public TomcatProperties(String acceptorThreadCount, String minSpareThreads, String maxSpareThreads, String maxThreads, String maxConnections, String connectionTimeout, String protocol, String redirectPort, String compression, String address, String maxFileSize, String maxRequestSize) {
        this.acceptorThreadCount = acceptorThreadCount;
        this.minSpareThreads = minSpareThreads;
        this.maxSpareThreads = maxSpareThreads;
        this.maxThreads = maxThreads;
        this.maxConnections = maxConnections;
        this.connectionTimeout = connectionTimeout;
        this.protocol = protocol;
        this.redirectPort = redirectPort;
        this.compression = compression;
        this.address = address;
        this.maxFileSize = maxFileSize;
        this.maxRequestSize = maxRequestSize;
    }

    public String getAcceptorThreadCount() {
        return acceptorThreadCount;
    }

    public void setAcceptorThreadCount(String acceptorThreadCount) {
        this.acceptorThreadCount = acceptorThreadCount;
    }

    public String getMinSpareThreads() {
        return minSpareThreads;
    }

    public void setMinSpareThreads(String minSpareThreads) {
        this.minSpareThreads = minSpareThreads;
    }

    public String getMaxSpareThreads() {
        return maxSpareThreads;
    }

    public void setMaxSpareThreads(String maxSpareThreads) {
        this.maxSpareThreads = maxSpareThreads;
    }

    public String getMaxThreads() {
        return maxThreads;
    }

    public void setMaxThreads(String maxThreads) {
        this.maxThreads = maxThreads;
    }

    public String getMaxConnections() {
        return maxConnections;
    }

    public void setMaxConnections(String maxConnections) {
        this.maxConnections = maxConnections;
    }

    public String getConnectionTimeout() {
        return connectionTimeout;
    }

    public void setConnectionTimeout(String connectionTimeout) {
        this.connectionTimeout = connectionTimeout;
    }

    public String getProtocol() {
        return protocol;
    }

    public void setProtocol(String protocol) {
        this.protocol = protocol;
    }

    public String getRedirectPort() {
        return redirectPort;
    }

    public void setRedirectPort(String redirectPort) {
        this.redirectPort = redirectPort;
    }

    public String getCompression() {
        return compression;
    }

    public void setCompression(String compression) {
        this.compression = compression;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    public String getMaxFileSize() {
        return maxFileSize;
    }

    public void setMaxFileSize(String maxFileSize) {
        this.maxFileSize = maxFileSize;
    }

    public String getMaxRequestSize() {
        return maxRequestSize;
    }

    public void setMaxRequestSize(String maxRequestSize) {
        this.maxRequestSize = maxRequestSize;
    }
}

```

> 2、TomcatConfig
```java
@Configuration
public class TomcatConfig {
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
        TomcatProperties tomcat=new TomcatProperties();
        Connector connector = new Connector(tomcat.getProtocol());
        connector.setAttribute("acceptorThreadCount",tomcat.getAcceptorThreadCount());
        connector.setAttribute("minSpareThreads",tomcat.getMinSpareThreads());
        connector.setAttribute("maxSpareThreads",tomcat.getMaxSpareThreads());
        connector.setAttribute("maxThreads",tomcat.getMaxThreads());
        connector.setAttribute("maxConnections",tomcat.getMaxConnections());
        connector.setAttribute("connectionTimeout",tomcat.getConnectionTimeout());
        connector.setAttribute("redirectPort",tomcat.getRedirectPort());
        connector.setAttribute("compression",tomcat.getCompression());
        connector.setAttribute("addresss",tomcat.getAddress());
        connector.setAttribute("maxFileSize",tomcat.getMaxFileSize());
        connector.setAttribute("maxRequestSize",tomcat.getMaxRequestSize());
        return connector;
    }
}
```

# 修改properties文件

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
tomcat.apr.addresss=0.0.0.0
```

# 测试

```
运行测试
```