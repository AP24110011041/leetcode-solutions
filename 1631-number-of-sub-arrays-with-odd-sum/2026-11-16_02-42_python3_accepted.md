# 1631. Number of Sub-arrays With Odd Sum
  
<br>**Problem:** https://leetcode.com/problems/number-of-sub-arrays-with-odd-sum/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math, Dynamic Programming, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-16 02:42 local time

**Runtime:** 71 ms (beats 68.79000000000006%)
**Memory:** 24.5 MB (beats 49.68150000000001%)


<!-- leetgit:submissionId=2196895868 codeHash=a7bd4b445e0923b5adc03675e7c84a685fc09816d555eeb4c95068213049bfea notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def numOfSubarrays(self, arr: List[int]) -> int:
        MOD = 10**9 + 7
        odd = even = ans = 0

        for x in arr:
            if x % 2 == 1:
                odd, even = even + 1, odd
            else:
                even += 1
            ans = (ans + odd) % MOD

        return ans
        
```
