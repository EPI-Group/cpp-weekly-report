给定一个二叉树，原地将它展开为链表。

例如，给定二叉树

   1

   / \
  2   5
 / \   \
3   4   6
将其展开为：

1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6



```c
/**

- Definition for a binary tree node.
- struct TreeNode {
- int val;
- struct TreeNode *left;
- struct TreeNode *right;
- };
  */

typedef struct TreeNode Node;

void print(Node *node){
    while(node){
        printf("%d->", node->val);
        node = node->right;
    }
    printf("\n");
}
void get(Node *node, Node **rear, Node *head) {
    Node *tmp;
    if(!node) return;
    tmp = (Node *)malloc(sizeof(Node));
    tmp->val = node->val;
    tmp->left = NULL;
    tmp->right = NULL;
    (*rear)->right = tmp;
    (*rear) = (*rear)->right;
    (*rear)->right = NULL;
    get(node->left, rear, head);
    get(node->right, rear, head);
}
void flatten(struct TreeNode* root){
    Node node;
    node.right = NULL;
    node.left = NULL;
    Node *rear = &node;
    get(root, &rear, &node);
    if(!root) return NULL;
    root->val = node.right->val;
    root->left = NULL;
    root->right = node.right->right;
}
```

