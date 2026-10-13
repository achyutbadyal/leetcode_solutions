# Two Sum

## Problem Information
- **Platform:** Leetcode
- **Difficulty:** Easy
- **URL:** https://leetcode.com/problems/two-sum/submissions/2171109972/
- **Date:** 2026-10-13

## Solution

```text
func twoSum(nums []int, target int) []int {
    seen := make(map[int]int)

    for ind1, n := range nums {
        left := target - n
        if ind2, ok := seen[left]; ok {
            return []int{ind1, ind2}
        }
        seen[n] = ind1
    }

    return []int{-1, -1}
}
```

---
*Generated automatically by LeetFeedback Extension*
