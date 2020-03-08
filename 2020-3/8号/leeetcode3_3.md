给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

示例:

给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：

​       0
​      / \

   -3   9
   /   /
 -10  5

```c
/**

- Definition for singly-linked list.
- struct ListNode {
- int val;
- struct ListNode *next;
- };
  */
  /**
- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

struct TreeNode* sortedListToBST(struct ListNode* head){
	if(!head){
		return NULL;
	}
	struct ListNode *pre = head, *slow = head, *fast = head;
	

while(fast->next && fast->next->next){
	fast = fast->next->next;
	pre = slow;
	slow = slow->next;
}

struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
root->val = slow->val;

if(pre == slow){
	root->left = NULL;
}else{
	pre->next = NULL;
	root->left = sortedListToBST(head);
	pre->next = slow;
}

root->right = sortedListToBST(slow->next);
return root;

}
```

