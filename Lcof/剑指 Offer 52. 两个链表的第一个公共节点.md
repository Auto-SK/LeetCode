``` python
class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        h1, h2 = headA, headB
        while h1 != h2:
            h1 = h1.next if h1 else headB
            h2 = h2.next if h2 else headA
        return h1
```