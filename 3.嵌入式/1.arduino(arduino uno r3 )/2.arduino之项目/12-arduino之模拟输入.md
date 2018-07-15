总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
链接各个器件

![](image/12-1.png)
# 写程序
```
int analogPin = A0;
int val = 0 ;
void setup()
{
  Serial.begin(9600);
}

void loop()
{
  val = analogRead(analogPin);
  Serial.println(val);
  delay(1000);
}
```
#测试
`转动电位器可以看到数值变化`
![](image/12-2.gif)