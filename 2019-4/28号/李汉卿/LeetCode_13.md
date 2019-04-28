给定二叉树，找到它的最小深度。最小深度是沿从根节点到最近的叶节点的最短路径上的节点数。

**注意：**  叶子是没有子节点的节点。

**例：**给定二叉树`[3,9,20,null,null,15,7]`，

​    3
   / \
  9  20
​      /  \
   15   7

返回其最小深度= 2。

实现代码：

```c++
int minDepth(TreeNode*root) {
        if (root == null) return 0;
        else {
            int ld = minDepth(root.left);
            int rd = minDepth(root.right);
            if (ld == 0)
                return rd + 1;
            else if (rd == 0) 
                return ld + 1;
            else 
                return Math.min(ld, rd) + 1;
        }
    }
```

