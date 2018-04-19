总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/13-1.png)
# 写程序
```
void setup()
{
  pinMode(10,OUTPUT);          //数字口要选择带#号的具有pwm功能的输出口
}

void loop()
{
  int n = analogRead(A0);     //读取A0模拟口的数值（0-5V 对应 0-1204取值）
  analogWrite(10,n/4);         //PWM最大取值255  所以将模拟口的取值n除以4
}
```
# 测试
`转动电位器可以看到led亮度`