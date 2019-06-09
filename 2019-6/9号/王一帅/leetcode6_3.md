## 对称二叉树

给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

​    1

   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

​    1

   / \
  2   2
   \   \
   3    3



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

bool com(struct TreeNode* a,struct TreeNode* b);
bool isSymmetric(struct TreeNode* root) {
    if(root == NULL)
        return true;
    return com(root->left,root->right);
    
}
bool com(struct TreeNode* a,struct TreeNode* b)
{
    if(a == NULL&&b == NULL)
        return true;
    else
    {
        if(a == NULL||b == NULL)
            return false;
        else if(a -> val==b -> val)
            return com(a->left,b->right)&&com(a->right,b->left);
        else
            return false;
    }      
}


```

