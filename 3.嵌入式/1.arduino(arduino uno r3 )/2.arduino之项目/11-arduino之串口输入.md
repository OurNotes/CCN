总操流程：
- 1、[写入程序](#arduino-01)
- 2、[测试](#arduino-02)

----------
# <a name="arduino-01" href="#" >写程序</a>
```c
int val;
void setup()
{
  Serial.begin(9600);
}

void loop()
{
  val = Serial.read();
  if(-1 != val){
    if('H' ==val){
      Serial.println("hello world");
      delay( 500 );
    }
  }

}
```
# <a name="arduino-02" href="#" >测试</a>
![](image/11-1.gif)