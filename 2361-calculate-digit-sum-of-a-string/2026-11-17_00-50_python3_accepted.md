# 2361. Calculate Digit Sum of a String
  
<br>**Problem:** https://leetcode.com/problems/calculate-digit-sum-of-a-string/<br>

**Difficulty:** Easy<br>
**Topics:** String, Simulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-17 00:50 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 51.79849999999999%)


<!-- leetgit:submissionId=2197558963 codeHash=40393d51e37a3057088a4b83b7b2283fa1b3b115f9f9658293fc374c2dd29c57 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def digitSum(self, s: str, k: int) -> str:
        while len(s) > k:
            s = ''.join(str(sum(map(int, g))) for g in batched(s, k))
        return s
```
