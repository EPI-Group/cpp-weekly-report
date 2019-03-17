#1 .两个总和
给定一个整数数组，返回两个数字的索引，使它们相加到特定目标。
您可以假设每个输入只有一个解决方案，并且您可能不会两次使用相同的元素。

例：

鉴于NUMS = [2，7，11，15]，目标= 9，

因为NUMS [ 0 ] + NUMS [ 1 ] = 2 + 7 = 9，
返回[ 0，1 ].

代码实现：

    int* twoSum(int* nums, int numsSize, int target) {
	int i = 0, j = 0;  
    int* result = NULL;  
    result = (int*)malloc(sizeof(int) * 2);  
    for(i = 0; i < numsSize; i++) {  
        for(j = i + 1; j < numsSize; j++) {  
            if(target == nums[i] + nums[j]) {  
                result[0] = i;  
                result[1] = j;  
                return result;  
            }  
        }  
    }  
    return result;
    }