[参考文献--瞬顺时的](http://blog.sina.com.cn/s/blog_8043e91a0102wiar.html)

总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/20-1.png)
# 写程序
```
int motorPin = 9;

void setup() {
pinMode(motorPin,OUTPUT);
}

void loop() {
   analogWrite(motorPin,150);//analogWrite values from 0 to 255
}
```
# 测试
![](image/19-2.png)