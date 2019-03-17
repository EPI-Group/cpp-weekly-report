#25 。k-Group中的反向节点
给定链表，一次反转链表k的节点并返回其修改后的列表。  
k是正整数，并且小于或等于链表的长度。如果节点数不是k的倍数，那么最后的剩余节点应该保持不变。

例：

鉴于此链接列表： 1->2->3->4->5

对于k = 2，您应该返回：2->1->4->3->5

对于k = 3，您应该返回：3->2->1->4->5

注意：

只允许恒定的额外内存。
您不能更改列表节点中的值，只能更改节点本身。

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
    
    struct ListNode* reverseKGroup(struct ListNode* head, int k) {
    if(head==NULL || head->next==NULL ||k<2) 
	return head;
    struct ListNode *dummy=(struct ListNode *)malloc(sizeof(struct ListNode));
    dummy->next=head;
    
    struct ListNode *tail=dummy;
    struct ListNode *pre=dummy;
    struct ListNode *temp=NULL;
    int count ;
    
    while(1)
    {
        count = k;
        while(count>0 && tail != NULL)
        {
            count--;
            tail=tail->next;
        }
        
        if(tail == NULL ) break;
        
        head=pre->next;
        
        while(pre->next != tail)
        {
            temp=pre->next;
            pre->next=temp->next;
            temp->next=tail->next;
            tail->next=temp;
        }
        tail=head;
        pre=head;
    }
    return dummy->next;
}