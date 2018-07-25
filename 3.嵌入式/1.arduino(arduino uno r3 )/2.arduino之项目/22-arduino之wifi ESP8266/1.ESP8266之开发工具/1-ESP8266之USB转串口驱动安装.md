总操作流程：
- 1、[驱动下载安装](#ESP8266-01)
- 2、[esp8266链接usb转串口](#ESP8266-02)
- 3、[测试](#ESP8266-03)

----------

'esp8266引脚说明：'

| pin | 名称 | 注释 |
| :-: | :-: | :-: |
| 1 | 3V3| 供电3.3V |
| 2 | RX | UART |
| 3 | IO16 | 这个脚还有一个名称叫RESET |
| 4 | IO0 | GPIO0 |
| 4 | EN | 又名CHIP_EN/CH_PD |
| 4 | IO2 | GPIO2 |
| 4 | TX | UART |
| 4 | GND | 接地，电源负极 |
# <a name="ESP8266-01" href="#" >驱动下载安装</a>
将USB 转串口插到电脑上，下载安装驱动
[![](https://img.shields.io/badge/CH341SER-exe-green.svg "CH341SER exe")](https://pan.baidu.com/s/1bPLiDqTQ5e6CPCk1NYWfDQ)

- 安装成功标志：

![](image/1-1.png)

# <a name="ESP8266-02" href="#" >esp8266链接usb转串口</a>
![](image/1-2.png)
# <a name="ESP8266-03" href="#" >测试</a>
[![](https://img.shields.io/badge/参考文献-调试篇-yellow.svg "参考文献 调试")](https://blog.csdn.net/jackhuang2015/article/details/45032571)

测试工具测试[![](https://img.shields.io/badge/USR--TCP232--Test-exe-green.svg "USR-TCP232-Test exe")](https://pan.baidu.com/s/1NYXFJInH5SEbsExB9rbR1Q)

![](image/1-3.png)
