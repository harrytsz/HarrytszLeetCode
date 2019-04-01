922. 按奇偶排序数组 II

给定一个非负整数数组 A， A 中一半整数是奇数，一半整数是偶数。

对数组进行排序，以便当 A[i] 为奇数时，i 也是奇数；当 A[i] 为偶数时， i 也是偶数。

你可以返回任何满足上述条件的数组作为答案。

 

示例：

输入：[4,2,5,7]
输出：[4,5,2,7]
解释：[4,7,2,5]，[2,5,4,7]，[2,7,4,5] 也会被接受。
 

提示：

2 <= A.length <= 20000
A.length % 2 == 0
0 <= A[i] <= 1000

Python 版本：

```python
class Solution(object):
    def sortArrayByParity(self, Arr):
        i = 0
        for j in range(len(Arr)):
            if Arr[j] % 2 != 0:
                Arr[j], Arr[i] = Arr[i], Arr[j]
                i += 1
        return Arr
    
    def sortArrayByParityII(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        tmp = self.sortArrayByParity(A)
        mid = len(tmp) // 2
        A = tmp[:mid]   # 奇数部分
        B = tmp[mid:]   # 偶数部分
        res = []
        flag = False
        
        i = 0
        while i < len(tmp):
            if flag:
                res.append(A.pop())
                flag = not flag
            else:
                res.append(B.pop())
                flag = not flag
            i += 1
        return res
```