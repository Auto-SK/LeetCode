# 二叉树的四种遍历

对于一个给定的二叉树，有四种遍历方式：先序遍历、中序遍历、后序遍历、层次遍历。

<img src="https://sunkai-markdown-pics.oss-cn-shanghai.aliyuncs.com/imgs/20200716221208.png" alt="img" style="zoom:50%;" />

* 前序遍历：根节点 -> 左孩子 -> 右孩子，遍历结果为 `1 2 4 5 3 6 7`；
* 中序遍历：左孩子 -> 根节点 -> 右孩子，遍历结果为 `4 2 5 1 6 3 7`；
* 后序遍历：左孩子 -> 右孩子 -> 根节点，遍历结果为 `4 5 2 6 7 3 1`；
* 层序遍历：按照每一层从左向右的方式进行遍历，遍历结果为 `1 2 3 4 5 6 7`。

## 一、递归解法

时间复杂度：O(n)，n为节点数，访问每个节点恰好一次。

空间复杂度：空间复杂度：O(h)，h为树的高度。最坏情况下需要空间O(n)，平均情况为O(logn)。

1. 前序遍历

```python
# 递归1：二叉树遍历最易理解和实现版本
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        return [root.val] + self.preorderTraversal(root.left) + self.preorderTraversal(root.right)
    
# 递归2：通用模板，可以适应不同的题目，添加参数、增加返回条件、修改进入递归条件、自定义返回值
class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        def dfs(cur):
            if not cur:
                return
            # 前序递归
            res.append(cur.val)
            dfs(cur.left)
            dfs(cur.right)
        res = []
        dfs(root)
        return res
```

2. 中序遍历

```python
# 递归1：二叉树遍历最易理解和实现版本
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        
        return self.inorderTraversal(root.left) + [root.val] + self.inorderTraversal(root.right)
    
# 递归2：通用模板，可以适应不同的题目，添加参数、增加返回条件、修改进入递归条件、自定义返回值
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        def dfs(cur):
            if not cur:
                return
            # 中序递归
            dfs(cur.left)
            res.append(cur.val)
            dfs(cur.right)
        res = []
        dfs(root)
        return res
```


3. 后序遍历

```python
# 递归1：二叉树遍历最易理解和实现版本
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []
        return self.postorderTraversal(root.left) + self.postorderTraversal(root.right) + [root.val]
    
# 递归2：通用模板，可以适应不同的题目，添加参数、增加返回条件、修改进入递归条件、自定义返回值
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        def dfs(cur):
            if not cur:
                return
            # 后序递归
            dfs(cur.left)
            dfs(cur.right)
            res.append(cur.val)
        res = []
        dfs(root)
        return res
```


4. 层序遍历

```python
# 递归1：二叉树遍历最易理解和实现版本

# 递归2：通用模板，可以适应不同的题目，添加参数、增加返回条件、修改进入递归条件、自定义返回值
```

## 二、迭代解法

时间复杂度：O(n)，n为节点数，访问每个节点恰好一次。

空间复杂度：O(h)，h为树的高度。取决于树的结构，最坏情况存储整棵树，即O(n)。

