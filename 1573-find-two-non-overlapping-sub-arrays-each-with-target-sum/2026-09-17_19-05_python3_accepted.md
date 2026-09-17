# 1573. Find Two Non-overlapping Sub-arrays Each With Target Sum
  
<br>**Problem:** https://leetcode.com/problems/find-two-non-overlapping-sub-arrays-each-with-target-sum/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Hash Table, Binary Search, Dynamic Programming, Sliding Window<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-17 19:05 local time

**Runtime:** 100 ms (beats 87.70929999999998%)
**Memory:** 31.2 MB (beats 66.48029999999999%)


<!-- leetgit:submissionId=2144753163 codeHash=c22b36ddaf87d6155bb89ca82687d0873a506825e223f4f71e12d71c01f9e224 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minSumOfLengths(self, A: List[int], k: int) -> int:
        n = len(A)
        res, tot, i = n + 1, 0, 0

        dp = [n] * (n + 1)

        for j in range(n):
            tot += A[j]

            while tot > k:
                tot -= A[i]
                i += 1
            dp[j + 1] = dp[j]

            if tot == k:
                res = min(res, j - i + 1 + dp[i])
                dp[j + 1] = min(dp[j], j - i + 1)

        return -1 if res == n + 1 else res
```
