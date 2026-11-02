# 462. Minimum Moves to Equal Array Elements II
  
<br>**Problem:** https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-02 19:33 local time

**Runtime:** 6 ms (beats 38.8767%)
**Memory:** 20.1 MB (beats 98.2495%)


<!-- leetgit:submissionId=2187800819 codeHash=18958800d469ee055a3054ceec6fe7cda005eb33f356ade5a878b3da298a3bbb notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minMoves2(self, nums: List[int]) -> int:
        def quickselect(a, k):
            while True:
                if len(a) <= 1:
                    return a[0]
                p = random.choice(a)
                lo = [x for x in a if x < p]
                if k < len(lo):
                    a = lo
                    continue
                hi = [x for x in a if x > p]
                if k >= len(a) - len(hi):
                    k -= len(a) - len(hi)
                    a = hi
                    continue
                return p  # pivot sits at position k

        med = quickselect(nums, len(nums) // 2)
        return sum(abs(x - med) for x in nums)
```
