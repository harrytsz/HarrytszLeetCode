23. 合并K个排序链表

合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

示例:

输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6

Python 版本：

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def mergeKLists(self, lists: List[ListNode]) -> ListNode:
        values = []
        
        for item in lists:
            head = item
            while head:
                values.append(head.val)
                head = head.next
        
        values.sort()
        newhead = ListNode(0)
        tmp = newhead
        
        while len(values) > 0:
            tmp.next = ListNode(values.pop(0))
            tmp = tmp.next
        
        return newhead.next
```