1002. 查找常用字符

给定仅有小写字母组成的字符串数组 A，返回列表中的每个字符串中都显示的全部字符（包括重复字符）组成的列表。例如，如果一个字符在每个字符串中出现 3 次，但不是 4 次，则需要在最终答案中包含该字符 3 次。

你可以按任意顺序返回答案。

 

示例 1：

输入：["bella","label","roller"]
输出：["e","l","l"]
示例 2：

输入：["cool","lock","cook"]
输出：["c","o"]
 

提示：

1 <= A.length <= 100
1 <= A[i].length <= 100
A[i][j] 是小写字母

Python 版本 01：

```python
class Solution(object):
    def commonChars(self, A):
        """
        :type A: List[str]
        :rtype: List[str]
        """
        string0 = A[0]
        charSet = list(set(string0))   # 最终结果中出现的字母，不会超出 A[0] 字符串中的字母范围，所以剩下的工作就是逐渐缩小这个范围
        
        # tmp 用来记录 charSet 中的每个字母在 A[0], A[1], A[2], ....中出现的次数
        tmp = []
        for string in A:
            map = {}
            for item in charSet:
                a = string.count(item)
                #print(item, a)
                map[item] = a
            tmp.append(map)
        # print(tmp)
        
        ############# 接下来开始组合答案：
        # 找出 tmp['o'] 对应的最小值，该值表示 'o' 在所有字符串中出现的最小次数，按照此次数将 'o' 添加 res[] 若干次。
        res = []
        for ch in charSet:
            minTime = 101
            for i,item in enumerate(tmp):
                minTime = min(minTime, item[ch])
            for i in range(minTime):
                res.append(ch)
        return res
```

最朴素的思路：首先选定结果集的最大范围 charSet，即最终结果肯定是由 charSet 中的字母组合而成。接下来就是确定 charSet 中每个字母在 A 中所有字符串中出现的次数的最小值，最后按照 charSet 中每个字母以及其最小的出现次数来组织 res 结果。