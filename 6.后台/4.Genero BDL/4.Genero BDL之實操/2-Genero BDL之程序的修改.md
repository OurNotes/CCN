本業目錄:
- 1、新建一支程序
    - 1.1、問題
    - 1.2、erp登錄測試區的客制區
    - 1.3、修改文件，移動文件，執行文件
    - 1.4、erp給新程序權限
    - 1.5、看效果

***

# 新建一支程序

### 1、問題
`
以caxmr411為模板製作出新的一個程序出來caxmr413
`

![](image/2-1.png)

### 2、erp登錄測試區的測試區

- 使用gdc創建一個進測試區的ERP登錄界面

![](image/2-2.png)

```
http://10.10.1.106/cgi-bin/fglccgi/wa/r/gdc-toptest-udm-intranet
```

![](image/2-3.png)



- erp登錄進客制區的erp

```
用戶名：tiptop

密碼：tiptop
```
![](image/2-4.png)

`選擇對應的系統`

![](image/2-5.png)

- ssh登錄進入測試區的克制區

![](image/2-6.png)

### 3、修改文件，移動文件，執行文件

- 修改文件

1、複製一份caxmr411.4gl，將名字修改成caxmr413.4gl，程序裡面的caxmr411字符串修改成caxmr413

2、複製一份caxmr411.4fd，將名字修改成caxmr413.4fd

- 移動文件

1、將將caxmr413.4gl文件移到/u1/toptest/topcust/cxm/4gl文件夾下

2、將caxmr413.4fd文件移到/u1/toptest/topcust/cxm/4fd文件夾下

- 執行文件

1、進入4gl的文件夾執行r.c2 caxmr413

2、進入4fd的文件夾執行r.f2 caxmr413

### 4、erp給新程序設置權限

- 給新程序授運行路徑權限

![](image/2-7.png)

![](image/2-8.png)

![](image/2-9.png)

- 給新程序授畫面權限

![](image/2-10.png)

![](image/2-11.png)

![](image/2-12.png)

![](image/2-13.png)

![](image/2-14.png)

- 看畫面設置是否成功

![](image/2-15.png)

![](image/2-16.png)

- 記得更新

![](image/2-17.png)

### 5、看效果

- 方式一

![](image/2-18.gif)

- 方式二

![](image/2-19.gif)

- 方式三

![](image/2-20.gif)




