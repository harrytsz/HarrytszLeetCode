189. 旋转数组

给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

示例 1:

输入: [1,2,3,4,5,6,7] 和 k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右旋转 1 步: [7,1,2,3,4,5,6]
向右旋转 2 步: [6,7,1,2,3,4,5]
向右旋转 3 步: [5,6,7,1,2,3,4]
示例 2:

输入: [-1,-100,3,99] 和 k = 2
输出: [3,99,-1,-100]
解释: 
向右旋转 1 步: [99,-1,-100,3]
向右旋转 2 步: [3,99,-1,-100]
说明:

尽可能想出更多的解决方案，至少有三种不同的方法可以解决这个问题。
要求使用空间复杂度为 O(1) 的原地算法。

Python version 00:

```python
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        length = len(nums)
        if k > length:
            k = k % length
        if k < 1:
            return nums
        front = nums[:length-k]
        # print(front)
        after = nums[-k:]
        # print(after)
        nums[:k] = after
        nums[k:] = front
        
```

Python version 01

```python
class Solution(object):
    def reverseArr(self, arr, start, end):
        while start < end:
            tmp = arr[start]
            arr[start] = arr[end]
            arr[end] = tmp
            start += 1
            end -= 1
    
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        if nums is None:
            return None
        length = len(nums)
        k = k % length
        self.reverseArr(nums, 0, length-k-1)
        self.reverseArr(nums, length-k, length-1)
        self.reverseArr(nums, 0, length-1)
```