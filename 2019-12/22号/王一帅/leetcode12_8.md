给定两个数组，编写一个函数来计算它们的交集。

示例 1:

输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2]
示例 2:

输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [9,4]
说明:

输出结果中的每个元素一定是唯一的。
我们可以不考虑输出结果的顺序。



```c
/**

 \* Note: The returned array must be malloced, assume caller calls free().

 */

int* intersection(int* a, int s1, int* b, int s2, int* returnSize){

​    int map1[1000],map2[1000];

​    for(int i=0;i<1000;i++){

​        map1[i]=0;

​        map2[i]=0;

​    }

​    for(int i=0;i<s1;i++){

​        map1[a[i]]++;

​    }

​    for(int i=0;i<s2;i++){

​        map2[b[i]]++;

​    }

​    int *res,k=0;

​    res=(int *)malloc(sizeof(int)*1000);

​    for(int i=0;i<1000;i++){

​        if(map1[i]!=0&&map2[i]!=0) res[k++]=i;

​    }

​    *returnSize=k;

​    return res;

}
```

