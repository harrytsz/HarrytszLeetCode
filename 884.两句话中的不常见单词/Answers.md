884. 两句话中的不常见单词

给定两个句子 A 和 B 。 （句子是一串由空格分隔的单词。每个单词仅由小写字母组成。）

如果一个单词在其中一个句子中只出现一次，在另一个句子中却没有出现，那么这个单词就是不常见的。

返回所有不常用单词的列表。

您可以按任何顺序返回列表。

 

示例 1：

输入：A = "this apple is sweet", B = "this apple is sour"
输出：["sweet","sour"]
示例 2：

输入：A = "apple apple", B = "banana"
输出：["banana"]
 

提示：

0 <= A.length <= 200
0 <= B.length <= 200
A 和 B 都只包含空格和小写字母。

Python version 00:

```python
class Solution(object):
    def uncommonFromSentences(self, A, B):
        """
        :type A: str
        :type B: str
        :rtype: List[str]
        """
        from collections import Counter
        tmp = A +" "+ B
        # print(tmp)
        strings = tmp.split()
        # print(strings) #[u'this', u'apple', u'is', u'sweet', u'this', u'apple', u'is', u'sour']
        res = []
        counter = Counter(strings)
        for key in counter.keys():
            if counter[key]==1:
                res.append(key)
        return res
```