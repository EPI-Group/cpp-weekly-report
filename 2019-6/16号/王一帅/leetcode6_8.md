## 二叉树的层序遍历

给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。

例如:
给定二叉树: [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回其层次遍历结果：

[
  [3],
  [9,20],
  [15,7]
]



```c
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
  #define LEV 1024
  #define LEN 1024
  typedef struct  TreeNode  Node;
  void get(Node *node, int level, int **ret, int *ret_index, int *rcs)
  {
  if(!node) return;
  if(!ret[level])
  {
      ret[level] = (int *)malloc(sizeof(int) * LEN);
      rcs[level] = 0;
  }
  if(level > *ret_index)
  {
      *ret_index = level;
  }
   ret[level][rcs[level]++] = node->val; 
   get(node->left, level+1, ret, ret_index, rcs);
   get(node->right, level+1, ret, ret_index, rcs);

}
int** levelOrder(struct TreeNode* root, int* returnSize, int** returnColumnSizes){
    int **ret = (int **)malloc(sizeof(int*) * LEV);
    int *rcs = (int*)malloc(sizeof(int) * LEV);
    int ret_index = 0;
    memset(ret, 0, sizeof(int*) * LEV);
    memset(rcs, 0, sizeof(int) * LEV);
    get(root, 0, ret, &ret_index, rcs);
    *returnSize = root==NULL ? 0 : ret_index+1;
    *returnColumnSizes = rcs;
    return ret;
}
```

