
## 方法一：

### 算法流程

- 基础：
    - 同余定理。 若 (a - b)%k = 0, 则 a%k = b%k. （等价的有 a%k - b%k = 0）
    - 对于本题而言，若 (total_sum - delete_sum) % k = 0, 则 total_sum % k = delete_sum % k.
    - 注意到，给定nums，total_sum % k 仅仅是一个常数，不妨称为我们的目标余数 tar_remainder, 则有tar_remainder = delete_sum%k.
- 前缀和。给定数组nums，定义前缀和presum[i] = nums[0] + nums[1] + ... + nums[i]. 若删去的子数组起始下标分别为i, j，则delete_sum = presum[j] - presum[i-1]. 再结合基础中的分析，有 tar_remainder = (presum[j] - presum[i-1]) % k. 这里我们对等式右端再次运用同余定理，并移项得：presum[i-1] % k = presum[j] % k - tar_remainder.
- 上述思路启示我们，通过前缀和，每次记录下对应项前缀和的余数，同时判断该项前面是否有记录过的余数等于现在计算得到的余数减掉目标余数。若有，则获取之前对应的下标i-1，和现在的对应的下标j，二者相减即为删去的子数组的元素个数。通过比较选取最小的个数即可。
- Hash表。进一步，这又启示我们需要选择合适的数据结构，使得余数和下标对应且便于查找之前的余数。一个选择是使用大小为n的数组，其中nums的下标为数组下标，而相应余数为该数组的值，另一个选择就是我们这里的Hash表，余数作为键，nums中对应下标作为值。

### 复杂度分析

* 时间复杂度：O(n)
* 空间复杂度：O(n)

### 代码

``` python
class Solution:
    def solve(self, nums, k):
        tar_remainder = (sum(nums) + k) % k
        if tar_remainder == 0:
            return 0
        n, presum = len(nums), 0
        hashmap = {0: -1}
        res = n
        for i in range(n):
            presum += nums[i]
            modulus = (presum + k) % k
            hashmap[modulus] = i
            if (modulus - tar_remainder + k) % k in hashmap:
                res = min(res, i - hashmap[(modulus - tar_remainder + k) % k])
        return res if res != n else -1
```

