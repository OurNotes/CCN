[![](https://img.shields.io/badge/参考文献-LED神灯闪烁-yellow.svg "参考文献 LED神灯闪烁")](http://www.51hei.com/bbs/dpj-41337-1.html)


总操流程：
- 1、[各器件链接](#arduino-01)
- 2、[写入程序](#arduino-02)
- 3、[测试](#arduino-03)

----------
# <a name="arduino-01" href="#" >各器件链接</a>

![](image/5-1.png)
# <a name="arduino-02" href="#" >写入程序</a>
```
int led = 13; // 定义针脚号，数字类型为整型
/**
 * 对Arduino电路板或相关状态进行初始化方法
 */
void setup() {
  pinMode(led, OUTPUT); // 设定13号针脚为输出状态，
}
/**
 *  系统调用，无限循环方法
 */
void loop() {
    digitalWrite(led,HIGH); // 向13号针脚输出值为高电压状态，
    delay(1000); //设定延时时间，1000 = 1秒
    digitalWrite(led,LOW); // 此处向Arduino的13针脚发送低电压状态，
    delay(1000); //设定延时时间，1000 = 1秒
}
```
### 另外一种方式（ardublock图形编程）

![](image/5-2.png)
# <a name="arduino-03" href="#" >测试</a>

![](image/5-3.png)