在未排序的数组中找到第 k 个最大的元素。请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

示例 1:

输入: [3,2,1,5,6,4] 和 k = 2
输出: 5
示例 2:

输入: [3,2,3,1,2,4,5,5,6] 和 k = 4
输出: 4
说明:

你可以假设 k 总是有效的，且 1 ≤ k ≤ 数组的长度。



```c
void heapfy(int* nums, int len, int i){

    int left = 2 * i + 1;

    int right = 2 * i + 2;

    int min_i = i;

    if(left < len && nums[left] < nums[min_i]) min_i = left;

    if(right < len && nums[right] < nums[min_i]) min_i = right;

    if(min_i != i){

        int tmp = nums[i];

        nums[i] = nums[min_i];

        nums[min_i] = tmp;

        heapfy(nums, len, min_i);

    }

}



int findKthLargest(int* nums, int numsSize, int k){

    for(int i = k/2 - 1; i >= 0; i--){

        heapfy(nums, k, i);

    }

    for(int i = k; i < numsSize; i++){

        if(nums[i] > nums[0]){

            nums[0] = nums[i];

            heapfy(nums, k, 0);

        }

    }

    return nums[0];

}
```

