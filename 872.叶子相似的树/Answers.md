872. 叶子相似的树

请考虑一颗二叉树上所有的叶子，这些叶子的值按从左到右的顺序排列形成一个 叶值序列 。



举个例子，如上图所示，给定一颗叶值序列为 (6, 7, 4, 9, 8) 的树。

如果有两颗二叉树的叶值序列是相同，那么我们就认为它们是 叶相似 的。

如果给定的两个头结点分别为 root1 和 root2 的树是叶相似的，则返回 true；否则返回 false 。

提示：

给定的两颗树可能会有 1 到 100 个结点。

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        if root1 is None and root2 is None:
            return True
        res1 = []
        res2 = []
        self.leaf(root1, res1)
        self.leaf(root2, res2)
        # print(res1)
        # print(res2)
        return res1 == res2
        
    def leaf(self, root, res):
        if root is None:
            return 
        if root.left is None and root.right is None:
            res.append(root.val)
        self.leaf(root.left, res)
        self.leaf(root.right, res)
        
```