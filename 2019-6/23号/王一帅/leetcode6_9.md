根据一棵树的前序遍历与中序遍历构造二叉树。

注意:
你可以假设树中没有重复的元素。

例如，给出

前序遍历 preorder = [3,9,20,15,7]
中序遍历 inorder = [9,3,15,20,7]
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

struct TreeNode* buildTree(int* preorder, int preorderSize, int* inorder, int inorderSize){
if(preorderSize==0)
		return NULL;
    struct TreeNode* root=(struct TreeNode*) malloc(sizeof(struct TreeNode));
    root->val=preorder[0];
    int i=0;
    for(;inorder[i]!=preorder[0];i++);
    if(i)
         root->left=buildTree(preorder+1, i, inorder, i);
    else 
        root->left=NULL;
    if(i!=inorderSize-1)
        root->right=buildTree(preorder+i+1, preorderSize-i-1, inorder+i+1, inorderSize-i-1);
    else 
        root->right=NULL;
    return root;
}
```

