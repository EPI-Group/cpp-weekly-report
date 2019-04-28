给定二叉树，确定它是否是高度平衡的。对于此问题，高度平衡的二叉树定义为：二叉树，其中*每个*节点的两个子树的深度从不相差超过1。

**例1：**鉴于以下树`[3,9,20,null,null,15,7]`：

​    3
   / \
  9  20
​    /  \
   15   7

返回ture。

**例2：**鉴于以下树`[1,2,2,3,3,null,null,4,4]`：

​       1
​      / \
​     2   2
​    / \
   3   3
  / \
 4   4

返回false。

实现代码：

```c++
  public boolean isBalanced(TreeNode root) {
        return getDepth(root)!=-1;
    }
    private int  getDepth(TreeNode root){
        if(root==null){
            return 0;
        }
        int left=getDepth(root.left);
        int right=getDepth(root.right);
        if(Math.abs(left-right)>1||left==-1||right==-1){
            return -1;
        }
        return Math.max(left,right)+1;
    }
```

