给定两个大小为 m 和 n 的有序数组 `nums1` 和 `nums2`。

请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。

你可以假设 `nums1` 和 `nums2` 不会同时为空。

**示例 1:**

```
nums1 = [1, 3]
nums2 = [2]

则中位数是 2.0
```

**示例 2:**

```
nums1 = [1, 2]
nums2 = [3, 4]

则中位数是 (2 + 3)/2 = 2.5  
```



```c
double findMedianSortedArrays(int* nums1, int nums1Size, int* nums2, int nums2Size){
    int i,j;
    int n = nums1Size + nums2Size;
    int temp;
    int tempn;
    int *num3 = (int*)malloc(sizeof(int)*n);
    memset(num3,0,sizeof(num3));
    for (i=0;i < nums1Size;i++)
    {
        *(num3+i) = *(nums1+i);
    }
    for(j=0;j < nums2Size;j++)
    {
        *(num3+j+nums1Size) = *(nums2+j);
    }
    for(j = 0 ;j < n ;j ++)
    {
        for(i = j+1 ; i < n ;i++)
        {
            temp = *(num3+j);
            tempn = *(num3+i);
            if(temp > tempn)
            {
                *(num3+j) = tempn;
                *(num3+i) = temp;
            }
        }
    }
    int up = n/2;
    int test = n%2;
    double num = 0;
    if(test==0)
    {
        int down  = up -1;
        num = num3[up]+num3[down];
        num = num/2;
        free(num3);
        return num;
    }
    else
    {
        num = num3[up];
        free(num3);
        return num;
    }
   return 0;
}
```

