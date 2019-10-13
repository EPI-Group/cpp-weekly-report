给定一个二叉树，返回它的 后序 遍历。

示例:

输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [3,2,1]



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

/**

- Note: The returned array must be malloced, assume caller calls free().
  */
  typedef struct StackNode {
  struct TreeNode *treePtr;
  struct StackNode *next;
  }StackNode;
  typedef struct {
  StackNode *top;
  int length;
  }StackHead;

void pushNode(StackHead *stack,struct TreeNode *treeNode) {
    if(!treeNode)
        return;
    StackNode *addNode=(StackNode *)malloc(sizeof(StackNode));
    addNode->treePtr=treeNode;
    if(stack->length) {
        addNode->next=stack->top;
        stack->top=addNode;
    }
    else {
        addNode->next=NULL;
        stack->top=addNode;
    }
    stack->length++;
    return;
}

struct TreeNode *popNode(StackHead *stack) {
    StackNode *deleteNode=stack->top;
    struct TreeNode *temp=deleteNode->treePtr;
    stack->top=deleteNode->next;
    stack->length--;
    free(deleteNode);
    return temp;
}

void swap(int *a,int *b) {
    int temp=*a;
    *a=*b;
    *b=temp;
    return;
}

int* postorderTraversal(struct TreeNode* root, int* returnSize){
    if(!root) {
        *returnSize=0;
        return NULL;
    }
    StackHead *stack1;
    int *arrBack=(int *)malloc(sizeof(int)*100),index=0;
    stack1=(StackHead *)malloc(sizeof(StackHead));
    stack1->length=0;
    stack1->top=NULL;
    pushNode(stack1,root);
    while(stack1->length) {
        struct TreeNode *temp=popNode(stack1);
        pushNode(stack1,temp->left);
        pushNode(stack1,temp->right);
        arrBack[index]=temp->val;
        index++;
        free(temp);
    }
    for(int i=0;i<(index/2);i++)
        swap(&arrBack[i],&arrBack[index-i-1]);
    *returnSize=index;
    return arrBack;
}
```

