# 4041. Climbing Stairs II
  
<br>**Problem:** https://leetcode.com/problems/climbing-stairs-ii/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Dynamic Programming<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-11 00:03 local time

**Runtime:** 153 ms (beats 94.10659999999993%)
**Memory:** 33.3 MB (beats 68.50829999999999%)


<!-- leetgit:submissionId=2193403037 codeHash=d3de31964b5fecfd111f0825e0b9c71bc01f78e508d890c7e2206693c12c7671 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def climbStairs(self, n: int, costs: list[int]) -> int:
        costs = [0] + costs
        a, b, c = costs[n], inf, inf  # dp[i + 1], dp[i + 2], dp[i + 3] for i = n - 1
        for i in reversed(range(n)):
            a, b, c = costs[i] + min(a + 1, b + 4, c + 9), a, b
        return a
```
