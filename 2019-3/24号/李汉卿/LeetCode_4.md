##### 给定一个整数数组，返回两个数字的索引，使它们相加到特定目标。

##### 您可以假设每个输入只有一个解决方案，并且您可能不会两次使用相同的元素。

***例：***

给定nums = [2,7,11,15], target = 9,

因为nums [ 0 ] + [ 1 ] = 2 + 7 = 9,

返回[ 0,1 ]。

***代码实现：***

```c
int *twoSum(int *nums, int numsSize, int target){`

​       `int *res = (int *) malloc(2 * sizeof(int));`

​       `for (int i = 0; i < numsSize; i++){`

​            `for (int j = i + 1; j < numsSize; j++){`

​                 `if (nums[i] + nums[j] == target){`

​                        `res[0] = i;`

​                        `res[1] = j;`

​                        `return res;`

​                    `}`

​                `}`

​             `}`

​             `return res;`

`}`
```

