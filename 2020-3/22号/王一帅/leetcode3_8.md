编写一个程序，找出第 n 个丑数。

丑数就是只包含质因数 2, 3, 5 的正整数。

示例:

输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
说明:  

1 是丑数。
n 不超过1690。



```c
int minofthree(int a, int b, int c){
    int temp = a < b ? a : b;
    return temp < c ? temp : c;
}

int nthUglyNumber(int n){
    int* nums = (int*)calloc(n, sizeof(int));
    nums[0] = 1;
    int p2=0, p3=0, p5=0, min;
    for(int i=1; i<n; i++){
        min = minofthree(nums[p2]*2, nums[p3]*3, nums[p5]*5);
        nums[i] = min;
        if(min == nums[p2]*2) p2++;
        if(min == nums[p3]*3) p3++;
        if(min == nums[p5]*5) p5++;
    }
    return nums[n-1];
}
```