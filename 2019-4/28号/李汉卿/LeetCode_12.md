给定二叉树，找到它的最大深度。最大深度是从根节点到最远叶节点的最长路径上的节点数。

**注意：**  叶子是没有子节点的节点。

**例：**给定二叉树`[3,9,20,null,null,15,7]`，

​    3
   / \
  9  20
​      /  \
   15   7

返回其深度= 3。

实现代码：

```c++
int maxDepth(TreeNode* root) {
        int maxDepth = 0;
        preorderTraverse(root, 0, maxDepth);
        return maxDepth;
    }
```

