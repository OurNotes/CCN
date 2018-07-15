总操作流程：
- 1、修改sql文件；
- 2、使用rollbackCount方式回退
    - 2-1、变更数据库；
    - 2-2、回退看效果；
- 3、使用rollbackDate方式回退
    - 3-1、变更数据库；
    - 3-2、回退看效果；
- 4、使用rollbackTag方式回退
    - 3-1、变更数据库和创建tag；
    - 3-2、回退看效果；

***

# 1、修改sql文件
```
--liquibase formatted sql

--changeset DKLi:version_01
CREATE TABLE table2 (
  id int(11) NOT NULL,
  name varchar(255) NOT NULL,
  PRIMARY KEY (id)
) ENGINE=MyISAM;
--rollback drop table table2;

--changeset DKLi:version_02
ALTER TABLE  table2 CHANGE  id  id INT( 11 ) AUTO_INCREMENT;
--rollback ALTER TABLE  table2 CHANGE  id  id INT( 11 ) NOT NULL;

--changeset DKLi:version_03
ALTER TABLE  table2 CHANGE  name  firstname VARCHAR( 255 );
--rollback ALTER TABLE  table2 CHANGE  firstname  name VARCHAR( 255 );

--changeset DKLi:version_04
INSERT INTO table2 (id, firstname) VALUES (NULL, 'name1'),(NULL, 'name2'), (NULL, 'name3');
--rollback DELETE FROM table2 WHERE firstname IN('name1','name2','name3');
```
# 使用rollbackCount方式回退
### 1、变更数据库
```
mvn liquibase:update
```
![](image/3-1.png)

### 2、回退看效果
- 回退1步
```
mvn liquibase:rollback -Dliquibase.rollbackCount=1
```
![](image/3-2.png)

`注意：回退一步后，再次回退，是在回退一次后的基础上再次回退。`

# 使用rollbackDate方式回退
```
mvn liquibase:dropAll #清空数据重新测试

```
### 1、变更数据库
```
mvn liquibase:update
```
![](image/3-3.png)
### 2、回退看效果
- 通过时间指定回退该步
```
mvn liquibase:rollback -Dliquibase.rollbackDate=2018-07-15T07:50:13
```
`注意时间格式是：日期+T+时间``

![](image/3-4.png)

# 使用rollbackTag方式回退
```
mvn liquibase:dropAll #清空数据重新测试
```

### 1、变更数据库和创建tag
```
mvn liquibase:update
```

`注意：每更新一个changeset设置一个tag`

```
mvn liquibase:tag -Dliquibase.tag=[版本号]
如：
mvn liquibase:tag -Dliquibase.tag=version_01
```
![](image/3-5.png)
### 2、回退看效果
- 通过标签指定回退到该步
```
mvn liquibase:rollback -Dliquibase.rollbackTag=version_03
```
![](image/3-6.png)