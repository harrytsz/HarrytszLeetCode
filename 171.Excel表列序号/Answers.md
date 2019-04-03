171. Excel表列序号

给定一个Excel表格中的列名称，返回其相应的列序号。

例如，

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
示例 1:

输入: "A"
输出: 1
示例 2:

输入: "AB"
输出: 28
示例 3:

输入: "ZY"
输出: 701
致谢：
特别感谢 @ts 添加此问题并创建所有测试用例。

Python 版本： 26进制 ---> 10进制

```python
class Solution(object):
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        map = {}
        stand = ord('A')
        for i in range(26):     # 创建字典 {'A': 1, 'B': 2, 'C': 3, ...., 'Z': 26}
            map[chr(stand+i)] = i + 1
        # print(map)
        res = 0
        n = len(s)
        # print(n)
        for i, item in enumerate(s):
            tmp = map[item] * (26 ** (n-i-1))   # 计算当前字母代表的十进制数值， 相当于 26进制 ---> 10 进制
            res += tmp
        return res
```