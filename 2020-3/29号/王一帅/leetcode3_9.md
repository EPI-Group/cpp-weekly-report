在上次打劫完一条街道之后和一圈房屋后，小偷又发现了一个新的可行窃的地区。这个地区只有一个入口，我们称之为“根”。 除了“根”之外，每栋房子有且只有一个“父“房子与之相连。一番侦察之后，聪明的小偷意识到“这个地方的所有房屋的排列类似于一棵二叉树”。 如果两个直接相连的房子在同一天晚上被打劫，房屋将自动报警。

计算在不触动警报的情况下，小偷一晚能够盗取的最高金额。

示例 1:

输入: [3,2,3,null,3,null,1]

 3
/ \

   2   3
    \   \ 
     3   1

输出: 7 
解释: 小偷一晚能够盗取的最高金额 = 3 + 3 + 1 = 7.
示例 2:

输入: [3,4,5,1,3,null,1]

 3
/ \

   4   5
  / \   \ 
 1   3   1

输出: 9
解释: 小偷一晚能够盗取的最高金额 = 4 + 5 = 9.



```c
/**

 \* Definition for a binary tree node.

 \* struct TreeNode {

 \*     int val;

 \*     struct TreeNode *left;

 \*     struct TreeNode *right;

 \* };

 */

#define MAX(a, b) ((a) > (b) ? (a) : (b))
int GetMaxMoney(struct TreeNode* currNode, bool status)
{
    if (currNode == NULL) {
        return 0;
    }
    
    int tmpTrueLeft = 0;
    int tmpFalseLeft = 0;
    int tmpTrueRight = 0;
    int tmpFalseRight = 0;

    tmpFalseLeft = GetMaxMoney(currNode->left, false);      //不加当前节点
    tmpFalseRight = GetMaxMoney(currNode->right, false);    //不加当前节点
    tmpTrueLeft = GetMaxMoney(currNode->left, true);        //加当前节点
    tmpTrueRight = GetMaxMoney(currNode->right, true);      //加当前节点

    if (status == true) {
        // 1、父节点为true
        return (tmpFalseLeft + tmpFalseRight);
    } else {
        return MAX((tmpTrueLeft + tmpTrueRight + currNode->val), (tmpFalseLeft + tmpFalseRight));
    }
}

int rob(struct TreeNode* root){
    return MAX(GetMaxMoney(root, false), GetMaxMoney(root, true));
}
```

