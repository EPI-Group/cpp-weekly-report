根据一棵树的中序遍历与后序遍历构造二叉树。

注意:
你可以假设树中没有重复的元素。

例如，给出

中序遍历 inorder = [9,3,15,20,7]
后序遍历 postorder = [9,15,7,20,3]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

struct TreeNode* buildTree(int* inorder, int inorderSize, int* postorder, int postorderSize){
if(inorderSize==0)
        return NULL;
    struct TreeNode* root=(struct TreeNode*) malloc(sizeof(struct TreeNode));
    root->val=postorder[postorderSize-1];
    int i=0;
    for(;inorder[i]!=postorder[postorderSize-1];i++);
    if(i)
         root->left=buildTree(inorder, i, postorder, i);
    else 
        root->left=NULL;
    if(i!=inorderSize-1)
        root->right=buildTree(inorder+i+1, inorderSize-i-1,postorder+i, postorderSize-i-1);
    else 
        root->right=NULL;
    return root;
}
```

