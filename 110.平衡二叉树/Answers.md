110. 平衡二叉树

给定一个二叉树，判断它是否是高度平衡的二叉树。

本题中，一棵高度平衡二叉树定义为：

一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。

示例 1:

给定二叉树 [3,9,20,null,null,15,7]

    3
   / \
  9  20
    /  \
   15   7
返回 true 。

示例 2:

给定二叉树 [1,2,2,3,3,null,null,4,4]

       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
返回 false 。

Python version 00:

```python 
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isBalanced(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root:
            return True
        if abs(countFloor(root.left)-countFloor(root.right))>1:
            return False
        else:
            return self.isBalanced(root.left) and self.isBalanced(root.right)

def countFloor(root):
    if not root:
        return 0
    else:
        return 1+max(countFloor(root.left), countFloor(root.right))
```

Java Version 01:

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isBalanced(TreeNode root) {
        boolean[] res = new boolean[1];
        res[0] = true;
        getHeight(root, 1, res);
        return res[0];
    }
    
    public int getHeight(TreeNode head, int level, boolean[] res){
        if (head == null){
            return level;
        }
        int lH = getHeight(head.left, level+1, res);
        if (!res[0]){
            return level;
        }
        int rH = getHeight(head.right, level+1, res);
        if (!res[0]){
            return level;
        }
        if ((Math.abs(lH-rH))>1){
            res[0] = false;
        }
        return Math.max(lH, rH);
    }
}
```

Python version 02:

```python 
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        flag = [True]
        getHeight(root, 1, flag)
        return flag[0]
    
def getHeight(head, level, flag):
    if not head:
        return level
    lH = getHeight(head.left, level+1, flag)
    if not flag[0]:
        return level
    rH = getHeight(head.right, level+1, flag)
    if not flag[0]:
        return level
    if abs(lH-rH)>1:
        flag[0] = False
    return max(lH, rH)
```