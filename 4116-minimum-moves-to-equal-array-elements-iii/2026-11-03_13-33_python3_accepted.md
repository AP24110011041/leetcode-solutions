# 4116. Minimum Moves to Equal Array Elements III
  
<br>**Problem:** https://leetcode.com/problems/minimum-moves-to-equal-array-elements-iii/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-03 13:33 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 39.48709999999999%)


<!-- leetgit:submissionId=2188411916 codeHash=b47c8c320636ef92a347de5f728c82def5dc79ecb2db173a0bdb3a32fccbfcc3 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minMoves(self, nums: List[int]) -> int:
        mx = max(nums)
        res = 0
        for x in nums:
            res += mx - x
        return res
```
