``` python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getKthFromEnd(self, head: ListNode, k: int) -> ListNode:
        # n = 0
        # cur = head
        # while cur:
        #     n += 1
        #     cur = cur.next
        # cur = head
        # for _ in range(n - k):
        #     cur = cur.next
        # return cur
        fast, slow = head, head
        for _ in range(k):
            fast = fast.next
        while fast:
            fast = fast.next
            slow = slow.next
        return slow
```