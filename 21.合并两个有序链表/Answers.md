21. 合并两个有序链表
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

示例：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

Python 版本：

```python
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if l1 is None:
            return l2
        if l2 is None:
            return l1
        
        tmp1 = l1
        tmp2 = l2
        newhead = ListNode(0)
        tmp = newhead
        while tmp1 and tmp2:
            if tmp1.val < tmp2.val:
                tmp.next = tmp1
                tmp1 = tmp1.next
            else:
                tmp.next = tmp2
                tmp2 = tmp2.next
            tmp = tmp.next
            
        rest = tmp1 if tmp1 else tmp2
        tmp.next = rest
        return newhead.next
        
````