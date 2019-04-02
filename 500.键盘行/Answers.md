500. 键盘行

给定一个单词列表，只返回可以使用在键盘同一行的字母打印出来的单词。键盘如下图所示。

 

American keyboard

 

示例：

输入: ["Hello", "Alaska", "Dad", "Peace"]
输出: ["Alaska", "Dad"]
 

注意：

你可以重复使用键盘上同一字符。
你可以假设输入的字符串将只包含字母。

Python 版本1：

```python
class Solution(object):
    def findWords(self, words):
        set1 = set('qwertyuiop')
        set2 = set('asdfghjkl')
        set3 = set('zxcvbnm')
        res = []
        for i in words:
            x = i.lower()
            setx = set(x)
            if setx<=set1 or setx<=set2 or setx<=set3:
                res.append(i)
        return res
```

```python
class Solution(object):
    def isAvail(self, Arr):
        tmp = Arr[0]
        for i in Arr:
            if i != tmp:
                return False
        return True
        
    def findWords(self, words):
        """
        :type words: List[str]
        :rtype: List[str]
        """
        tmp = ['bcmnvxz', 'adfghjkls', 'eiopqrtuwy']
        map = {}
        
        n = 0
        for item in tmp:
            for i in item:
                map[i] = n
            n += 1
        res = []
        for string in words:
            st = set(string.lower())
            arr = [map[str(s)] for s in st]

            if self.isAvail(arr):
                res.append(string)
        return res
```