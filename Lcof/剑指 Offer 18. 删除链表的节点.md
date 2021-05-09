``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution:
    def deleteNode(self, head: ListNode, val: int) -> ListNode:
        if head == None:
            return None
        if head.val == val:
            return head.next
        cur = head
        while cur.next != None and cur.next.val != val:
            cur = cur.next
        if cur.next != None:
            cur.next = cur.next.next
        return head
```