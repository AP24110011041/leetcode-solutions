# 3831. Find X Value of Array I
  
<br>**Problem:** https://leetcode.com/problems/find-x-value-of-array-i/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math, Dynamic Programming<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-21 22:35 local time

**Runtime:** 403 ms (beats 32.89430000000002%)
**Memory:** 34.2 MB (beats 69.7368%)


<!-- leetgit:submissionId=2148904993 codeHash=09572d89fd28ab9e6d2d329805f40d47ff2d5487b7c1a9ba43749e7be23f4b8c notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def resultArray(self, A: List[int], k: int) -> List[int]:
        res = freq = [0] * k

        for n in A:
            n %= k
            cur = [0] * k
            cur[n] = 1

            for x, y in enumerate(freq):
                cur[x * n % k] += y

            freq = cur
            for x, y in enumerate(freq):
                res[x] += y

        return res
```
