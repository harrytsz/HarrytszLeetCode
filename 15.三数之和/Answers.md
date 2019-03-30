15. 三数之和
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。

例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]


```python
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        nums.sort()
        L, res = len(nums), []
        for i in range(L-2):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            target = -1 * nums[i]
            j,k = i + 1, L - 1
            while j<k:
                if nums[j]+nums[k] == target:
                    res.append([nums[i], nums[j], nums[k]])
                    j = j + 1
                    while j<k and nums[j] == nums[j-1]:
                        j = j + 1
                elif nums[j] + nums[k] < target:
                    j = j + 1
                else:
                    k = k - 1
        return res
```