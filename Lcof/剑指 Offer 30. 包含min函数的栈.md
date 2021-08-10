## 方法一：栈

### 算法流程

用两个栈，数据栈`stack_data`和最小栈`stack_min`。数据栈用来存所有的数据，最小栈用来存所有的最小值。

* `push`：此时`stack_data`入栈，`stack_min`判断栈是否为空或者元素**小于等于**栈顶元素，小于等于是因为会有重复的最小值；
* `pop`：比较`stack_data`栈顶和`stack_min`栈顶是否相等，如果相等，`stack_min`也要出栈；
* `top`：返回`stack_data`栈顶值；
* `min`：返回`stack_min`栈顶值。

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(1)

### 代码

``` python
class MinStack:

    def __init__(self):
        """
        initialize your data structure here.
        """
        self.stack_data = []
        self.stack_min = []


    def push(self, x: int) -> None:
        self.stack_data.append(x)
        if not self.stack_min or x <= self.stack_min[-1]:  # 必须是<=，因为有重复的最小值
            self.stack_min.append(x)


    def pop(self) -> None:
        if self.stack_data.pop() == self.stack_min[-1]:
            self.stack_min.pop()


    def top(self) -> int:
        return self.stack_data[-1]


    def min(self) -> int:
        return self.stack_min[-1]
```

