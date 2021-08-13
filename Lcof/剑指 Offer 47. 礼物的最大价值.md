## 方法一：动态规划

### 算法流程

* 状态定义： 设动态规划矩阵 dp，dp(i,j) 代表从棋盘的左上角开始，到达单元格 (i,j) 时能拿到礼物的最大累计价值。
* 转移方程：

1. 当 i = 0 且 j = 0 时，为起始元素；
2. 当 i = 0 且 j != 0 时，为矩阵第一行元素，只可从左边到达；
3. 当 i != 0 且 j = 0 时，为矩阵第一列元素，只可从上边到达；
4. 当 i != 0 且 j != 0 时，可从左边或上边到达；

$$
dp(i,j)=\left\{ \begin{matrix}
	\mathrm{grid(}i,j)&		,i=0,j=0\\
	\mathrm{grid(}i,j)+dp(i,j-1)&		,i=0,j\ne 0\\
	\mathrm{grid(}i,j)+dp(i-1,j)&		,i\ne 0,j=0\\
	\mathrm{grid(}i,j)+\max\mathrm{[}dp(i-1,j),dp(i,j-1)]&		,i\ne 0,j\ne 0\\
\end{matrix} \right.
$$

### 复杂度分析

* 时间复杂度：O(mn)
* 空间复杂度：O(mn)

### 代码

``` python
class Solution:
    def maxValue(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        # 初始化第一行
        for j in range(1, n):
            grid[0][j] += grid[0][j - 1]
        # 初始化第一列
        for i in range(1, m):
            grid[i][0] += grid[i - 1][0]
        for i in range(1, m):
            for j in range(1, n):
                grid[i][j] += max(grid[i - 1][j], grid[i][j - 1])
        return grid[-1][-1]
```

