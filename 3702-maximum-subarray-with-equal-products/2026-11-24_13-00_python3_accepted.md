# 3702. Maximum Subarray With Equal Products
  
<br>**Problem:** https://leetcode.com/problems/maximum-subarray-with-equal-products/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Math, Sliding Window, Enumeration, Number Theory<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-24 13:00 local time

**Runtime:** 2 ms (beats 95.8333%)
**Memory:** 19.1 MB (beats 95%)


<!-- leetgit:submissionId=2202424664 codeHash=ea6b6a16763e56f00b109834a92ebedcf9e4ae149eaeee4e99113f1cbb3d4670 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxLength(self, nums: list[int]) -> int:
        best, left, product = 2, 0, 1
        for right, x in enumerate(nums):
            while gcd(product, x) > 1:
                product //= nums[left]
                left += 1
            product *= x
            best = max(best, right - left + 1)
        return best
```
