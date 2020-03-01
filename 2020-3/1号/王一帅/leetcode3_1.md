编写程序以查找两个单链表的交点开始的节点。

例如，以下两个链接列表：

[![img](https://assets.leetcode.com/uploads/2018/12/13/160_statement.png)](https://assets.leetcode.com/uploads/2018/12/13/160_statement.png)

 

**范例1：**

[![img](https://assets.leetcode.com/uploads/2018/12/13/160_example_1.png)](https://assets.leetcode.com/uploads/2018/12/13/160_example_1.png)

 

**范例2：**

[![img](https://assets.leetcode.com/uploads/2018/12/13/160_example_2.png)](https://assets.leetcode.com/uploads/2018/12/13/160_example_2.png)

 

**范例3：**

[![img](https://assets.leetcode.com/uploads/2018/12/13/160_example_3.png)](https://assets.leetcode.com/uploads/2018/12/13/160_example_3.png)



 * ```c
 /**

    - Definition for singly-linked list.
    
    - struct ListNode {
    
    - int val;
    
    - struct ListNode *next;
    
    - };
  */
   struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
   struct ListNode *ia, *ib;
 
   if(!headA || !headB) return(NULL);
 
   for( ia = headA; ia; ia = ia->next)
       for( ib = headB; ib; ib = ib->next)
           if(ia == ib) return(ia);
 
   return(NULL);
   }
 ```
 
 

