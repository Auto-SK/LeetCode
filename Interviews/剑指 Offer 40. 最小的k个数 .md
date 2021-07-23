## 方法一：堆排序

### 算法流程

建一个容量为 k 的小顶堆（因为 Python 没有大顶堆），将 -arr[:k] 压入堆中，如果有 -i > hp[0] 就弹出堆顶，将 -i 压入堆中。

### 复杂度分析

* 时间复杂度：O(nlogk)
* 空间复杂度：O(k)

### 代码

``` python
class Solution:
    def getLeastNumbers(self, arr: List[int], k: int) -> List[int]:
        if k == 0:
            return []
        if len(arr) <= k:
            return arr
        heap = [-i for i in arr[:k]]
        heapq.heapify(heap)
        for i in arr[k:]:
            if -i > heap[0]:
                heapq.heappop(heap)
                heapq.heappush(heap, -i)
        return [-i for i in heap]
```

