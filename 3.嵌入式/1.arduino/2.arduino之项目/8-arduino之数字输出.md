总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/8-1.png)
# 写入程序
```
int startPin = 2 ;
int endPin = 7 ;
int index = 0 ;

void setup()
{
  for(int i = startPin;i <= endPin;i++){
    pinMode(i,OUTPUT);
  }
}

void loop()
{
  for(int i = startPin;i <= endPin;i++){
   digitalWrite(i,LOW);
  }
  digitalWrite(startPin + index,HIGH);
  index = (index + 1) % (endPin -  startPin + 1);
  delay(100);
}
```
# 测试
![](image/8-2.gif)