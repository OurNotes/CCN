总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/3-1.png)
# 写入程序
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
  digitalWrite(led, HIGH);// 向13号针脚输出值为高电压状态，
}
```
###另外一种方式（ardublock图形编程）
![](image/3-2.png)

![](image/3-3.png)

![](image/3-4.png)

![](image/3-5.png)
# 测试
![](image/3-6.png)