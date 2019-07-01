给定一个二叉树，找出其最小深度。

最小深度是从根节点到最近叶子节点的最短路径上的节点数量。

说明: 叶子节点是指没有子节点的节点。

示例:

给定二叉树 [3,9,20,null,null,15,7],

    3
   / \
  9  20
    /  \
   15   7
返回它的最小深度  2.



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

typedef struct TreeNode Node;
void get(Node *node, int level, int *min){
    if(!node) return;
    if(!node->left && !node->right && (level < *min)) 
        *min = level;
    get(node->left, level+1, min);
    get(node->right, level+1, min);
    
}
int minDepth(struct TreeNode* root){
    int min = INT_MAX;
    get(root, 1, &min);
    return min == INT_MAX ? 0 : min;
}
```

