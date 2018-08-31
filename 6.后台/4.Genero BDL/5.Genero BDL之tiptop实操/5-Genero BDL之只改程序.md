本業目錄:
- [1、問題](#tiptop-01)
- [2、erp登錄測試區的客制區](#tiptop-02)
- [3、修改文件，移動文件，執行文件](#tiptop-03)
- [4、erp給新程序權限](#tiptop-04)
- [5、看效果](#tiptop-05)

***

# <a name="tiptop-01" href="#" >1、問題</a>
`
以caxmr411為模板製作出新的一個程序出來caxmr413
`

![](image/5-1.png)

# <a name="tiptop-02" href="#" >2、erp登錄測試區的測試區</a>

- 使用gdc創建一個進測試區的ERP登錄界面

![](image/5-2.png)

```
http://10.10.1.106/cgi-bin/fglccgi/wa/r/gdc-toptest-udm-intranet
```

![](image/5-3.png)



- erp登錄進客制區的erp

```
用戶名：tiptop

密碼：tiptop
```
![](image/5-4.png)

`選擇對應的系統`

![](image/5-5.png)

- ssh登錄進入測試區的克制區

![](image/5-6.png)

# <a name="tiptop-03" href="#" >3、修改文件，移動文件，執行文件</a>

- 修改文件

1、從/u1/toptest/topcust/cxm/4gl中複製一份caxmr411.4gl，將名字修改成caxmr413.4gl，程序裡面的caxmr411字符串修改成caxmr413

2、從/u1/toptest/topcust/cxm/4fd中複製一份caxmr411.4fd，將名字修改成caxmr413.4fd,打开4fd的文件修改textGroup的text的名称

- 移動文件

1、將將caxmr413.4gl文件移到/u1/toptest/topcust/cxm/4gl文件夾下

2、將caxmr413.4fd文件移到/u1/toptest/topcust/cxm/4fd文件夾下

- 執行文件

1、進入4gl的文件夾執行r.c2 caxmr413

2、進入4fd的文件夾執行r.f2 caxmr413

# <a name="tiptop--04" href="#" >4、erp給新程序設置權限</a>

- 給新程序授運行路徑權限

![](image/5-7.png)

![](image/5-8.png)

![](image/5-9.png)

- 給新程序授畫面權限

![](image/5-10.png)

![](image/5-11.png)

![](image/5-12.png)

![](image/5-13.png)

![](image/5-14.png)

- 看畫面設置是否成功

![](image/5-15.png)

![](image/5-16.png)

- 記得更新

![](image/5-17.png)

### <a name="tiptop-01-05" href="#" >5、看效果</a>

- 方式一

![](image/5-18.gif)

- 方式二

![](image/5-19.gif)

- 方式三

![](image/5-20.gif)



