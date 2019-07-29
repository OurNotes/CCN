总操作流程：
- 1、[下载模板](#STM-M4-01)
- 2、[创建修改文件和配置环境](#STM-M4-02)
    - 2.[1、创建修改文件夹和文件](#STM-M4-02-01)
    - 2.[2、配置环境](#STM-M4-02-02)
- 3、[程序下载看效果](#STM-M4-03)


***

# <a name="STM-M4-01" href="#" >下载模板</a>
[![](https://img.shields.io/badge/源码-Template--FirmwareLibrary-blue.svg "源码 Template-FirmwareLibrary")](https://github.com/lidekai/Template-FirmwareLibrary.git)

# <a name="STM-M4-02" href="#" >创建修改文件和配置环境</a>

### <a name="STM-M4-02-01" href="#" >1、创建修改文件夹和文件</a>
- 将根目录名改成：RacingLights
- 创建OBJ文件夹
- 创建HARDWARE文件夹，且其下也创建LED文件夹
- 在LED文件夹下创建led.c和led.h文件
- led.c
```c
#include "led.h"
#include "stm32f4xx.h"

/**
* LED IO 初始化
*/
void LED_Init(void)
{

 GPIO_InitTypeDef GPIO_InitStructure;

 RCC_AHB1PeriphClockCmd(RCC_AHB1Periph_GPIOF,ENABLE);//使能 GPIOF 时钟

//GPIOF9,F10 初始化设置
 GPIO_InitStructure.GPIO_Pin = GPIO_Pin_9 | GPIO_Pin_10;//LED0 和 LED1 对应 IO 口
 GPIO_InitStructure.GPIO_Mode = GPIO_Mode_OUT;//普通输出模式
 GPIO_InitStructure.GPIO_OType = GPIO_OType_PP;//推挽输出
 GPIO_InitStructure.GPIO_Speed = GPIO_Speed_100MHz;//100MHz
 GPIO_InitStructure.GPIO_PuPd = GPIO_PuPd_UP;//上拉

 GPIO_Init(GPIOF, &GPIO_InitStructure);//初始化 GPIO
 GPIO_SetBits(GPIOF,GPIO_Pin_9 | GPIO_Pin_10);//GPIOF9,F10 设置高，灯灭
}

```
- led.h
```c
#ifndef  __LED_H

#define __LED_H

#include "sys.h"
//LED 端口定义
#define LED0 PFout(9) // DS0 PF9
#define LED1 PFout(10)// DS1 PF10

void LED_Init(void);//初始化

#endif


```

- main.c
```c
#include "sys.h"
#include "delay.h"
#include "usart.h"
#include "led.h"
int main(void)
{
delay_init(168); //初始化延时函数
LED_Init(); //初始化 LED 端口
/**下面是通过直接操作库函数的方式实现 IO 控制**/
	while(1)
	{
		GPIO_ResetBits(GPIOF,GPIO_Pin_9); //LED0 对应引脚 GPIOF.9 拉低，亮 等同 LED0=0;
		GPIO_SetBits(GPIOF,GPIO_Pin_10); //LED1 对应引脚 GPIOF.10 拉高，灭 等同 LED1=1;
		delay_ms(500); //延时 500ms
		GPIO_SetBits(GPIOF,GPIO_Pin_9); //LED0对应引脚 GPIOF.0拉高，灭 等同 LED0=1;
		GPIO_ResetBits(GPIOF,GPIO_Pin_10); //LED1 对应引脚 GPIOF.10 拉低，亮 等同 LED1=0;
		delay_ms(500); //延时 500ms
	}
}

```

### <a name="STM-M4-02-02" href="#" >2、配置环境</a>
- 导入文件

![](image/2-1.png)

- 设置文件路径

`STM32F40_41xxx,USE_STDPERIPH_DRIVER`

![](image/2-2.png)


# <a name="STM-M4-03" href="#" >程序下载看效果</a>
- 编译

![](image/1-13.png)

- 将程序下载到开发板

![](image/2-3.png)

- 看效果

`开发板灯一闪闪的发亮`
