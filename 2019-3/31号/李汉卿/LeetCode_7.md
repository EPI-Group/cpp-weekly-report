##### 给定表示非负整数的**非空**数字数组，加上整数的1。存储数字使得最高有效数字位于列表的开头，并且数组中的每个元素包含单个数字。您可以假设整数不包含任何前导零，除了数字0本身。

**例1：**

```
输入： [1,2,3] 输出： [1,2,4] 说明：数组表示整数123。
```

**例2：**

```
输入： [4,3,2,1] 输出： [4,3,2,2] 说明：数组表示整数4321。
```

实现代码：

```c
int[] plusOne(int[] digits) {        
        Stack<Integer> st = new Stack<Integer> ();
        
        int d = 0;
        int c = 1;
        int l = 0;
        for (int i=digits.length-1; 0<=i; i--) {
            d = digits[i] + c;
            c = (d > 9) ? 1 : 0;
            d = d - c * 10;
            st.push(d);
            l = l + 1;
        }
        if (c == 1) {
            st.push(1);
            l += 1;
        }
        
        int[] a = new int[l];
        for (int i=0; i<l; i++) {
            a[i] = st.pop();
        }
        
        return a;
    }
}
```

