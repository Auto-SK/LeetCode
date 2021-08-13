## 方法一：链表

### 算法流程

![Picture1.png](https://pic.leetcode-cn.com/1604779288-WXygqL-Picture1.png)

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(1)

### 代码

``` python
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        pre = None
        cur = head
        while cur:
            cur.next, pre, cur = pre, cur, cur.next
        return pre
```

