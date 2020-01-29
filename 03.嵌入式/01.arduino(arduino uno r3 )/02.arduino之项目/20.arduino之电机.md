[参考文献--瞬顺时的](http://blog.sina.com.cn/s/blog_8043e91a0102wiar.html)

总操流程：
- 1、[各器件链接](#arduino-01)
- 2、[写入程序](#arduino-02)
- 3、[测试](#arduino-03)

----------
# <a name="arduino-01" href="#" >各器件链接</a>
![](image/20-1.png)
# <a name="arduino-02" href="#" >写程序</a>
```c
int motorPin = 9;

void setup() {
pinMode(motorPin,OUTPUT);
}

void loop() {
   analogWrite(motorPin,150);//analogWrite values from 0 to 255
}
```
# <a name="arduino-03" href="#" >测试</a>
![](image/19-2.png)