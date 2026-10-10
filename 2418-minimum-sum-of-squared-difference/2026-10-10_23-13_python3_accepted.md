# 2418. Minimum Sum of Squared Difference
  
<br>**Problem:** https://leetcode.com/problems/minimum-sum-of-squared-difference/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Binary Search, Greedy, Sorting, Heap (Priority Queue)<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-10 23:13 local time

**Runtime:** 611 ms (beats 8.75%)
**Memory:** 39.1 MB (beats 35%)


<!-- leetgit:submissionId=2168501597 codeHash=7f32e088e0b1ef7cfd9dd16040e967070f1b53273d7b39ae425a789109c594cc notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minSumSquareDiff(self, nums1: list[int], nums2: list[int], k1: int, k2: int) -> int:
        n = len(nums1)
        d = [abs(a - b) for a, b in zip(nums1, nums2)]
        total = sum(d)
        k = k1 + k2
        if total <= k:
            return 0
        left, right = 0, max(d)
        while left < right:
            mid = (left + right) // 2
            need = sum(max(0, v - mid) for v in d)
            if need <= k:
                right = mid
            else:
                left = mid + 1
        for i in range(n):
            k -= max(0, d[i] - left)
            d[i] = min(d[i], left)
        for i in range(n):
            if k == 0:
                break
            if d[i] == left:
                d[i] -= 1
                k -= 1
        return sum(v * v for v in d)
```
