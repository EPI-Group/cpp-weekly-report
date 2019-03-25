##### 你正在爬楼梯。它需要n不才能到达顶峰。每次你可以爬1或2步。

#####您可以通过多少不同的方式登顶？

注意：给定n将是一个正整数。

***例1：***输入：2  输出 ：2

说明：有两种方法可以爬到顶部。一.1步+加1步  二.2步

***例2：***输入 ：3 输出 ：3

说明： 有三种方法可以爬到顶部。一.1步+ 1步 +1步  二.1步+2步 三.2步+一步

***代码实现：***

**普通解法：**

```c
int climbStairs(int n) {`

​         `int x = 0;`        

​         `int s = 0;`         

​         `while (2 * x <= n) {` 

​             `s = s + combination1(n - x, x);`         

​             `x = x + 1;`      

​        `}`        

​         `return s;`   

  `}`      

`private int combination1(int a, int b) {`        

​          `int c1 = 1;`       

​          `int c2 = 1;`        

​          `for (int i=1; i<=a-b; i++) {`            

​           `c1 = c1 * (i + b);`            

​           `c2 = c2 * i;`         

​         `}`         

​           `return c1 / c2;`     

  `}`     

  `private int combination2(int a, int b) {` 

​         `if (b == 0 || b == a) {return 1;}`         

​         `return combination(a - 1, b - 1) + combination(a - 1, b);`   

   `}` 

`}
```

**规律解法：**爬楼梯的方法随层数的增长依次为：1  2  3  5  8... 满足**斐波那契**序列，因此

 

```c
int climbStairs(int n) {  

​       int a = 0;        

​       int b = 1;        

​       int f = 0;            

​       for (int i=0; i<n; i++) {       

​            f = a + b;            

​            a = b;          

​            b = f;      

​        }        

​        return f;     

   } 

}


```

