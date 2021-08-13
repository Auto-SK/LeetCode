## 方法一：单调队列

### 算法流程

为了实现此递减列表，需要使用**双向队列**，假设队列已经有若干元素：

当执行入队 push_back() 时： 若入队一个比队列某些元素更大的数字 x ，则为了保持此列表递减，需要将双向队列 尾部所有小于 x 的元素 弹出。
当执行出队 pop_front() 时： 若出队的元素是最大元素，则 双向队列**需要同时**将首元素出队 ，以保持队列和双向队列的元素一致性。

### 复杂度分析

* 时间复杂度：O(1)
* 空间复杂度：O(n)

### 代码

``` python
class MaxQueue:

    def __init__(self):
        self.queue = collections.deque()  # 数据队列
        self.deque = collections.deque()  # 单调队列

    def max_value(self) -> int:
        return self.deque[0] if self.deque else -1

    def push_back(self, value: int) -> None:
        self.queue.append(value)
        while self.deque and self.deque[-1] < value:
            self.deque.pop()
        self.deque.append(value)

    def pop_front(self) -> int:
        if not self.deque:
            return -1
        res = self.queue.popleft()
        if res == self.deque[0]:
            self.deque.popleft()
        return res
```

