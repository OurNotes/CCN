总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/15-1.png)
# 写程序
```
int LM35 = A0;
void setup() {
  // put your setup code here, to run once:
Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
  float temp = (5.0 * analogRead(LM35) * 100.0) / 1024;
  Serial.println(temp);
  delay( 1000 );
}
```
# 测试
![](image/14-2.png)