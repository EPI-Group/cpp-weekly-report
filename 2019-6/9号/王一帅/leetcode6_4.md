## 平衡二叉树

给定一个二叉树，判断它是否是高度平衡的二叉树。

本题中，一棵高度平衡二叉树定义为：

一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。

示例 1:

给定二叉树 [3,9,20,null,null,15,7]

3

   / \
  9  20
    /  \
   15   7
返回 true 。

示例 2:

给定二叉树 [1,2,2,3,3,null,null,4,4]

   1
  / \
 2   2
/ \

   3   3
  / \
 4   4
返回 false 。



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

int depth(struct TreeNode *t){
    int l_depth = 0, r_depth = 0, diff;
    if(t == NULL) return 0;
    else{
        l_depth = depth(t -> left) + 1;
        r_depth = depth(t -> right) + 1;
    }
    int depth = l_depth > r_depth ? l_depth : r_depth;
    return depth;
}

bool isBalanced(struct TreeNode* root) {
    int l, r;
    if(root == NULL) return true;
    l = depth(root -> left);
    r = depth(root -> right);
    if(abs(l - r) > 1) return false;
    return isBalanced(root -> left) && isBalanced(root -> right);
}
```

