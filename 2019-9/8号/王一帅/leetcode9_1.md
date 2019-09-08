将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

示例:

给定有序数组: [-10,-3,0,5,9],

一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：

 	 0
 	/ \

   -3   9
   /   /
 -10  5



```c
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */


struct TreeNode* generateBST(int *nums,int left,int right){
    if(left>right) return NULL;
    int mid = (left+right)/2;
    struct TreeNode* p;
    p = (struct TreeNode*) malloc(sizeof(struct TreeNode));
    p->val = nums[mid];
    p->left = generateBST(nums,left,mid-1);
    p->right = generateBST(nums,mid+1,right);
    return p;
}

struct TreeNode* sortedArrayToBST(int* nums, int numsSize){
    struct TreeNode * t = generateBST(nums,0,numsSize-1);
    return t;
}
```

