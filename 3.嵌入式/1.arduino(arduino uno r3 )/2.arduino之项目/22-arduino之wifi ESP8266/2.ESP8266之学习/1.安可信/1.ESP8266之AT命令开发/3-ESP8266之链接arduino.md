总操作流程：
- 1、[各器件链接](#ESP8266-01)
- 2、[写入程序](#ESP8266-02)
- 3、[测试](#ESP8266-03)

----------
# <a name="ESP8266-01" href="#" >各器件链接</a>

![](image/3-1.png)
# <a name="ESP8266-02" href="#" >写入程序</a>
```c
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
# <a name="ESP8266-03" href="#" >测试</a>

![](image/3-2.gif)