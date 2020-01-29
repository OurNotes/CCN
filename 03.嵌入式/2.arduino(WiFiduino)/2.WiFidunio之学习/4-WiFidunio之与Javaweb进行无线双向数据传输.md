总操作流程:
- 1、[烧写函数库的程序](#WiFiduino-01)
- 2、[运行Javaweb程序](#WiFiduino-02)
- 3、[测试](#WiFiduino-03)

***

# <a name="WiFiduino-01" href="#" >烧写函数库的程序</a>
![](image/4-1.png)

`修改文件`

![](image/4-2.png)

![](image/4-3.png)

# <a name="WiFiduino-02" href="#" >运行Javaweb程序</a>

[![](https://img.shields.io/badge/源码-esp8266--javaweb-blue.svg "源码 esp8266_javaweb")](https://github.com/lidekai/esp8266_javaweb.git)


```java
@Controller
@RequestMapping("/esp8266")
public class ESP8266Controller {
    @RequestMapping(value="/getWiFiData",method= RequestMethod.GET)
    public void getWiFiData(HttpServletRequest request, HttpServletResponse response) throws Exception{
        request.setCharacterEncoding("utf-8");  //这里不设置编码会有乱码
        System.out.println("====================================");
        String sord = request.getParameter("request");//排序方式
        System.out.println(sord);
        System.out.println("====================================");
        response.setContentType("text/html;charset=utf-8");
        PrintWriter out = response.getWriter();
        out.println("111111111111111111111");
        out.flush();
        out.close();
    }
}

```

![](image/4-4.png)
# <a name="WiFiduino-03" href="#" >测试</a>

![](image/4-5.gif)