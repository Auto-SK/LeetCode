``` python
class Solution:
    def reversePrint(self, head: ListNode) -> List[int]:
        ans = []
        cur = head
        while cur:
            ans.append(cur.val)
            cur = cur.next
        return ans[::-1]
```