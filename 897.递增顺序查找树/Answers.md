897. 递增顺序查找树

给定一个树，按中序遍历重新排列树，使树中最左边的结点现在是树的根，并且每个结点没有左子结点，只有一个右子结点。

 

示例 ：

输入：[5,3,6,2,4,null,8,1,null,null,null,7,9]

       5
      / \
    3    6
   / \    \
  2   4    8
 /        / \ 
1        7   9

输出：[1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]

 1
  \
   2
    \
     3
      \
       4
        \
         5
          \
           6
            \
             7
              \
               8
                \
                 9  
 

提示：

给定树中的结点数介于 1 和 100 之间。
每个结点都有一个从 0 到 1000 范围内的唯一整数值。

Python version 00:
先中序遍历 获得 res = []
然后用 res 重新构建一颗只有右孩子的树

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def increasingBST(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        res = []
        inorder(root, res)
        # print(res) [1, 2, 3, 4, 5, 6, 7, 8, 9]
        newroot = TreeNode(res[0])
        tmp = newroot
        for i in range(1, len(res)):
            node = TreeNode(res[i])
            tmp.right = node
            tmp = tmp.right
        return newroot
            
def inorder(root, res):
    if root is None:
        return 
    inorder(root.left, res)
    res.append(root.val)
    inorder(root.right, res)
```