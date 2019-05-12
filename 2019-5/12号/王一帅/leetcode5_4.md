实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须**原地**修改，只允许使用额外常数空间。

以下是一些例子，输入位于左侧列，其相应输出位于右侧列。
`1,2,3` → `1,3,2`
`3,2,1` → `1,2,3`
`1,1,5` → `1,5,1`



```C
void nextPermutation(int* nums, int numsSize){
    int i = 0, t = 0, t_index = 0;
    for(i = numsSize - 1; i > 0; i--) {
        if(nums[i] > nums[i - 1]) {
            t_index = i - 1;
            t = nums[i - 1];
            break;
        }     
    }
    if(i == 0) {
        for(i = 0; i < numsSize / 2; i++) {
            t = nums[i];
            nums[i] = nums[numsSize - 1 - i];
            nums[numsSize - 1 - i] = t;
        }
    }
    else {
        for(i = numsSize - 1; i > t_index; i--) {
            if(nums[i] > t) {
                nums[t_index] = nums[i];
                nums[i] = t;
                break;
            }
        }
        for(i = 0; i < (numsSize - 1 - t_index) / 2; i++) {
            int j = i + 1 + t_index;
            t = nums[j];
            nums[j] = nums[numsSize - i - 1];
            nums[numsSize - 1 - i] = t;
        }
    }
    return nums;
}
```

