# 3372. Longest Strictly Increasing or Strictly Decreasing Subarray
  
<br>**Problem:** https://leetcode.com/problems/longest-strictly-increasing-or-strictly-decreasing-subarray/<br>

**Difficulty:** Easy<br>
**Topics:** Array<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-12 21:02 local time

**Runtime:** 2 ms (beats 42.0131%)
**Memory:** 19.4 MB (beats 21.225399999999997%)


<!-- leetgit:submissionId=2194713640 codeHash=8883fe92ed56e5633627d9827eca243a9a3c26180a8bfe5bde710af5145ed8e4 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def longestMonotonicSubarray(self, nums: list[int]) -> int:
        best = up = down = 1
        for a, b in pairwise(nums):
            up = up + 1 if a < b else 1  # increasing streak ending at b
            down = down + 1 if a > b else 1  # decreasing streak ending at b
            best = max(best, up, down)
        return best
```
