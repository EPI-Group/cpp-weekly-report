2 。添加两个数字  
您将获得两个非空链表，表示两个非负整数。数字以相反的顺序存储，每个节点包含一个数字。添加两个数字并将其作为链接列表返回。  

您可以假设这两个数字不包含任何前导零，除了数字0本身。  

例：  

输入：（2  - > 4  - > 3）+（5  - > 6  - > 4）  
 输出： 7  - > 0  - > 8  
 说明： 342 + 465 = 807。  

	/**
 	 * Definition for singly-linked list.
 	 * struct ListNode {
	 *     int val;
	 *     struct ListNode *next;
	 * };
	 */
	struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    	struct ListNode *p1=l1;
    	struct ListNode *p2=l2;
    	struct ListNode *result=(struct ListNode *)malloc(sizeof(struct ListNode));
    	result->val=0;
    	struct ListNode *p=NULL;
    	int c=0;
    	while (p1!=NULL || p2!=NULL || c!=0)
    	{
        	if(p == NULL)
        	{
            	p=result;
        	}
        	else
        	{
            	p->next=(struct ListNode*)malloc(sizeof(struct ListNode)); 
            	p->next->val=0;
            	p=p->next;
        	}
        	int a=(p1==NULL ? 0:p1->val);
        	int b=(p2==NULL ? 0:p2->val);
        	int s=(a+b+c)%10;
        	c=(a+b+c)/10;
        	p->val=s;     
        	p->next=NULL;
        	p1=(p1==NULL ? NULL : p1->next);
        	p2=(p2==NULL ? NULL : p2->next);
 
    	}
    	return result;
	}