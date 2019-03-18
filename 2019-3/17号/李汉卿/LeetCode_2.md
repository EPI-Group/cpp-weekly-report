#####k-Group中的反向节点 给定链表，一次反转链表k的节点并返回其修改后的列表。k是正整数，并且小于或等于链表的长度。如果节点数不是k的倍数，那么最后的剩余节点应该保持不变。

***例***：

鉴于此链接列表： 1->2->3->4->5

对于k = 2，您应该返回：2->1->4->3->5

对于k = 3，您应该返回：3->2->1->4->5

**注意**：

只允许恒定的额外内存。 您不能更改列表节点中的值，只能更改节点本身。

***代码实现：***

```
ListNode* reverseKGroup(ListNode* head, int k) {
        if (!head || k == 1) return head;
        ListNode *dummy = new ListNode(-1);
        ListNode *pre = dummy;
        ListNode *cur = head;
        dummy->next = head;
        
        for (int i = 1; cur; ++i) {
            if (i % k == 0) {
                pre = reverseOneGroup(pre, cur->next);
                cur = pre->next;
            } else {
                cur = cur->next;
            }
        }
        return dummy->next;
    }
    ListNode* reverseOneGroup(ListNode* pre, ListNode* next) {
        ListNode *last = pre->next, *cur = last->next;
        while(cur != next) {
            last->next = cur->next;
            cur->next = pre->next;
            pre->next = cur;
            cur = last->next;
        }
        return last;
    }
```

