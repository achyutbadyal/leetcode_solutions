# Union of 2 Sorted Arrays

## Problem Information
- **Platform:** Geeksforgeeks
- **Difficulty:** Medium
- **URL:** https://www.geeksforgeeks.org/problems/union-of-two-sorted-arrays-1587115621/1
- **Date:** 2026-10-10

## Solution

```python
class Solution:
    def findUnion(self, a, b):
        return sorted(set(a).union(set(b)))
```

---
*Generated automatically by LeetFeedback Extension*
