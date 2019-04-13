538. 把二叉搜索树转换为累加树

给定一个二叉搜索树（Binary Search Tree），把它转换成为累加树（Greater Tree)，使得每个节点的值是原来的节点值加上所有大于它的节点值之和。

例如：

输入: 二叉搜索树:
              5
            /   \
           2     13

输出: 转换为累加树:
             18
            /   \
          20     13

Python version 00:

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def convertBST(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if root is None:
            return 
        values = []
        inorder(root, values)
        # print(values)
        queue = [root]
        while queue:
            cur = queue.pop(0)
            index = values.index(cur.val)
            cur.val += sum(values[index+1:])
            if cur.left:
                queue.append(cur.left)
            if cur.right:
                queue.append(cur.right)
        return root
        

def inorder(root, values):
    if root is None:
        return 
    inorder(root.left, values)
    values.append(root.val)
    inorder(root.right, values)
```