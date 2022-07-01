---
layout: post
title: Linked list manipulation logic
tags:
  - linkedlist
  - algorithms
---
### Reversing a linkedlist
Given the head of a linkedlist, reverse the list in place. 

Time complexity: O(n)

sample code: 
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if head == None:
            return head
        
        curr = head
        prev = None
        
        while curr.next != None:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp
        
        curr.next = prev
        
        return curr
```

### Finding the middle element of a linked list.
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        slow = head
        fast = head
        
        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            
        return slow
```

Time complexity: O(n)

If there are two middle nodes, the second middle node will be returned.