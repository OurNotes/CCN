总操流程：
- 1、写入程序
- 2、测试

----------
# 写程序
```
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
# 测试
![](image/11-1.gif)