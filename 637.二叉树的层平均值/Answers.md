637. 二叉树的层平均值

给定一个非空二叉树, 返回一个由每层节点平均值组成的数组.

示例 1:

输入:
    3
   / \
  9  20
    /  \
   15   7
输出: [3, 14.5, 11]
解释:
第0层的平均值是 3,  第1层是 14.5, 第2层是 11. 因此返回 [3, 14.5, 11].
注意：

节点值的范围在32位有符号整数范围内。

Python version 00 

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def averageOfLevels(self, root):
        """
        :type root: TreeNode
        :rtype: List[float]
        """
        if root is None:
            return []
        res = []
        queue = [root]
        while queue:
            qsize = len(queue)
            t = qsize
            levelsum = 0
            while t > 0:
                cur = queue.pop()
                levelsum += cur.val
                t -= 1
            if cur.left:
                queue.append(cur.left)
            if cur.right:
                queue.append(cur.right)
            res.append(float(levelsum)/qsize)
        return res
```