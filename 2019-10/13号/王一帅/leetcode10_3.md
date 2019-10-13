给定一棵二叉树，你需要计算它的直径长度。一棵二叉树的直径长度是任意两个结点路径长度中的最大值。这条路径可能穿过根结点。

示例 :
给定二叉树

          1
         / \
        2   3
       / \     
      4   5    
返回 3, 它的长度是路径 [4,2,1,3] 或者 [5,2,1,3]。

注意：两结点之间的路径长度是以它们之间边的数目表示。



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

int height(struct TreeNode* root){
    if(root == NULL) return 0;
    int left = height(root->left);
    int right = height(root->right);
    return left > right ? left+1:right+1;
}

int diameterOfBinaryTree(struct TreeNode* root){
    if(root == NULL) return 0;
    int d = height(root->left)+height(root->right);
    int left = diameterOfBinaryTree(root->left);
    int right = diameterOfBinaryTree(root->right);
    int max = left > right ? left:right;
    if(d > max) max = d;
    return max;
}
```

