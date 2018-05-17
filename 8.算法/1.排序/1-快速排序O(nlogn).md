[参考文献](https://blog.csdn.net/yzllz001/article/details/50982841)

本页目录：
- 1、应用场景；
- 2、工作原理；
- 3、代码；


***

# 应用场景
`
数组中的元素都是独特的，重复的少
利：不浪费空间又可以快一点的排序
`

# 工作原理
1、取一个元素做基准数（参考）；
2、小于该基准数的元素放其左边，大于该基准数的元素放其右边；
（具体：先从右往左找一个小于基准数的数，再从左往右找一个大于基准数的数，然后交换他们）
3、该基准数的左右数组重复以上操作；

# 代码
```
    public static void sort(int a[], int low, int hight) {
        int i, j, index;
        if (low > hight) {
            return;
        }
        i = low;
        j = hight;
        index = a[i]; // 用子表的第一个记录做基准
        while (i < j) { // 从表的两端交替向中间扫描
            while (i < j && a[j] >= index)
                j--;
            if (i < j)
                a[i++] = a[j];// 用比基准小的记录替换低位记录
            while (i < j && a[i] < index)
                i++;
            if (i < j) // 用比基准大的记录替换高位记录
                a[j--] = a[i];
        }
        a[i] = index;// 将基准数值替换回 a[i]
        sort(a, low, i - 1); // 对低子表进行递归排序
        sort(a, i + 1, hight); // 对高子表进行递归排序

    }

    public static void quickSort(int a[]) {
        sort(a, 0, a.length - 1);
    }

    public static void main(String[] args) {
        int a[] = { 49, 38, 65, 97, 76, 13, 27, 49 };
        quickSort(a);
        System.out.println(Arrays.toString(a));
    }
```