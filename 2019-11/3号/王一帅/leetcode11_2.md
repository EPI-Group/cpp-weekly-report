给定一个整数数组 nums，其中恰好有两个元素只出现一次，其余所有元素均出现两次。 找出只出现一次的那两个元素。

示例 :

输入: [1,2,1,3,2,5]
输出: [3,5]
注意：

结果输出的顺序并不重要，对于上面的例子， [5, 3] 也是正确答案。
你的算法应该具有线性时间复杂度。你能否仅使用常数空间复杂度来实现？



 *  * ```c
   /**
  
  - Note: The returned array must be malloced, assume caller calls free().
        */
        int* singleNumber(int* nums, int numsSize, int* returnSize)
        {
        int i=0;
        int pos=0;
        int ret=0;
        int *arr=malloc(2*sizeof(int));
        arr[0]=0;
        arr[1]=0;
        if(arr==NULL)
        {
            return NULL;
        }
        for(i=0;i<numsSize;++i)
        {
            ret=ret^nums[i];
        }
        for(i=0;i<32;++i)
        {
            if(((ret>>i)&1)==1)
            {
                pos=i;
                break;
            }
        }
        for(i=0;i<numsSize;++i)
        {
            if(((nums[i]>>pos)&1)==1)
            {
                arr[0]=arr[0]^nums[i];
            }
            if(((nums[i]>>pos)&1)==0)
            {
                arr[1]=arr[1]^nums[i];
            }
    }
       *returnSize=2;
       return arr;
       }
   ```
 
   