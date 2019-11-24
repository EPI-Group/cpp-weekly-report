删除链表中等于给定值 **val** 的所有节点。

**示例:**

```
输入: 1->2->6->3->4->5->6, val = 6
输出: 1->2->3->4->5
```



```c
struct ListNode* removeElements(struct ListNode* head, int val){
    // 如果头结点满足条件,则需要删除
    while (head != NULL && head->val == val) {
        head = head->next;
    }
    
    // 如果头结点不满足条件,则从第二个结点开始删除
    struct ListNode *current = head;
    while (current != NULL) {
        struct ListNode *pNext = current->next;
        if (pNext != NULL && pNext->val == val) {
            current->next = pNext->next;
            free(pNext);
        } else {
            current = current->next;
        }
    }
    return head;
}
```