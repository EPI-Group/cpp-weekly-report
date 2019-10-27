给定一个包含非负整数的数组，你的任务是统计其中可以组成三角形三条边的三元组个数。

示例 1:

输入: [2,2,3,4]
输出: 3
解释:
有效的组合是: 
2,3,4 (使用第一个 2)
2,3,4 (使用第二个 2)
2,2,3
注意:

数组长度不超过1000。
数组里整数的范围为 [0, 1000]。



```c
void swap(int* i, int* j) {
    int tmp = *i;
    *i = *j;
    *j = tmp;
}

int* partition(int* nums, int lo, int hi) {
    int less = lo, more = hi + 1, i = lo + 1;
    while (i < more) {
        if (nums[i] < nums[lo]) {
            swap(nums + (++less), nums + (i++));
        } else if (nums[i] > nums[lo]) {
            swap(nums + (--more), nums + i);
        } else {
            ++i;
        }
    }
    swap(nums + lo, nums + less--);
    int* p = (int*) malloc(sizeof(int) * 2);
    p[0] = less;
    p[1] = more;
    return p;
}

void quick_sort(int* nums, int lo, int hi) {
    int n = hi - lo + 1;
    if (n <= 0) {
        return;
    }
    int j = lo + rand() % n;
    swap(nums + lo, nums + j);
    int* p = partition(nums, lo, hi);
    quick_sort(nums, lo, p[0]);
    quick_sort(nums, p[1], hi);
    free(p);
}

int triangleNumber(int* nums, int numsSize){
    quick_sort(nums, 0, numsSize - 1);
    int ans = 0;
    for (int i = numsSize - 1; i > 1; --i) {
        int lo = 0, hi = i - 1;
        while (lo < hi) {
            if (nums[lo] + nums[hi] > nums[i]) {
                ans += hi - lo;
                --hi;
            } else {
                ++lo;
            }
        }
    }
    return ans;
}
```

