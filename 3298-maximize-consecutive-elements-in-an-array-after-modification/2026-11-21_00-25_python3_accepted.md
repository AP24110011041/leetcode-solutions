# 3298. Maximize Consecutive Elements in an Array After Modification
  
<br>**Problem:** https://leetcode.com/problems/maximize-consecutive-elements-in-an-array-after-modification/<br>

**Difficulty:** Hard<br>
**Topics:** Array, Dynamic Programming, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-21 00:25 local time

**Runtime:** 115 ms (beats 95.71419999999999%)
**Memory:** 32 MB (beats 78.5715%)


<!-- leetgit:submissionId=2200182493 codeHash=9cb2d2eebb18bacfdc4087cf4cebf65401e0fa7b60294473d88b8d50ef927074 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxSelectedElements(self, nums: list[int]) -> int:
        best = keep = bump = 1
        last = -10
        for x in sorted(nums):
            match x - last:
                case 0: bump = keep + 1  # x repeat: bump it on top of keep
                case 1: keep, bump = keep + 1, bump + 1  # x extends keep, x + 1 extends bump
                case 2: keep, bump = bump + 1, 1  # x extends bump, x + 1 starts over
                case _: keep = bump = 1
            best, last = max(best, keep, bump), x
        return best
```
