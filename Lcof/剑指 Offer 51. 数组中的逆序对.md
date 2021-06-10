## 方法一：归并排序

### 算法流程

1. 终止条件： 当`l ≥ r`时，代表子数组长度为 1，此时终止划分；

2. 递归划分： 计算数组中点 `m`，递归划分左子数组`merge_sort(l, m)`和右子数组`merge_sort(m + 1, r)`；

3. 合并与逆序对统计：

    1. 暂存数组`nums`闭区间`[i, r]`内的元素至辅助数组`tmp`；

    2.  循环合并： 设置双指针`i`，`j`分别指向左 / 右子数组的首元素； 

        * 当`i = m + 1`时： 代表左子数组已合并完，因此添加右子数组当前元素`tmp[j]`，并执行`j = j + 1`；
        * 否则，当`j = r + 1`时： 代表右子数组已合并完，因此添加左子数组当前元素 `tmp[i]`，并执行`i = i + 1`；
        * 否则，当`tmp[i] ≤ tmp[j]`时： 添加左子数组当前元素`tmp[i]`，并执行`i = i + 1`；
        * 否则（即`tmp[i] > tmp[j]`）时： 添加右子数组当前元素`tmp[j]`，并执行`j = j + 1`；此时构成`m - i + 1`个「逆序对」，统计添加至`res`；

4. 返回值： 返回直至目前的逆序对总数`res`；

![Picture1.png](https://cdn.jsdelivr.net/gh/Auto-SK/CDN/Articles/Python3/1614274007-nBQbZZ-Picture1.png)

![Picture2.png](https://cdn.jsdelivr.net/gh/Auto-SK/CDN/Articles/Python3/1614274007-rtFHbG-Picture2.png)

### 复杂度分析

* 时间复杂度：O(nlogn)
* 空间复杂度：O(n)

### 代码

``` python
class Solution:
    def reversePairs(self, nums: List[int]) -> int:
        def merge_sort(l, r):
            # 终止条件
            if l >= r: return 0
            # 递归划分
            m = (l + r) // 2
            res = merge_sort(l, m) + merge_sort(m + 1, r)
            # 合并阶段
            i, j = l, m + 1
            tmp[l:r + 1] = nums[l:r + 1]
            for k in range(l, r + 1):
                if i == m + 1:
                    nums[k] = tmp[j]
                    j += 1
                elif j == r + 1 or tmp[i] <= tmp[j]:
                    nums[k] = tmp[i]
                    i += 1
                else:
                    nums[k] = tmp[j]
                    j += 1
                    res += m - i + 1 # 统计逆序对
            return res
        
        tmp = [0] * len(nums)
        return merge_sort(0, len(nums) - 1)
```