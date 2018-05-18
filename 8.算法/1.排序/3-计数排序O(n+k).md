[参考文献](https://www.cnblogs.com/zer0Black/p/6169858.html)

本页目录：
- 1、应用场景；
- 2、工作原理；
- 3、代码；

***

# 应用场景
`
取值范围非常有限
缺点：首先如果想用数组统计各个元素出现的次数，它的值必须是正整数
`

# 工作原理
1、创建一个数组（排序数组），长度是待排序数组的最大值和最小值的差值；
2、取待排序的元素，查找待排序数组中的个数，元素对应排序数组的下标，个数对应排序数组的值。
3、排序好后，为下标就是(如果它对应的值不为零的)。

# 代码
```
import java.util.Arrays;

/**
 * Created by DK_Li on 2018/5/18.
 */
public class test {
    public static int[] countSort(int[] arr){
        if (arr == null || arr.length == 0) {
            return null;
        }

        int max = Integer.MIN_VALUE;
        int min = Integer.MAX_VALUE;

        //找出数组中的最大最小值
        for(int i = 0; i < arr.length; i++){
            max = Math.max(max, arr[i]);
            min = Math.min(min, arr[i]);
        }

        int help[] = new int[max];

        //找出每个数字出现的次数
        for(int i = 0; i < arr.length; i++){
            int mapPos = arr[i] - min;
            help[mapPos]++;
        }

        int index = 0;
        for(int i = 0; i < help.length; i++){
            while(help[i]-- > 0){
                arr[index++] = i+min;
            }
        }

        return arr;
    }
    public static void main(String[] args) {
        int[] arr = new int[]{4,3,6,3,5,1};
        System.out.println(Arrays.toString(countSort(arr)));
    }


}

```