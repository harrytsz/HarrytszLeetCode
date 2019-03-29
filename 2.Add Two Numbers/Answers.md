2. 两数相加

给出两个 非空 的链表用来表示两个非负的整数。其中，它们各自的位数是按照 逆序 的方式存储的，并且它们的每个节点只能存储 一位 数字。

如果，我们将这两个数相加起来，则会返回一个新的链表来表示它们的和。

您可以假设除了数字 0 之外，这两个数都不会以 0 开头。

**示例：**

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        if l1 is None:
            return l2
        if l2 is None:
            return l1
        
        tmp1 = l1
        tmp2 = l2
        newhead = ListNode(0)
        carry = 0
        tmp = newhead
        
        while tmp1 and tmp2:
            value = (tmp1.val + tmp2.val + carry)
            tmp.next = ListNode(value % 10)
            tmp = tmp.next
            carry = value / 10
            tmp1 = tmp1.next
            tmp2 = tmp2.next
        
        tmp12 = tmp1 if tmp1 else tmp2
            
        while tmp12:
            value12 = tmp12.val + carry
            tmp.next = ListNode(value12 % 10)
            tmp = tmp.next
            tmp12 = tmp12.next
            carry = value12 / 10
            
        if carry != 0:
            tmp.next = ListNode(1)
            
        return newhead.next
```