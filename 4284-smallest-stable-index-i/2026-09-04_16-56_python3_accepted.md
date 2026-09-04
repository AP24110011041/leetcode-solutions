# 4284. Smallest Stable Index I
  
<br>**Problem:** https://leetcode.com/problems/smallest-stable-index-i/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-04 16:56 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 71.42859999999999%)


<!-- leetgit:submissionId=2130633104 codeHash=22e010f744f25f9a31e22ea2a0face50d6be44956f9388086e6c78d6bc957e62 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
suf = [0] * 100
class Solution:
    def firstStableIndex(self, A: list[int], k: int) -> int:
        n = len(A)        
        suf[n - 1] = A[-1]

        for i in range(n - 2, -1, -1):
            suf[i] = min(suf[i + 1], A[i])

        mx = 0
        for i, x in enumerate(A):
            mx = max(mx, x)
            if mx - suf[i] <= k:
                return i

        return -1
```
