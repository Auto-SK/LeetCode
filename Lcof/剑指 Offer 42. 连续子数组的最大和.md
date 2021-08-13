## 方法一：动态规划

### 算法流程

```
dp[i] 代表以第 i 个数结尾的「连续子数组的最大和」

dp[i] = nums[i] if dp[i - 1] <= 0 else nums[i] + dp[i - 1]
```

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(n)

### 代码

``` python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        # dp = [0] * len(nums)
        # dp[0] = nums[0]
        # res = dp[0]
        # for i in range(1, len(nums)):
        #     dp[i] = max(dp[i - 1] + nums[i], nums[i])
        #     if res < dp[i]:
        #         res = dp[i]
        # return res

        # res = nums[0]
        # pre = nums[0]
        # for i in range(1, len(nums)):
        #     cur = max(pre + nums[i], nums[i])
        #     pre = cur
        #     if cur > res:
        #         res = cur
        # return res
        
        for i in range(1, len(nums)):
            nums[i] += max(0, nums[i - 1])
        return max(nums)
```

