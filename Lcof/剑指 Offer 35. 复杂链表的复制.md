## 方法一：哈希表

### 算法流程

利用哈希表的查询特点，考虑构建 **原链表节点** 和 **新链表对应节点** 的键值对映射关系，再遍历构建新链表各节点的 `next` 和 `random` 引用指向即可。

1. 若头节点 head 为空节点，直接返回 null ；

2. **初始化**： 哈希表 dic ，节点 cur 指向头节点；

3. **复制链表**：

    1. 建立新节点，并向 dic 添加键值对 (原 cur 节点, 新 cur 节点）；

    2. cur 遍历至原链表下一节点；

4. 构建新链表的引用指向：
    1. 构建新节点的 next 和 random 引用指向；
    2. cur 遍历至原链表下一节点；
5. 返回值： 新链表的头节点 dic[cur] ；

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(n)

### 代码

``` python
class Solution:
    def copyRandomList(self, head: 'Node') -> 'Node':
        if not head:
            return None
        dic = {}
        # 复制各节点，并建立 "原节点 -> 新节点" 的 Map 映射
        cur = head
        while cur:
            dic[cur] = Node(cur.val)
            cur = cur.next
        # 构建新节点的 next 和 random 指向
        cur = head
        while cur:
            dic[cur].next = dic.get(cur.next)
            dic[cur].random = dic.get(cur.random)
            cur = cur.next
        # 返回新链表的头节点
        return dic[head]
```

