本業目錄:
- 1、新建一支程序
    - 1.1、問題
    - 1.2、erp登錄測試區的客制區
    - 1.3、erp給新程序權限
    - 1.4、修改文件，移動文件，執行文件
    - 1.5、看效果

***

# 新建一支程序

### 1、問題
```
以caxmr411样子制作一支新的，名字是caxmr413。
```

![](image/2-5.png)

- 製作成這樣

![](image/2-6.png)

### 1、erp登錄測試區的測試區

![](image/2-1.png)

` http://10.10.1.106/cgi-bin/fglccgi/wa/r/gdc-toptest-udm-intranet `
![](image/2-2.png)

```
用戶名：tiptop

密碼：tiptop
```

![](image/2-3.png)

![](image/2-4.png)

![](image/2-7.png)

### 2、erp給新程序權限

![](image/2-10.png)

- 查看caxmr411的以其為模板

![](image/2-11.png)

- 新增caxmr413參數和caxmr411相當

![](image/2-12.png)

注意：erp可以開啟多個窗口，方便參考

![](image/2-13.png)

### 3、修改文件，移動文件，執行文件caxmr411來新增caxmr413

- 修改文件
將caxmr411.4gl和caxmr411.4fd文件複製一份，將文件名caxmr411修改成caxmr413

caxmr413.4gl修改內容

![](image/2-8.png)

- 移動文件

1、將caxmr413.4gl文件複製一份到/u1/toptest/topcust/cxm/4gl 下

2、將caxmr413.4fd文件複製一份到/u1/toptest/topcust/cxm/4fd 下


- 執行文件

1、到/u1/toptest/topcust/cxm/4gl 下執行 r.c2 caxmr413

2、到/u1/toptest/topcust/cxm/4fd 下執行 r.f2 caxmr413

3、到/u1/toptest/topcust/cxm/4gl 下執行 r.l2 caxmr413

### 4、看效果

到/u1/toptest/topcust/cxm/4gl 下執行 exe2 caxmr413

![](image/2-9.png)

![](image/2-6.png)


