总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/7-1.png)
# 写入程序
```
int led = 11;// 定义针脚号，数字类型为整型
void setup()
{
  pinMode(led, OUTPUT);// 设定11号针脚为输出状态
}
void loop()
{
  for (int i= 1; i<= 255; i++ )
  {
    analogWrite(led , i);// 设置LED神灯的当前亮度
    delay( 10 );
  }
  for (int j= 1; j<= 255 ; j++ )
  {
    analogWrite(led , ( 255 - j ));// 设置LED神灯的当前亮度
    delay( 10 );
  }
}
```
### 另外一种方式（ardublock图形编程）
![](image/7-2.png)
# 测试
![](image/7-3.png)