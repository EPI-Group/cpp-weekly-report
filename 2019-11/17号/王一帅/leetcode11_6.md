给定一个含有 n 个正整数的数组和一个正整数 s ，找出该数组中满足其和 ≥ s 的长度最小的连续子数组。如果不存在符合条件的连续子数组，返回 0。

示例: 

输入: s = 7, nums = [2,3,1,2,4,3]
输出: 2
解释: 子数组 [4,3] 是该条件下的长度最小的连续子数组。
进阶:

如果你已经完成了O(n) 时间复杂度的解法, 请尝试 O(n log n) 时间复杂度的解法。



\

```c
#define MIN(a, b) ((a) < (b) ? (a) : (b))

int minSubArrayLen(int s, int* nums, int numsSize){
    int i = 0, j = 0, sum = 0, min = 0;
    while(true){
        if(sum < s){
            if(j == numsSize){
                break;
            }
            sum += nums[j++];
        }else{
            if(min == 0){
                min = j - i;
            }
            min = MIN(min, j - i);
            if(min == 1){
                return min;
            }
            sum -= nums[i++];
        }
    }
    return min;
}
```


