## 方法一：字符串遍历

### 算法流程



### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(n)

### 代码

``` python
class Solution:
    def replaceSpace(self, s: str) -> str:
        s1 = ''
        for i in s:
            if i == ' ':
                s1 += '%20'
            else:
                s1 += i
        return s1
```

