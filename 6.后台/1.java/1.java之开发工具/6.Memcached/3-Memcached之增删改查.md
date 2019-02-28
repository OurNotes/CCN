总操作流程：
- 1、创建Java
- 2、测试

***

# 创建Java

>1、创建model
```java
package net.person.model;

import com.alibaba.fastjson.annotation.JSONField;

import java.io.Serializable;

/**
 * Created by admin on 2019/2/27.
 */
public class TestModel implements Serializable {
    @JSONField(name="ID",ordinal =1)
    private int uuid;
    @JSONField(name="NAME",ordinal =2)
    private String userName;
    @JSONField(name="AGE",ordinal =3)
    private int age;

    public TestModel(){}

    public TestModel(int uuid, String userName, int age) {
        this.uuid = uuid;
        this.userName = userName;
        this.age = age;
    }

    public int getUuid() {
        return uuid;
    }

    public void setUuid(int uuid) {
        this.uuid = uuid;
    }

    public String getUserName() {
        return userName;
    }

    public void setUserName(String userName) {
        this.userName = userName;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "TestModel{" +
                "uuid=" + uuid +
                ", userName='" + userName + '\'' +
                ", age=" + age +
                '}';
    }
}


```

>2、ConnectonMemcached。创建连接Memcached类
```java
package net.person.memcached;

import net.rubyeye.xmemcached.MemcachedClient;
import net.rubyeye.xmemcached.MemcachedClientBuilder;
import net.rubyeye.xmemcached.XMemcachedClient;
import net.rubyeye.xmemcached.XMemcachedClientBuilder;
import net.rubyeye.xmemcached.exception.MemcachedException;
import net.rubyeye.xmemcached.utils.AddrUtil;
import org.junit.Test;

import java.io.IOException;
import java.util.concurrent.TimeoutException;

/**
 * Created by admin on 2019/2/27.
 */
public class ConnectonMemcached {
    public static MemcachedClient getClient(){
// 连接配置
        MemcachedClientBuilder memcachedClientBuilder = new XMemcachedClientBuilder(AddrUtil.getAddresses("10.10.2.4:2222"));
        // 创建与服务端之间的连接[ip地址，端口号，用户名和密码]
        // 获取操作业务对象
        MemcachedClient memcachedClient = null;
        try {
            memcachedClient = memcachedClientBuilder.build();
        } catch (IOException e) {
            e.printStackTrace();
        }
        return memcachedClient;
    }

    // 测试是否连接成功
    @Test
    public void cluTest() throws  Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
     }

}
```

# 测试

> 创建测试类
```java
package net.person.memcached;

import com.alibaba.fastjson.JSON;
import net.person.memcached.ConnectonMemcached;
import net.person.model.TestModel;
import net.rubyeye.xmemcached.GetsResponse;
import net.rubyeye.xmemcached.MemcachedClient;
import org.junit.Test;

import java.util.Map;

/**
 * Created by admin on 2019/2/27.
 */
public class MemcachedAPI {
    static MemcachedClient client = ConnectonMemcached.getClient();

    /**
     * 查询：get
     * @param key
     * @throws Exception
     */
    public static String showGet(String key)throws  Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String um = memcachedClient.get(key);
        return  um;
    }

    /**
     * 查询：gets
     * @param key
     * @throws Exception
     */
    public static GetsResponse<TestModel> showGets(String key)throws  Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        return memcachedClient.gets(key);
    }


    /**
     * 新增：set
     * @param um
     * @throws Exception
     */
    public static void showSet(TestModel um) throws Exception {
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String jsonOutput= JSON.toJSONString(um);
        memcachedClient.set("set-user",3600,jsonOutput);
    }
    /**
     * 新增：add
     * @param um
     * @throws Exception
     */
    public static void showAdd(TestModel um) throws Exception {
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String jsonOutput= JSON.toJSONString(um);
        memcachedClient.add("add-user",3600,jsonOutput);
    }

    /**
     * 修改：replace
     * @param um
     * @throws Exception
     */
    public static void showReplace(TestModel um) throws Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String jsonOutput= JSON.toJSONString(um);
        memcachedClient.replace("set-user",3600,jsonOutput);
    }

    /**
     * 修改：append
     * @param um
     * @throws Exception
     */
    public static void showAppend(TestModel um) throws Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String jsonOutput= JSON.toJSONString(um);
        memcachedClient.append("set-user",jsonOutput);
    }

    /**
     * 修改：prepend
     * @param um
     * @throws Exception
     */
    public static void showPrepend(TestModel um) throws Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String jsonOutput= JSON.toJSONString(um);
        memcachedClient.prepend("set-user",jsonOutput);
    }

    /**
     * 修改：cas
     * @param um
     * @throws Exception
     */
    public static void showCas(TestModel um,String key) throws Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        String jsonOutput= JSON.toJSONString(um);
        long cas=memcachedClient.gets(key).getCas();
        memcachedClient.cas(key,3600,jsonOutput,cas);
    }

    /**
     * 删除：delete
     * @param key
     * @throws Exception
     */
    public static void showDelete(String key) throws Exception{
        MemcachedClient memcachedClient = ConnectonMemcached.getClient();
        memcachedClient.delete(key);
    }



    @Test
    public void showMemcached() throws  Exception {
        TestModel um1=new TestModel(1,"hello1",18);
        showSet(um1);
        System.out.println("===================set=====================");
        System.out.println("新增set: "+showGet("set-user"));
        System.out.println("获取cas: "+showGets("set-user").getCas());

        TestModel um2=new TestModel(2,"hello2",18);
        showAdd(um2);
        System.out.println("===================add=====================");
        System.out.println("新增add: "+showGet("add-user"));
        System.out.println("获取cas: "+showGets("add-user").getCas());

        TestModel um3=new TestModel(3,"hello3",18);
        showReplace(um3);
        System.out.println("===================replace=====================");
        System.out.println("修改replace: "+showGet("set-user"));
        System.out.println("获取cas: "+showGets("set-user").getCas());

        TestModel um4=new TestModel(4,"hello4",18);
        showAppend(um4);
        System.out.println("===================append=====================");
        System.out.println("修改append: "+showGet("set-user"));
        System.out.println("获取cas: "+showGets("set-user").getCas());

        TestModel um5=new TestModel(5,"hello4",18);
        showPrepend(um5);
        System.out.println("===================prepend=====================");
        System.out.println("修改prepend: "+showGet("set-user"));
        System.out.println("获取cas: "+showGets("set-user").getCas());

        TestModel um6=new TestModel(6,"hello6",18);
        showCas(um6,"set-user");
        System.out.println("===================cas=====================");
        System.out.println("修改cas: "+showGet("set-user"));
        System.out.println("获取cas: "+showGets("set-user").getCas());

        System.out.println("===================delete=====================");
        showDelete("set-user");
        showDelete("add-user");
        System.out.println(showGet("set-user"));
        System.out.println(showGet("add-user"));



    }
}
```
