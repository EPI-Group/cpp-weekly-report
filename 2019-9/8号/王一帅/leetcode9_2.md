给定一个单链表，其中的元素按升序排序，将其转换为高度平衡的二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

示例:

给定的有序链表： [-10, -3, 0, 5, 9],

一个可能的答案是：[0, -3, 9, -10, null, 5], 它可以表示下面这个高度平衡二叉搜索树：

 	 0
	 / \

   -3   9
   /   /
 -10  5



```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */


struct ListNode* FindMiddle(struct ListNode* start, struct ListNode* end){
    struct ListNode* fast = start;
    struct ListNode* slow = start;
    while(slow != end && fast != end){
        if(fast->next == end)
            return slow;
        else if(fast->next != end && fast->next->next == end)
            return slow;
        else{
            fast = fast->next;
            fast = fast->next;
            slow = slow->next;
        }
    }
    return NULL;
}

struct Tree* ListToBST(struct ListNode* start, struct ListNode* end){
    if(start == NULL)
        return NULL;
    struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    struct ListNode* middle = FindMiddle(start, end);
    if(middle == NULL)
        return NULL;
    root->val = middle->val;
    root->left = ListToBST(start, middle);
    root->right = ListToBST(middle->next, end);
    return root;
}

struct TreeNode* sortedListToBST(struct ListNode* head) {
    struct TreeNode* root = (struct TreeNode*)malloc(sizeof(struct TreeNode));
    root = ListToBST(head, NULL);
    return root;
}


```

