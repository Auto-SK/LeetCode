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