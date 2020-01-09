总操流程：
- 1、[写入程序](#arduino-01)
- 2、[测试](#arduino-02)

----------
# <a name="arduino-01" href="#" >写程序</a>
```c
void setup()
{
  Serial.begin(9600);
}

void loop()
{
  Serial.print("hello world");
  Serial.println();
  delay( 1000 );
}
```
### 另外一种方式（ardublock图形编程）

![](image/10-1.png)
# <a name="arduino-02" href="#" >测试</a>

![](image/10-2.png)