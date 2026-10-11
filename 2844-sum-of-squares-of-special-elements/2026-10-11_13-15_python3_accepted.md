# 2844. Sum of Squares of Special Elements 
  
<br>**Problem:** https://leetcode.com/problems/sum-of-squares-of-special-elements/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Enumeration<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-11 13:15 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.3 MB (beats 51.57889999999999%)


<!-- leetgit:submissionId=2169049839 codeHash=f7f3dd1d9d60f7c9bab8f6d5a1afed3027c3772b6e948b2b9d0943fb0ce75ac9 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def sumOfSquares(self, nums: List[int]) -> int:
        ans = 0
        n = len(nums)
        for i in range(1, n + 1):
            if n % i == 0:
                ans += nums[i - 1] * nums[i - 1]
        return ans
```
