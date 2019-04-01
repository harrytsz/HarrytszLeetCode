590. N叉树的后序遍历

给定一个 N 叉树，返回其节点值的后序遍历。

例如，给定一个 3叉树 :

<img src="https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/12/narytreeexample.png">

返回其后序遍历: [5,6,3,2,4,1].

 

说明: 递归法很简单，你可以使用迭代法完成此题吗?

Python 版本：

```python
## 递归版本 后序遍历
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if root is None:
            return []
        res = []
        for node in root.children:
            res += self.postorder(node)
        res.append(root.val)
        return res
```

```python
## 递归版 先序遍历
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def postorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if root is None:
            return []
        res = []
        res.append(root.val)
        for node in root.children:
            res += self.postorder(node)
        return res
```