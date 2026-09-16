# 1725. Number of Sets of K Non-Overlapping Line Segments
  
<br>**Problem:** https://leetcode.com/problems/number-of-sets-of-k-non-overlapping-line-segments/<br>

**Difficulty:** Medium<br>
**Topics:** Math, Dynamic Programming, Combinatorics, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-16 19:39 local time

**Runtime:** 575 ms (beats 44.82710000000002%)
**Memory:** 42.9 MB (beats 44.8275%)


<!-- leetgit:submissionId=2143724553 codeHash=abedbb29680bf85f8a32ec8647a9e89b447edf1ec1e43517ce787f4c171800c9 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def numberOfSets(self, n, k):
        MOD = 10**9 + 7
        dp = [[0] * (k + 1) for _ in range(n)]

        # 0 segments → exactly 1 way
        for i in range(n):
            dp[i][0] = 1

        for j in range(1, k + 1):
            total = 0
            for i in range(1, n):
                # Add ways for j-1 segments
                total = (total + dp[i - 1][j - 1]) % MOD
                # Don't use i OR end a segment at i
                dp[i][j] = (dp[i - 1][j] + total) % MOD

        return dp[n - 1][k]
```
