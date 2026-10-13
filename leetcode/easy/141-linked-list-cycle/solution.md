# Linked List Cycle

## Problem Information
- **Platform:** Leetcode
- **Difficulty:** Easy
- **URL:** https://leetcode.com/problems/linked-list-cycle/submissions/2171301943/
- **Date:** 2026-10-13

## Solution

```text
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
    if head == nil {
        return false
    }

    fast := head
    slow := head

    for ; fast.Next != nil && fast.Next.Next != nil; {
        fast = fast.Next.Next
        slow = slow.Next
        if fast == slow {
            return true
        }
    }
    return false
}
```

---
*Generated automatically by LeetFeedback Extension*
