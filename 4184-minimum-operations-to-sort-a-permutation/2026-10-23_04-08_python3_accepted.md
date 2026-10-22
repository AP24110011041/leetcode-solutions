# 4184. Minimum Operations to Sort a Permutation
  
<br>**Problem:** https://leetcode.com/problems/minimum-operations-to-sort-a-permutation/<br>

**Difficulty:** Medium<br>
**Topics:** Array<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-23 04:08 local time

**Runtime:** 170 ms (beats 14.771699999999985%)
**Memory:** 31.5 MB (beats 62.4999%)


<!-- leetgit:submissionId=2179220163 codeHash=4b6d013c260d46d74985a2f73ff5173d0d91800ee032a603efc54d11e1f68461 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minOperations(self, A: List[int]) -> int:
        n = len(A)
        asc = dsc = 1

        for i in range(1, n):
            asc += A[i] == (A[i - 1] + 1) % n
            dsc += A[i - 1] == (A[i] + 1) % n

        if asc == n:
            return 0 if not A[0] else min(n - A[0], A[0] + 2)

        if dsc == n:
            return min(n - A[-1], A[-1]) + 1

        return -1
```
