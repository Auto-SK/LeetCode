## 方法一：字符串

### 算法流程

![Picture1.png](https://pic.leetcode-cn.com/0be9098b13047fe3e07f3c4e51c612244ace01a023ed010bce43940408334f2a-Picture1.png)

![Picture2.png](https://pic.leetcode-cn.com/d1b06a91801868af63f6e309da31bcfa01c7b6c385529fb974389a61e454cd12-Picture2.png)

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(1)

### 代码

``` python
class Solution:
    def strToInt(self, str: str) -> int:
        res, i, sign, length = 0, 0, 1, len(str)
        int_max, int_min, bndry = 2 ** 31 - 1, -2 ** 31, 2 ** 31 // 10
        if not str: 
            return 0  # 空字符串，提前返回
        while str[i] == ' ':
            i += 1
            if i == length: 
                return 0  # 字符串全为空格，提前返回
        if str[i] == '-': 
            sign = -1
        if str[i] in '+-': 
            i += 1
        for j in range(i, length):
            if not '0' <= str[j] <= '9': 
                break
            if res > bndry or res == bndry and str[j] > '7':
                return int_max if sign == 1 else int_min
            res = 10 * res + ord(str[j]) - ord('0')
        return sign * res
```

