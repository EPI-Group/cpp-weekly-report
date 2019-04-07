#####给定两个二叉树，编写一个函数来检查它们是否相同。

##### 如果两个二叉树在结构上相同并且节点具有相同的值，则认为它们是相同的。

***例一：***

```
输入：      1 1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

输出： true
```

***例二：***

```
输入：      1 1
          /           \
         2             2

        [1,2]，[1，null，2]

输出： false
```

***例三：***

```
输入：      1 1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

输出： false
```

***代码实现：***

```c
boolean isSameTree(TreeNode*p, TreeNode*q) {

        if (p == null && q == null) {
            return true;
        } 
        if (p == null || q == null) {
            return false;
        }
        
        if (p.val == q.val) {
               return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
         }
        
        return false;
    }
```

