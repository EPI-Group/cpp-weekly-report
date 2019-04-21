给定一个包括 *n* 个整数的数组 `nums` 和 一个目标值 `target`。找出 `nums` 中的三个整数，使得它们的和与 `target` 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

```c
例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.

与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).

int threeSumClosest(int* nums, int numsSize, int target) {
    if (nums == NULL || numsSize < 3)
    {
        return 0;
    }
    if (numsSize == 3)
    {
        return nums[0] + nums[1] + nums[2];
    }
    /*sort*/
    for (int i=0; i<numsSize-1; i++)   
    {
        for (int j=i+1; j<numsSize; j++)
        {
            if (nums[i] > nums[j])
            {
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
            }
        }
    }
    int num = nums[0] + nums[1] + nums[2];
    for (int i=0; i < numsSize-2; i++)
    {
        int j = i + 1;
        int k = numsSize - 1;
        while (j < k)
        {
            int sum = nums[i] + nums[j] + nums[k];
            int a = sum > target?(sum-target):(target-sum);
            int b = num > target?(num-target):(target-num);
            if (a < b)
            {
                num = sum;
            }
            if (sum > target)
            {
                k--;
            } 
            else if (sum < target)
            {
                j++;
            }
            else
            {
                return target;    
            }
        }
    }
    return num;
}
```