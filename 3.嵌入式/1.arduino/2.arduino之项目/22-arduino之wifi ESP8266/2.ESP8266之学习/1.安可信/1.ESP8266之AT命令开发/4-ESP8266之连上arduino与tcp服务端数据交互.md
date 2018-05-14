总操作流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

***

8266作为TCP客户端

- 接收服务发送来的信息
# 各器件链接
![](image/4-1.png)
# 写入程序
`注意：上传代码的时候断开RX和TX的连接，完成后接回`

```
#include <SoftwareSerial.h>
SoftwareSerial getData(0, 1);//esp8266-01的TX对应开发板的RX，esp8266-01的RX对应开发板的TX

void setup() {
  getData.begin(115200);
  getAT();
  Serial.begin(115200);
}

void loop() {
  if (getData.available() > 0){
      String str=getData.readString();
      Serial.println(str);
  }
}
void getAT(){
  getData.println("AT+CWMODE=1");//将8266设置为STA模式
  delay(3000);
  getData.println("AT+RST");//设置完之后重启
  delay(3000);
  getData.println("AT+CWJAP=\"WE-178\",\"AbCe@163.com~*~");//8266连接路由器发出的WiFi
  delay(3000);
  getData.println("AT+CIPMUX=0");//启动多连接
  delay(3000);
  getData.println("AT+CIPSTART=\"TCP\",\"192.168.0.103\",8080");//通过协议、IP和端口连接服务器
  delay(3000);
  getData.println("AT+CIPMODE=1");//设置透传
  delay(3000);
  getData.println("AT+CIPSEND");//启动发送
  delay(3000);
  getData.println("Connection Successful");//发送数据
  delay(3000);
 }
```
# 测试
![](image/4-2.png)

![](image/4-3.gif)
- 向服务发送信息
# 各器件链接
![](image/4-4.png)
# 写入程序
`注意：上传代码的时候断开RX和TX的连接，完成后接回`

```
#include <SoftwareSerial.h>
SoftwareSerial sendData(1, 0);//esp8266-01的RX对应开发板的RX，esp8266-01的TX对应开发板的TX

void setup() {
  sendData.begin(115200);
  sendAT();
  Serial.begin(115200);
}

void loop() {
 if (Serial.available() > 0){
      String str=sendData.readString();
      sendData.println(str);
  }
}

 /**
 * 写AT命令，连接服务器
 */
void sendAT(){
  sendData.println("AT+CWMODE=1");//将8266设置为STA模式
  delay(3000);
  sendData.println("AT+RST");//设置完之后重启
  delay(3000);
  sendData.println("AT+CWJAP=\"WE-178\",\"AbCe@163.com~*~");//8266连接路由器发出的WiFi
  delay(3000);
  sendData.println("AT+CIPMUX=0");//启动多连接
  delay(3000);
  sendData.println("AT+CIPSTART=\"TCP\",\"192.168.0.103\",8080");//通过协议、IP和端口连接服务器
  delay(3000);
  sendData.println("AT+CIPMODE=1");//设置透传
  delay(3000);
  sendData.println("AT+CIPSEND");//启动发送
  delay(3000);
  sendData.println("Connection Successful");//发送数据
  delay(3000);
 }

```
# 测试
![](image/4-5.gif)