821. 字符的最短距离

给定一个字符串 S 和一个字符 C。返回一个代表字符串 S 中每个字符到字符串 S 中的字符 C 的最短距离的数组。

示例 1:

输入: S = "loveleetcode", C = 'e'
输出: [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]
说明:

字符串 S 的长度范围为 [1, 10000]。
C 是一个单字符，且保证是字符串 S 里的字符。
S 和 C 中的所有字母均为小写字母。

Python 版本：

```python
class Solution(object):
    def shortestToChar(self, S, C):
        """
        :type S: str
        :type C: str
        :rtype: List[int]
        """
        rightC = S.find(C)  # 当前索引右边第一个 C 的位置
        leftC = - 2**31      # 当前索引左边第一个 C 的位置
        res = []
        for i, item in enumerate(S):
            if i > rightC:      # 只需在索引值 i 超出了 [leftC, rightC] 右边界的时候才需要更新边界
                leftC = rightC
                rightC = max(rightC, S[i:].find(C) + rightC+1)
            magin = min(abs(i-leftC), abs(rightC-i))  # 计算在当前 [leftC, rightC] 边界中，i 距离左右边界哪个更近
            res.append(magin)        
        return res
```