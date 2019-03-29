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
        if not l1:
            return l2
        if not l2:
            return l1
        
        tmp1 = l1
        tmp2 = l2
        newhead = ListNode(0)
        tmp = newhead
        carry = 0
        
        while tmp1 and tmp2:
            val = tmp1.val + tmp2.val + carry
            carry = val / 10
            tmp.next = ListNode(val % 10)
            tmp = tmp.next
            tmp1 = tmp1.next
            tmp2 = tmp2.next
            
        tmp12 = tmp1 if tmp1 else tmp2
        
        while tmp12:
            val = tmp12.val + carry
            carry = val / 10
            tmp.next = ListNode(val % 10)
            tmp = tmp.next
            tmp12 = tmp12.next
        
        if carry != 0:
            tmp.next = ListNode(1)
            
        return newhead.next
```

Java 版本

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        if (l1 == null) return l2;
        else if (l2 == null) return l1;
        
        ListNode tmp1 = l1;
        ListNode tmp2 = l2;
        int carry = 0;
        ListNode newhead = new  ListNode(0);
        ListNode tmp = newhead;
        
        while (tmp1 != null && tmp2 != null)
        {
            int val = (tmp1.val + tmp2.val + carry);
            carry = val / 10;
            tmp.next = new ListNode(val % 10);
            tmp = tmp.next;
            tmp1 = tmp1.next;
            tmp2 = tmp2.next;
        }
        
        ListNode tmp12 = tmp1 != null ? tmp1 : tmp2;
        
        while (tmp12 != null)
        {
            int val = (tmp12.val + carry);
            carry = val / 10;
            tmp.next = new ListNode(val % 10);
            tmp = tmp.next;
            tmp12 = tmp12.next;
        }
        
        if (carry != 0)
        {
            tmp.next = new ListNode(1);
        }
        
        return newhead.next;
    }
}
```