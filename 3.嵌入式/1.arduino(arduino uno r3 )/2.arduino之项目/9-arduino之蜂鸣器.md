总操流程：
- 1、[各器件链接](#arduino-01)
- 2、[写入程序](#arduino-02)
- 3、[测试](#arduino-03)

----------
# <a name="arduino-01" href="#" >各器件链接</a>
![](image/9-1.png)
# <a name="arduino-02" href="#" >写程序</a>
```
int led = 8;
void setup()
{
}

void loop()
{
  tone(led, 1000);
  delay( 1000 );
  noTone(led);
  delay( 1000 );
}
```
另外一种方式（ardublock图形编程）
![](image/9-2.png)
# <a name="arduino-03" href="#" >测试</a>
![](image/9-3.png)