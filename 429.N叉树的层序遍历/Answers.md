429. N叉树的层序遍历

给定一个 N 叉树，返回其节点值的层序遍历。 (即从左到右，逐层遍历)。

例如，给定一个 3叉树 :

 



 

返回其层序遍历:

[
     [1],
     [3,2,4],
     [5,6]
]
 

说明:

树的深度不会超过 1000。
树的节点总数不会超过 5000。

Python DFS：

```python
"""
# Definition for a Node.
class Node(object):
    def __init__(self, val, children):
        self.val = val
        self.children = children
"""
class Solution(object):
    def levelOrder(self, root):
        """
        :type root: Node
        :rtype: List[List[int]]
        """
        if root is None:
            return []
        res = []
        tmp = [root]
        while tmp:
            tval = []
            for i in range(len(tmp)):
                node = tmp.pop(0)
                tval.append(node.val)
                for children in node.children:
                    tmp.append(children)
            res.append(tval)
        return res
                
```