# 报错信息

```
Cause: java.sql.SQLException: 无效的列类型: getBigDecimal not implemented for class oracle.jdbc.driver.T4CDateAccessor
```

# 解决方案

- 1、如果不指定number的长度，或指定长度n>18 
>id number not null，转换为pojo类时，为java.math.BigDecimal类型

- 2、如果number的长度在10 <= n <= 18
>id number(n) not null，转换为pojo类时，为java.lang.Long类型

- 3、如果number的长度在1 <= n <= 9 
>id number(n) not null，转换为pojo类时，为java.lang.Integer类型