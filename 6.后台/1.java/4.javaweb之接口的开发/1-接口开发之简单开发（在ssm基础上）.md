总操作流程：
- 1、pom.xml添加相应依赖包
- 2、添加Json的实体类
- 3、添加json的工具类
- 4、修改service
- 5、修改contor类

[![](https://img.shields.io/badge/源码-idea--Interface-blue.svg "源码 idea-Interface")](https://github.com/lidekai/idea-Interface.git)

----------

# pom.xml添加相应依赖包
```
 版本设置处添加：
    <jackson.version>2.9.2</jackson.version><!-- json -->
    <servletApi.version>2.5</servletApi.version><!--servletApi-->

导入的包处添加：
    <!-- ============================jackson=================================== -->
    <dependency>
	    <groupId>com.fasterxml.jackson.core</groupId>
	    <artifactId>jackson-databind</artifactId>
	    <version>${jackson.version}</version>
	</dependency>
	
	<dependency>
	    <groupId>com.fasterxml.jackson.core</groupId>
	    <artifactId>jackson-core</artifactId>
	    <version>${jackson.version}</version>
	</dependency>
	
	<dependency>
	    <groupId>com.fasterxml.jackson.core</groupId>
	    <artifactId>jackson-annotations</artifactId>
	    <version>${jackson.version}</version>
	</dependency>
    <!--============================servlet-api============================-->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>servlet-api</artifactId>
      <version>${servletApi.version}</version>
      <scope>provided</scope>
    </dependency>
```

# 添加Json的实体类
### 1、AbstractJsonObject
```
package net.person.model.json;

import java.util.Date;
/**
 *Json数据的基类
 * Created by a2665 on 2018/2/4.
 */
public class AbstractJsonObject {
    //code
    private String code;
    //msg
    private String msg;
    private Long time = new Date().getTime();
    public String getCode() {
        return code;
    }
    public void setCode(String code) {
        this.code = code;
    }
    /**
     * @return the time
     */
    public Long getTime() {
        return time;
    }
    /**
     * @param time
     *            the time to set
     */
    public void setTime(Long time) {
        this.time = time;
    }
    public String getMsg() {
        return msg;
    }
    public void setMsg(String msg) {
        this.msg = msg;
    }
    public void setContent(String code, String msg) {
        this.code = code;
        this.msg = msg;
    }
    public void setStatusObject(StatusObject statusObject) {
        this.code = statusObject.getCode();
        this.msg = statusObject.getMsg();
    }
}

```
### 2、ListObject
```
package net.person.model.json;

import java.util.List;

/**
 * Json数组类
 * Created by a2665 on 2018/2/5.
 */
public class ListObject extends AbstractJsonObject {

    // 列表对象
    private List<?> items;

    public List<?> getItems() {
        return items;
    }

    public void setItems(List<?> items) {
        this.items = items;
    }

}

```
### 3、SingleObject
```
package net.person.model.json;

/**
 * Json对象类
 * Created by a2665 on 2018/2/4.
 */
public class SingleObject extends AbstractJsonObject{
    private Object object;
    public Object getObject() {
        return object;
    }
    public void setObject(Object object) {
        this.object = object;
    }
}
```
### 4、StatusObject
```
package net.person.model.json;

/**
 * 状态对象
 * Created by a2665 on 2018/2/4.
 */
public class StatusObject {
    // 状态码
    private String code;
    // 状态信息
    private String msg;
    public StatusObject(String code, String msg) {
        super();
        this.code = code;
        this.msg = msg;
    }
    public String getCode() {
        return code;
    }
    public void setCode(String code) {
        this.code = code;
    }
    public String getMsg() {
        return msg;
    }
    public void setMsg(String msg) {
        this.msg = msg;
    }
}

```
# 添加json的工具类
### 1、JackJsonUtils
```
package net.person.utils;

import com.fasterxml.jackson.databind.ObjectMapper;

/**
 * 生成json数据和解析json数据
 * Created by a2665 on 2018/2/4.
 */
public class JackJsonUtils {
    static ObjectMapper objectMapper;
    /**
     * 解析json
     *
     * @param content
     * @param valueType
     * @return
     */
    public static <T> T fromJson(String content, Class<T> valueType) {
        if (objectMapper == null) {
            objectMapper = new ObjectMapper();
        }
        try {
            return objectMapper.readValue(content, valueType);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return null;
    }
    /**
     * 生成json
     *
     * @param object
     * @return
     */
    public static String toJson(Object object) {
        if (objectMapper == null) {
            objectMapper = new ObjectMapper();
        }
        try {
            return objectMapper.writeValueAsString(object);
        } catch (Exception e) {
            e.printStackTrace();
        }
        return null;
    }
}

```
### 2、ResponseUtils
```
package net.person.utils;

import javax.servlet.http.HttpServletResponse;

import java.io.IOException;
/**
 * 响应处理
 * Created by a2665 on 2018/2/4.
 */
public class ResponseUtils {
    /**
     * 返回json 串
     *
     * @param response
     * @param text
     */
    public static void renderJson(HttpServletResponse response, String text) {
        // System.out.print(text);
        render(response, "text/plain;charset=UTF-8", text);
    }
    /**
     * 发送内容。使用UTF-8编码。
     *
     * @param response
     * @param contentType
     * @param text
     */
    public static void render(HttpServletResponse response, String contentType, String text) {
        response.setContentType(contentType);
        response.setCharacterEncoding("utf-8");
        response.setHeader("Pragma", "No-cache");
        response.setHeader("Cache-Control", "no-cache");
        response.setDateHeader("Expires", 0);
        try {
            response.getWriter().write(text);
        } catch (IOException e) {
        }
    }
}

```
### 3、StatusCode
```
package net.person.utils;

/**
 * 定义响应状态码
 * Created by a2665 on 2018/2/5.
 */
public class StatusCode {
    public static String CODE_SUCCESS = "ok";//访问成功

    public static String CODE_ERROR = "0001"; //访问错误

    public static String CODE_ERROR_PARAMETER = "0002";//参数错误

    public static String CODE_ERROR_PROGRAM = "0003";//程序异常

    public static String CODE_ERROR_NO_LOGIN_OR_TIMEOUT = "0004";//未登录或登录超时,请重新登录

    public static String CODE_ERROR_EXIST_OPERATION = "0005";//已操作
}

```
### 4、StatusHouse
```
package net.person.utils;

import net.person.model.json.StatusObject;

/**
 * 状态封装类
 * Created by a2665 on 2018/2/5.
 */
public class StatusHouse {
    public static StatusObject COMMON_STATUS_OK = new StatusObject(StatusCode.CODE_SUCCESS, "访问成功");
    public static StatusObject COMMON_STATUS_ERROR = new StatusObject(StatusCode.CODE_ERROR, "访问错误，错误码：(" + StatusCode.CODE_ERROR + ")");
    public static StatusObject COMMON_STATUS_NO_LOGIN_OR_TIMEOUT = new StatusObject(StatusCode.CODE_ERROR_NO_LOGIN_OR_TIMEOUT, "未登录或登录超时,请重新登录,错误码：(" + StatusCode.CODE_ERROR_NO_LOGIN_OR_TIMEOUT + ")");
    public static StatusObject COMMON_STATUS_ERROR_PROGRAM = new StatusObject(StatusCode.CODE_ERROR_PROGRAM, "程序异常，错误码：(" + StatusCode.CODE_ERROR_PROGRAM + ")");
    public static StatusObject COMMON_STATUS_ERROR_PARAMETER = new StatusObject(StatusCode.CODE_ERROR_PARAMETER, "参数错误，错误码：(" + StatusCode.CODE_ERROR_PARAMETER + ")");
    public static StatusObject COMMON_STATUS_EXIST_OPERATION = new StatusObject(StatusCode.CODE_ERROR_EXIST_OPERATION, "已操作，错误码：(" + StatusCode.CODE_ERROR_EXIST_OPERATION + ")");
}

```
# 修改service
### 1、TestService
```
package net.person.service;


import javax.servlet.http.HttpServletResponse;

/**
 * service的接口
 * Created by admin on 2018/1/31.
 */
public interface TestService {
    //获取test表所有数据
    public void getAllTest(HttpServletResponse response);
}

```
### 2、TestServiceImpl
```
package net.person.service.impl;

import net.person.dao.TestDao;
import net.person.model.TestModel;
import net.person.model.json.ListObject;
import net.person.service.TestService;
import net.person.utils.JackJsonUtils;
import net.person.utils.ResponseUtils;
import net.person.utils.StatusHouse;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;

import javax.servlet.http.HttpServletResponse;
import java.util.List;

/**
 * service的实现类
 * Created by admin on 2018/1/31.
 */
@Service
@Transactional
public class TestServiceImpl implements TestService {

    public TestDao testDao;
    @Autowired
    public void setTestDao(TestDao testDao) {
        this.testDao = testDao;
    }
    public void getAllTest(HttpServletResponse response) {
        List<TestModel> list = testDao.getAllTest();
        ListObject listObject=new ListObject();
        listObject.setItems(list);
        listObject.setStatusObject(StatusHouse.COMMON_STATUS_OK);
        String responseText = JackJsonUtils.toJson(listObject);
        ResponseUtils.renderJson(response, responseText);
    }
}
```
# 修改contor类
```
package net.person.controller;

import net.person.service.TestService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

import javax.servlet.http.HttpServletResponse;


/**
 * 测试springMVC映射
 * Created by admin on 2018/1/31.
 */
@Controller
@RequestMapping("/home")
public class TestController {
    public TestService testServiceImpl;
    @Autowired
    public void setTestService(TestService testServiceImpl) {
        this.testServiceImpl = testServiceImpl;
    }

    @RequestMapping(value="/index",method= RequestMethod.GET)
    public void editItemsQuery(Model model,HttpServletResponse response) throws Exception{
        testServiceImpl.getAllTest(response);
    }
}

```