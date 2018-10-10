总操作流程：
- 1、[编写代码](#arduino-01)
- 2、[上传编译代码](#arduino-02)
- 3、[查看效果](#arduino-03)

----------
# <a name="arduino-01" href="#" >编写代码</a>
```c
void setup() {
  Serial.begin(9600); //初始化串口，波特率为9600
}

void loop() {
  Serial.println("hello, world"); //向串口打印字符串
}
```
# <a name="arduino-02" href="#" >上传编译代码</a>
![](image/1-1.png)
# <a name="arduino-03" href="#" >查看效果</a>
![](image/1-2.png)

![](image/1-3.png)