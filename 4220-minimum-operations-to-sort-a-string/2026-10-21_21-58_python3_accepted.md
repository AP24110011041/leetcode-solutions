# 4220. Minimum Operations to Sort a String
  
<br>**Problem:** https://leetcode.com/problems/minimum-operations-to-sort-a-string/<br>

**Difficulty:** Medium<br>
**Topics:** String<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-21 21:58 local time

**Runtime:** 359 ms (beats 15.907300000000141%)
**Memory:** 19.8 MB (beats 96.9697%)


<!-- leetgit:submissionId=2178130936 codeHash=4ca7d8400d7f534838fb6318810c289bcba039fd3f27982c227f17dcd09b0c90 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minOperations(self, s: str) -> int:
        n = len(s)
        mn = mx = s[0]
        isSorted = 1

        for i in range(1, n):
            if s[i] < s[i - 1]:
                isSorted = 0
            mn = min(mn, s[i])
            mx = max(mx, s[i])

        if isSorted: return 0
        if n == 2: return -1
        if s[0] == mn or s[-1] == mx:
            return 1

        for i in range(1, n - 1):
            if s[i] == mn or s[i] == mx:
                return 2

        return 3
```
