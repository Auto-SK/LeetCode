# 二叉树的四种遍历

对于一个给定的二叉树，有四种遍历方式：先序遍历、中序遍历、后序遍历、层次遍历。

<img src="https://sunkai-markdown-pics.oss-cn-shanghai.aliyuncs.com/imgs/20200716221208.png" alt="img" style="zoom:50%;" />

* 前序遍历：根节点 -> 左孩子 -> 右孩子，遍历结果为 `1 2 4 5 3 6 7`；
* 中序遍历：左孩子 -> 根节点 -> 右孩子，遍历结果为 `4 2 5 1 6 3 7`；
* 后序遍历：左孩子 -> 右孩子 -> 根节点，遍历结果为 `4 5 2 6 7 3 1`；
* 层序遍历：按照每一层从左向右的方式进行遍历，遍历结果为 `1 2 3 4 5 6 7`。

## 1 前序遍历

### 复杂度分析

* 时间复杂度：O(n)，n 为节点数，访问每个节点恰好一次。

* 空间复杂度：O(h)，h 为树的高度。最坏情况下需要空间 O(n)，平均情况为 O(logn)。

```python
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def dfs(root):
            nonlocal res  # 为了让上一级的 res 能在这个函数用
            if not root:
                return
            res.append(root.val)  # 先将根节点的值加入结果
            dfs(self.left)  # 左子树
            dfs(self.right)  # 右子树
		dfs(root)
        return res
```

## 2 中序遍历

### 复杂度分析

* 时间复杂度：O(n)，n 为节点数，访问每个节点恰好一次。

* 空间复杂度：O(h)，h 为树的高度。最坏情况下需要空间 O(n)，平均情况为 O(logn)。

```python
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def dfs(root):
            nonlocal res
            dfs(root.left)  # 左子树
            res.append(root.val)  # 将根节点加入结果
            dfs(root.right)  # 右子树
		dfs(root)
        return res
```

## 3 后序遍历

### 复杂度分析

* 时间复杂度：O(n)，n 为节点数，访问每个节点恰好一次。

* 空间复杂度：O(h)，h 为树的高度。最坏情况下需要空间 O(n)，平均情况为 O(logn)。

```python
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        res = []
        def dfs(root):
            nonlocal res
            dfs(root.left)  # 左子树
            dfs(root.right)  # 右子树
            res.append(root.val)  # 将根节点加入结果
		dfs(root)
        return res
```

## 4 层序遍历

### 复杂度分析

* 时间复杂度：O(n)，n 为节点数，访问每个节点恰好一次。

* 空间复杂度：O(h)，h 为树的高度。最坏情况下需要空间 O(n)，平均情况为 O(logn)。

```python
class Solution:
    def levelorderTraversal(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        res, q = [], [root]
        while q:
            n = len(q)
            level = []
            for i in range(n):
                node = q.pop(0)  # 这里的 q 相当于一个队列
                level.append(node.val)
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
			res.append(level)
		return res
```

