给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

说明: 叶子节点是指没有子节点的节点。

示例:
给定如下二叉树，以及目标和 sum = 22，

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
返回:

[
   [5,4,11,2],
   [5,8,4,5]
]



 * ```c
 /**

    - Definition for a binary tree node.
    - struct TreeNode {
    - int val;
    - struct TreeNode *left;
    - struct TreeNode *right;
    - };
      */
    
    /**
    
    - Return an array of arrays of size *returnSize.
    - The sizes of the arrays are returned as *returnColumnSizes array.
    - Note: Both returned array and *columnSizes array must be malloced, assume caller calls free().
      */
      int** pathSum(struct TreeNode* root, int sum, int* returnSize, int** returnColumnSizes){
      *returnSize = 0;
      if(root==NULL)  return 0;
      struct TreeNode* stack[1000];int top = -1;
      *returnColumnSizes = (int*)malloc(sizeof(int)*20);
      int** result = (int**)malloc(sizeof(int*)*20);
      result[0] = (int*)malloc(sizeof(int)*20);
      int i = 0,j = 0,n = 0,temp = sum;
      stack[++top] = root;
      struct TreeNode* p = root;
      while(top!=-1)
      {
          root = stack[top--];
          if(root->right!=NULL)
              stack[++top] = root->right;
          if(root->left!=NULL)
              stack[++top] = root->left;
          if(temp>0)
          {
              result[i][j] = root->val;
              temp -= root->val;
              ++j;
              ++n;   
          }
          if(temp==0&&root->right==NULL&&root->left==NULL)
          {
          (*returnColumnSizes)[i] = j;
           ++i;
           j = 0;
           result[i] = (int*)malloc(sizeof(int)*20);
           root = stack[top--];
       }
       else if(temp<=0)
       {
           temp += root->val;
           --j;
           --n;
       }
   }
   *returnSize = n;
   return result;
   }
 ```
 
 

