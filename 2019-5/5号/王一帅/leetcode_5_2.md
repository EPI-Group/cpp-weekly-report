## 删除链表的倒数第N个节点

给定一个链表，删除链表的倒数第 *n* 个节点，并且返回链表的头结点。

**示例：**

```
给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.
```

**说明：**

给定的 *n* 保证是有效的。

**进阶：**

你能尝试使用一趟扫描实现吗？

```c
/**

- Definition for singly-linked list.
- struct ListNode {
- int val;
- struct ListNode *next;
- };
  */


struct ListNode* removeNthFromEnd(struct ListNode* head, int n){
     if(n==0)
     {
        return head;
    }
    struct ListNode *fastp=NULL,*slowp=NULL,*p=NULL;
    for(fastp=head;n>0;fastp=fastp->next,n--);
    slowp=head;
    while(fastp)
    {
        p=slowp;
        slowp=slowp->next;
        fastp=fastp->next;
    }
    if(slowp==head)
    {
        head=head->next;
    }
    else
    {
          p->next=slowp->next;  
          free(slowp);
    }
    return head;
}
```

