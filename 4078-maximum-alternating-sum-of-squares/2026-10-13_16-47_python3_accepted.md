# 4078. Maximum Alternating Sum of Squares
  
<br>**Problem:** https://leetcode.com/problems/maximum-alternating-sum-of-squares/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Greedy, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-13 16:47 local time

**Runtime:** 203 ms (beats 46.701700000000066%)
**Memory:** 32.4 MB (beats 92.85700000000001%)


<!-- leetgit:submissionId=2171111537 codeHash=528a8c6e5e665e0ee6df3cbf8a03506383e75fa316ecb84f1eb95366b285776f notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxAlternatingSum(self, nums):
        n = len(nums)

        for i in range(n):
            nums[i] *= nums[i]

        nums.sort()
        ans = 0

        for i in range(n // 2):
            ans -= nums[i]

        for i in range(n // 2, n):
            ans += nums[i]

        return ans
```
