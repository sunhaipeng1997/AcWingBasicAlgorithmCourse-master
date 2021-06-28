# AcWing 算法基础课 -- 基础算法

## AcWing 785. 快速排序 

`难度：简单`

### 题目描述

给定你一个长度为n的整数数列。

请你使用快速排序对这个数列按照从小到大进行排序。

并将排好序的数列按顺序输出。

**输入格式**

输入共两行，第一行包含整数 n。

第二行包含 n 个整数（所有整数均在$1~10^9$范围内），表示整个数列。

**输出格式**

输出共一行，包含 n 个整数，表示排好序的数列。

**数据范围**

1 ≤ n ≤ 100000

**输入样例**：

```
5
3 1 2 4 5
```

**输出样例**：

```
1 2 3 4 5
```

### Solution

```java 

import java.io.BufferedInputStream;
import java.io.IOException;
import java.util.Scanner;


class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(new BufferedInputStream(System.in));
        int n = sc.nextInt();
        int a[] = new int[n];
        for (int i = 0; i < n; i++) {
            a[i] = sc.nextInt();
        }
        quickSort(a, 0, n - 1);
        for (int i = 0; i < n; i++) {
            System.out.print(a[i] + " ");
        }
    }

    static void quickSort(int[] a, int l, int r) {
        if (l >= r) return;
        int x = a[l];
        int i = l - 1;
        int j = r + 1;
        while (i < j) {
            //快排重点，必须要用++i,和--j 避免[2,3]这种情况
            while (a[++i] < x) ;
            while (a[--j] > x) ;
            if (i < j) {
                int t = a[i];
                a[i] = a[j];
                a[j] = t;
            }
        }
        quickSort(a, l, j);
        quickSort(a, j + 1, r);
    }

}
```

