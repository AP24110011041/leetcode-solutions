# 115. Distinct Subsequences
  
<br>**Problem:** https://leetcode.com/problems/distinct-subsequences/<br>

**Difficulty:** Hard<br>
**Topics:** String, Dynamic Programming<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-06 19:58 local time

**Runtime:** 923 ms (beats 5.618600000000415%)
**Memory:** 254.7 MB (beats 5.10480000000012%)


<!-- leetgit:submissionId=2132942211 codeHash=13f6f56db21b2a21a60b2a1e15f61b428e00f613e93cd028ce763da971384f95 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def numDistinct(self, s, t):
        n, m = len(s), len(t)
        memo = {}

        def solve(i, j):
            if j == m:
                return 1
            if i == n:
                return 0
            if (i, j) in memo:
                return memo[(i, j)]

            notTake = solve(i + 1, j)
            take = 0

            if s[i] == t[j]:
                take = solve(i + 1, j + 1)

            memo[(i, j)] = take + notTake
            return memo[(i, j)]

        return solve(0, 0)
```
