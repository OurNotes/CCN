总操作流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接

![](image/3-1.png)
# 写入程序
```
#include <SoftwareSerial.h>

SoftwareSerial mySerial(0,1); // RX, TX 配置0、1为软串口
void setup()
{
  Serial.begin(9600);
  mySerial.begin(9600);
}

void loop() // run over and over
{
  if (Serial.available() > 0){
    String str=Serial.readString();
    mySerial.print(str);
  }
  if (mySerial.available() > 0){
      String str=mySerial.readString();
      Serial.print(str);
  }
}
```
# 测试

![](image/3-2.gif)