总操作流程：
- 1、[修改pom.xml](springBoot-01)
- 2、[创建Java文件](springBoot-02)
- 3、[测试](springBoot-03)

***

# <a name="springBoot-01" href="#" >修改pom.xml</a>
```xml
		<dependency>
			<groupId>log4j</groupId>
			<artifactId>log4j</artifactId>
			<version>1.2.17</version>
		</dependency>
		<dependency>
			<groupId>com.alibaba</groupId>
			<artifactId>druid</artifactId>
			<version>1.1.15</version>
		</dependency>
		<dependency>
			<groupId>com.alibaba</groupId>
			<artifactId>druid-spring-boot-starter</artifactId>
			<version>1.1.14</version>
		</dependency>
		<dependency>
			<groupId>com.oracle</groupId>
			<artifactId>ojdbc7</artifactId>
			<version>12.1.0.2</version>
		</dependency>
		<dependency>
			<groupId>com.microsoft.sqlserver</groupId>
			<artifactId>sqljdbc4</artifactId>
			<version>4.0</version>
		</dependency>
```
# <a name="springBoot-02" href="#" >创建Java文件</a>

- 一、配置来个数据源

>1、DruidConfig
```java
@Configuration
public class DruidConfig {
    @Bean
    public ServletRegistrationBean statViewServlet(){

        ServletRegistrationBean servletRegistrationBean = new ServletRegistrationBean(new StatViewServlet(),"/druid/*");
        servletRegistrationBean.addInitParameter("allow","127.0.0.1");  //设置ip白名单
        servletRegistrationBean.addInitParameter("deny","192.168.0.19");//设置ip黑名单，优先级高于白名单
        //设置控制台管理用户
        servletRegistrationBean.addInitParameter("loginUsername","root");
        servletRegistrationBean.addInitParameter("loginPassword","root");
        //是否可以重置数据
        servletRegistrationBean.addInitParameter("resetEnable","false");
        return servletRegistrationBean;
    }

    @Bean
    public FilterRegistrationBean statFilter(){
        //创建过滤器
        FilterRegistrationBean filterRegistrationBean = new FilterRegistrationBean(new WebStatFilter());
        //设置过滤器过滤路径
        filterRegistrationBean.addUrlPatterns("/*");
        //忽略过滤的形式
        filterRegistrationBean.addInitParameter("exclusions","*.js,*.gif,*.jpg,*.png,*.css,*.ico,/druid/*");
        return filterRegistrationBean;
    }
}

```

> 2、OracleConfig

```java
@Configuration
@MapperScan(basePackages = "net.person.dao.oracle", sqlSessionTemplateRef  = "masterSqlSessionTemplate")
public class OracleConfig {
    @Bean(name = "masterDataSource")
    //下面这个注解控制哪个实例优先被注入，我们放在第一个数据源上面
    @Primary
    @ConfigurationProperties(prefix = "spring.datasource.oracle")
    public DataSource dataSource() {
        return  new DruidDataSource();
    }

    @Bean(name = "masterSqlSessionFactory")
    @Primary
    public SqlSessionFactory sqlSessionFactory(@Qualifier("masterDataSource") DataSource dataSource) throws Exception {
        SqlSessionFactoryBean bean = new SqlSessionFactoryBean();
        bean.setDataSource(dataSource);
        bean.setMapperLocations(new PathMatchingResourcePatternResolver().getResources("classpath:mybatis/*Mapper.xml"));
        return bean.getObject();
    }

    @Bean(name = "masterSqlSessionTemplate")
    @Primary
    public SqlSessionTemplate sqlSessionTemplate(@Qualifier("masterSqlSessionFactory") SqlSessionFactory sqlSessionFactory)
            throws Exception {
        return new SqlSessionTemplate(sqlSessionFactory);
    }
}

```

> 3、SqlServerConfig

```java
@Configuration
@MapperScan(basePackages = "net.person.dao.sqlserver", sqlSessionTemplateRef  = "slaveSqlSessionTemplate")
public class SqlServerConfig {
    @Bean(name = "slaveDataSource")
    @ConfigurationProperties(prefix = "spring.datasource.sqlserver")
    public DataSource dataSource() {
        return  new DruidDataSource();
    }

    @Bean(name = "slaveSqlSessionFactory")
    @Primary
    public SqlSessionFactory sqlSessionFactory(@Qualifier("slaveDataSource") DataSource dataSource) throws Exception {
        SqlSessionFactoryBean bean = new SqlSessionFactoryBean();
        bean.setDataSource(dataSource);
        bean.setMapperLocations(new PathMatchingResourcePatternResolver().getResources("classpath:mybatis/*Mapper.xml"));
        return bean.getObject();
    }

    @Bean(name = "slaveSqlSessionTemplate")
    @Primary
    public SqlSessionTemplate sqlSessionTemplate(@Qualifier("slaveSqlSessionFactory") SqlSessionFactory sqlSessionFactory)
            throws Exception {
        return new SqlSessionTemplate(sqlSessionFactory);
    }
}

```

> 二、修改application.properties

```js
#oracle
spring.datasource.oracle.driverClassName= oracle.jdbc.driver.OracleDriver
spring.datasource.oracle.url= jdbc:oracle:thin:@localhost:1521:ORCL
spring.datasource.oracle.username= system
spring.datasource.oracle.password= 123456
spring.datasource.oracle.connectionProperties= 'druid.stat.mergeSql=true;druid.stat.slowSqlMillis=5000;druid.stat.logSlowSql=true'

#sqlserver
spring.datasource.sqlserver.driverClassName= com.microsoft.sqlserver.jdbc.SQLServerDriver
spring.datasource.sqlserver.url= jdbc:sqlserver://localhost;DatabaseName=SBSSM
spring.datasource.sqlserver.username= sa
spring.datasource.sqlserver.password= 123456
spring.datasource.sqlserver.connectionProperties= 'druid.stat.mergeSql=true;druid.stat.slowSqlMillis=5000;druid.stat.logSlowSql=true'


#mybatis
mybatis.mapper-locations=classpath:mybatis/*Mapper.xml
```

- 三、*Mapper.xml

>1、OracleMapper.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="net.person.dao.oracle.OracleDao" >
    <select id="getAllTest"  resultType="net.person.entity.TestEntity">
       SELECT * FROM "SSM"."TEST"
    </select>
</mapper>
```

>2、SqlServerMapper.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd" >
<mapper namespace="net.person.dao.sqlserver.SqlServerDao" >
    <select id="getAllSqlServer"  resultType="net.person.entity.SqlServerEntity">
       SELECT * FROM dbo.TEST
    </select>
</mapper>
```

- 四、dao层

>1、OracleDao

```java
@Repository
@Mapper
public interface OracleDao {
    public List<TestEntity> getAllTest();
}

```

>2、SqlServerDao

```java
@Repository
@Mapper
public interface SqlServerDao {
    public List<SqlServerEntity> getAllSqlServer();
}

```

# <a name="springBoot-03" href="#" >测试</a>

运行测试接口
