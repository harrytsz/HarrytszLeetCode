589. N叉树的前序遍历

给定一个 N 叉树，返回其节点值的前序遍历。

例如，给定一个 3叉树 :

 



 

返回其前序遍历: [1,3,5,6,2,4]。

 

说明: 递归法很简单，你可以使用迭代法完成此题吗?

Python version 00 queue:

```python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def preorder(self, root):
        """
        :type root: Node
        :rtype: List[int]
        """
        if root is None:
            return []
        
        res = []
        queue = [root]
        while queue:
            cur = queue.pop(0)
            res.append(cur.val)
            if cur.children:
                # cur.children.reverse()
                queue = cur.children + queue
        return res
            
```