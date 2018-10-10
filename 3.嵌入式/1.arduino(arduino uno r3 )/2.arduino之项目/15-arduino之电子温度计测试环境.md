总操流程：
- 1、[各器件链接](#arduino-01)
- 2、[写入程序](#arduino-02)
- 3、[测试](#arduino-03)

----------
# <a name="arduino-01" href="#" >各器件链接</a>
![](image/15-1.png)
# <a name="arduino-02" href="#" >写程序</a>
```c
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
# <a name="arduino-03" href="#" >测试</a>
![](image/14-2.png)