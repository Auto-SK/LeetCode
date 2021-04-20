``` python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        votes = 0
        for num in nums:
            if votes == 0:
                x = num
            if num == x:
                votes += 1
            else:
                votes -= 1
        # 验证 x 是否为众数
        count = 0
        for num in nums:
            if num == x:
                count += 1
        if count < len(nums) / 2:
            return -1
        return x
```