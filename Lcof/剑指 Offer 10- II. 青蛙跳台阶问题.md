## 方法一：动态规划

### 算法流程

```
f(n + 1) = f(n) + f(n - 1)
f(0) = 1
f(1) = 1
返回 f(n)
```

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(1)

### 代码

``` python
class Solution:
    def numWays(self, n: int) -> int:
        a, b = 1, 1
        for _ in range(n):
            a, b = b, (a + b) % 1000000007
        return a
```

