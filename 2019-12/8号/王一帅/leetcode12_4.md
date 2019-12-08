找出所有相加之和为 n 的 k 个数的组合。组合中只允许含有 1 - 9 的正整数，并且每种组合中不存在重复的数字。

说明：

所有数字都是正整数。
解集不能包含重复的组合。 
示例 1:

输入: k = 3, n = 7
输出: [[1,2,4]]
示例 2:

输入: k = 3, n = 9
输出: [[1,2,6], [1,3,5], [2,3,4]]



```c
 \* Return an array of arrays of size *returnSize.

 \* The sizes of the arrays are returned as *returnColumnSizes array.

 \* Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().

 */

void _combinationSum3(int n, int k, int* buf, int bufSize, int* nums, int numsSize, int pos, int** res, int* returnSize, int** returnColumnSizes){

    if(n <= 0 || bufSize >= k){

        if(n == 0 && bufSize == k){

            res[*returnSize] = (int*)malloc(sizeof(int) * bufSize);

            (*returnColumnSizes)[*returnSize] = bufSize;

            for(int j = 0; j < bufSize; j++){

                res[*returnSize][j] = buf[j];
            }

            (*returnSize)++;

        }

        return ;

    }
    for(int i = pos; i < numsSize; i++){

        if(n - nums[i] < 0){

            break;

        }

        buf[bufSize] = nums[i];

        _combinationSum3(n - nums[i], k, buf, bufSize + 1, nums, numsSize, i + 1, res, returnSize, returnColumnSizes);

    }

}


    int nums[] = {1, 2, 3, 4, 5, 6, 7, 8, 9}, buf[9];

    int **res = (int**)malloc(sizeof(int*) * 1024);

    *returnColumnSizes = (int*)malloc(sizeof(int) * 1024);

    *returnSize = 0;

    

    _combinationSum3(n, k, buf, 0, nums, 9, 0, res, returnSize, returnColumnSizes);

    

    return res;

}
```

