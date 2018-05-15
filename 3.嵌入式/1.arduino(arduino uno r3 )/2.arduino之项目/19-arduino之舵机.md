总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/19-1.png)
# 写程序
```
#include <Servo.h>

#define PIN_SERVO 10
Servo myservo;

void setup()
{
  myservo.attach(PIN_SERVO);
}

void loop()
{
  /**
   * 角度范围是0°到180°
   */
  myservo.write(0);
  delay(1000);
  myservo.write(90);
  delay(1000);
}
```
# 测试
![](image/19-2.png)