[![](https://img.shields.io/badge/参考文献-48步进电机-yellow.svg "参考文献 48步进电机")](http://blog.sina.com.cn/s/blog_8043e91a0102wiar.html)


总操流程：
- 1、各器件链接
- 2、写入程序
- 3、测试

----------
# 各器件链接
![](image/21-1.png)
# 写程序
```
#include <Stepper.h>
#define STEPS 100// 这里设置步进电机旋转一圈是多少步
Stepper stepper(STEPS, 8, 9, 10, 11);

void setup() {
  stepper.setSpeed(90);// 设置电机的转速：每分钟为90步
}

void loop() {
  /**
   * 顺时针旋转数值为正，逆时针旋转数值为负。
   * 转动角度对应数值
   * 1、转360°:2048;
   * 2、转180°:1024;
   * 3、转90°:512;
   */
  stepper.step(512); // 顺时针旋转半周
  delay(500);
  stepper.step(-512); // 逆时针旋转半周
  delay(500);
}
```
# 测试
![](image/19-2.png)