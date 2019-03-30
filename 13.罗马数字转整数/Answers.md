13. 罗马数字转整数
罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。

字符          数值
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。

示例 1:

输入: "III"
输出: 3
示例 2:

输入: "IV"
输出: 4
示例 3:

输入: "IX"
输出: 9
示例 4:

输入: "LVIII"
输出: 58
解释: L = 50, V= 5, III = 3.
示例 5:

输入: "MCMXCIV"
输出: 1994
解释: M = 1000, CM = 900, XC = 90, IV = 4.

Python 版本：

```python
class Solution:
    def romanToInt(self, s: str) -> int:
        map = {'M':1000, 'D':500, 'C':100, 'L':50, 'X':10, 'V':5, 'I':1}
        result = 0
        start = 0
        end = len(s)-1
        
        while start < end:            # start 的范围： [0, len(s)-1)
            cur = map[s[start]]    
            next = map[s[start+1]]
            if next > cur:            # 相邻的两个数字中，如果后面一位数字比当前的数字大，表示遇到了“一对组合”
                tmp = next-cur
                result += tmp
                start += 2
            else:
                result += cur
                start += 1
                
        if start == end:          # start = len(s) - 2, 即表示 s 中还有最后一位没有遍历到的情形
            result += map[s[-1]]  # 当前结果加上最后一位没有遍历到的数，返回最终结果
            return result
        elif start == end+1:      # start = len(s) - 1, 即表示遍历了 s 中所有的数字
            return result
        else:
            return None
```