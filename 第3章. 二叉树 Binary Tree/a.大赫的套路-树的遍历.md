# 树的遍历

## 1. 递归法·模板框架

```java
/* 二叉树遍历框架 */
public void traverse(TreeNode root) {
    // 前序遍历
    traverse(root.left)
    // 中序遍历
    traverse(root.right)
    // 后序遍历
}
```

何时使用**前中后**序遍历？

* 根据题意，思考一个**二叉树节点需要做什么**，到底用什么遍历顺序就清楚了

## 2. 迭代法·模板框架

使用stack控制TreeNode节点

* 根：`res.add(node.val)`  
* 左：`node = node.left`
* 右：`node = node.right`
* 控制出栈入栈：
  * `stack.push(node.val)`
  * `stack.pop()`

整体代码逻辑

```java
//省略号(...)为“根”可能出现的位置
while(!stack.isEmpty() || node != null){
    if(node != null){
        //根：根据遍历顺序调整
        res.add(node.val)
        ...
        stack.push(node.val);
        //左子树
        node = node.left;
    }
    else{
    	stack.pop();
        ...
        //右子树
        node = node.right;
    }
}
```

[前序遍历套路](3.1二叉树的基础算法/01.二叉树的前序遍历.md)

[中序遍历套路](3.1二叉树的基础算法/02.二叉树的中序遍历.md)

[后序遍历套路](3.1二叉树的基础算法/03.二叉树的后序遍历.md)

## 3. BFS层序遍历·模板框架

```java
void traverse(TreeNode root) {
    if (root == null) return;
    // 初始化队列，将 root 加入队列
    Queue<TreeNode> q = new LinkedList<>();
    q.offer(root);

    while (!q.isEmpty()) {
        TreeNode cur = q.poll();

        /* 层级遍历代码位置 */
        System.out.println(root.val);
        /*****************/

        if (cur.left != null) {
            q.offer(cur.left);
        }

        if (cur.right != null) {
            q.offer(cur.right);
        }
    }
}
```
