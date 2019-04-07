21 。合并两个排序列表  
合并两个已排序的链接列表并将其作为新列表返回。新列表应该通过拼接前两个列表的节点来完成。

例：

输入： 1-> 2-> 4,1-> 3-> 4  
输出： 1-> 1-> 2-> 3-> 4-> 4  

	/**
 	* Definition for singly-linked list.
 	* struct ListNode {
 	*     int val;
 	*     struct ListNode *next;
 	* };
 	*/

	struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2) {
    	struct ListNode* temp;
    	struct ListNode* result;
    	if(l1==NULL)
        	return l2;
    	if (l2==NULL)
        	return l1;
    	if (l1->val<=l2->val) 
    	{
        	temp=l1;
        	l1=l1->next;
    	}   
    	else 
    	{
        	temp=l2;
        	l2=l2->next;
    	}
    	result=temp;
    	while(l1 && l2) 
    	{
        	if (l1->val<=l2->val) 
        	{
            	temp->next=l1;
            	l1=l1->next;
        	}
        	else {
            	temp->next=l2;
            	l2=l2->next;
        	}  
        	temp=temp->next;
    	}
    	if(l1)
    	{
        	temp->next=l1;
    	}
    	else if(l2)
    	{
        	temp->next=l2;
    	}
    	return result;
	}