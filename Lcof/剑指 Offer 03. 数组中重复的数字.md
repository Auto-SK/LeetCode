``` python
class Solution:
    def findRepeatNumber(self, nums: List[int]) -> int:
        # nums.sort()
        # for i in range(len(nums) - 1):
        #     if nums[i] == nums[i + 1]:
        #         return nums[i]
        tmp_set = set()
        repeat = -1
        for i in range(len(nums)):
            tmp_set.add(nums[i])
            if len(tmp_set) < i + 1:
                repeat = nums[i]
                break
        return repeat
```