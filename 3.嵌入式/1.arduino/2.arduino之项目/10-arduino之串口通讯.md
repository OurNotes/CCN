总操流程：
- 1、写入程序
- 2、测试

----------
# 写程序
```
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
# 测试

![](image/10-2.png)