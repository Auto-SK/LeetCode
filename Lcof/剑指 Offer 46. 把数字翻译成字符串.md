## 方法一：动态规划

### 算法流程

$$
dp\left[ i \right] =\begin{cases}
	dp\left[ i-1 \right] +dp\left[ i-2 \right] , if\,\,s\left[ i-2: i \right] \in \left[ 10, 25 \right]\\
	dp\left[ i-1 \right] , else\\
\end{cases}
\\
dp\left[ 0 \right] =dp\left[ 1 \right] =1
$$

dp[i] 表示以第 i 位结尾的前缀串翻译的方案数，dp[0] 表示第 0 位，dp[n] 表示第 n 位。

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(n)

### 代码

``` python
class Solution:
    def translateNum(self, num: int) -> int:
        str_num = str(num)
        n = len(str_num)
        dp = [1 for _ in range(n + 1)] 
        for i in range(2, n + 1):
            if str_num[i - 2] == '1' or (str_num[i - 2] == '2' and str_num[i - 1] < '6'):
                dp[i] = dp[i - 2] + dp[i - 1]
            else:
                dp[i] = dp[i - 1]
        return dp[n]
```

