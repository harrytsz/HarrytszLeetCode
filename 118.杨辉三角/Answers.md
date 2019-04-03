118. 杨辉三角

给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。



在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:

输入: 5
输出:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]

Python 版本：

```python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        res = []
        for i in range(numRows):
            curRow = [1]*(i+1)
            if i >= 2:
                for n in range(1, i):
                    curRow[n] = preRow[n-1] + preRow[n]
            res += [curRow]
            preRow = curRow
        return res
```