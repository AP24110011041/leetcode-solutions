# 4084. Maximize Sum of Squares of Digits
  
<br>**Problem:** https://leetcode.com/problems/maximize-sum-of-squares-of-digits/<br>

**Difficulty:** Medium<br>
**Topics:** Math, Greedy<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-14 19:22 local time

**Runtime:** 1145 ms (beats 24.40960000000002%)
**Memory:** 32.7 MB (beats 15.748199999999994%)


<!-- leetgit:submissionId=2172176757 codeHash=c87c2300b2f3c1a99eccb6c074013798cc6a7e491982bd677fa22af96174527e notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def maxSumOfSquares(self, num: int, sum: int) -> str:
        # Step 1: the biggest possible digit sum is 9 * num
        if sum > 9 * num:
            return ""

        ans = []

        # Step 2: fill every position from left to right
        for _ in range(num):
            digit = min(9, sum)   # take as much as we can, at most 9
            ans.append(str(digit))
            sum -= digit

        return "".join(ans) if sum == 0 else ""
```
