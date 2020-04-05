给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

示例：

给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
说明:

你可以假设数组不可变。
会多次调用 sumRange 方法。

```c++
typedef struct {
    int *dp;
} NumArray;

NumArray* numArrayCreate(int* nums, int numsSize) {
    NumArray *n = ( NumArray*) malloc ( sizeof(NumArray));
    n->dp = (int *) malloc ( sizeof( int) * (numsSize+1) );
    n->dp[0] = 0;
    for( int i = 1; i <= numsSize; i++ ) {
        n->dp[i] = n->dp[i-1] + nums[i-1];
    } 
    return n;
}

int numArraySumRange(NumArray* obj, int i, int j) {
    return obj->dp[j+1] - obj->dp[i];
}

void numArrayFree(NumArray* obj) {
    free(obj->dp);
    free(obj);
}

/**
 * Your NumArray struct will be instantiated and called as such:
 * NumArray* obj = numArrayCreate(nums, numsSize);
 * int param_1 = numArraySumRange(obj, i, j);
 
 * numArrayFree(obj);
*/
```

