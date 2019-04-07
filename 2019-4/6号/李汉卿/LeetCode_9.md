##### 给定二叉树，检查它是否是自身的镜像（即，围绕其中心对称）。

例如，这个二叉树`[1,2,2,3,4,4,3]`是对称的：

```
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

但以下`[1,2,2,null,3,null,3]` 不是：

```
   1
   / \
  2   2
   \   \
   3    3
```



***代码实现：***

```c
boolean isSymmetric(TreeNode *root) {
        if(root == null){
            return true;
        }
        
        return dfs(root.left,root.right);
    }
    
    private boolean dfs(TreeNode *left, TreeNode *right){
        if(left == null && right == null){
            return true;
        }
        
        if(left == null || right == null){
            return false;
        }
        
        if(left.val == right.val){
            return dfs(left.left,right.right) && dfs(left.right,right.left);
        }else{
            return false;
        }
```

