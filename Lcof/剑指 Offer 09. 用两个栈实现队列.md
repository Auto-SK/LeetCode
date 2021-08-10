## 方法一：栈

### 算法流程

用两个栈`stack_in`和`stack_out`，`stack_in`负责入栈；出栈的时候看`stack_out`是否为空，为空就把`stack_in`倒过来。

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(n)

### 代码

``` python
class CQueue:

    def __init__(self):
        self.stack_in = []
        self.stack_out = []


    def appendTail(self, value: int) -> None:
        self.stack_in.append(value)


    def deleteHead(self) -> int:
        if self.stack_out:
            return self.stack_out.pop()
        if self.stack_in:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
            return self.stack_out.pop()
        return -1
```

