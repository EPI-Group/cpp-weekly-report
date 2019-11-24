给出一个完全二叉树，求出该树的节点个数。

说明：

完全二叉树的定义如下：在完全二叉树中，除了最底层节点可能没填满外，其余每层节点数都达到最大值，并且最下面一层的节点都集中在该层最左边的若干位置。若最底层为第 h 层，则该层包含 1~ 2h 个节点。

示例:

输入: 
    1
   / \
  2   3
 / \  /
4  5 6

输出: 6





```c
/**

 \* Definition for a binary tree node.

 \* struct TreeNode {

 \*     int val;

 \*     struct TreeNode *left;

 \*     struct TreeNode *right;

 \* };

 */



int getHeight(struct TreeNode* root){

    int height = 0;

    while(root){

        height++;

        root = root->left;

    }

    

    return height;

}



int countNodes(struct TreeNode* root){

    if(!root){

        return 0;

    }

    

    int count = 0, left = getHeight(root->left), right;

    while(root){

        right = getHeight(root->right);

        if(left == right){

            count += 1 << left;

            root = root->right;

            left = right - 1;

        }else{

            count += 1 << right;

            root = root->left;

            left = left - 1;

        }

    }

    

    return count;

}
```

