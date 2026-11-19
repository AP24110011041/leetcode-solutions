# 2706. Minimum Score by Changing Two Elements
  
<br>**Problem:** https://leetcode.com/problems/minimum-score-by-changing-two-elements/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Greedy, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-19 23:58 local time

**Runtime:** 5 ms (beats 100%)
**Memory:** 31.3 MB (beats 26.126199999999976%)


<!-- leetgit:submissionId=2199552933 codeHash=02363b7a302a9c319fdcfaa08b79ba9dcd3a41fc07cba63d8d61d70186667ed5 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minimizeSum(self, nums: List[int]) -> int:
        small = nsmallest(3, nums)
        large = nlargest(3, nums)
        return min(large[0] - small[2], large[1] - small[1], large[2] - small[0])
```
