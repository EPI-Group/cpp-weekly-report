##### 1.给定32位有符号整数，整数的反向数字。

  **例1**： 输入：123  输出：321

  **例2**： 输入：-123  输出： -321

  **例3**： 输入：120  输出： 21

  **注意**：假设我们正在处理的环境中，其只能在32位带符号整数的范围内存储的整数：[-2147483648 2147483648] 出于此问题的目的，假设当反向整数溢出时，函数返回0。 

***代码实现***：

```int reverse (int x){
int reverse (int x){
long int isNegative = x<0?-1:1;
long int reversed = 0;
long num = x*isNegative;

while (num){
reversed *= 10;
reversed += num%10;
num /= 10;
}

if((isNegative == -1 && reversed>2147483648) || (isNegative == 1 && reversed>2147483647))
return 0;

int ret = (int)reversed * (int)isNegative;
return ret;
}
```





