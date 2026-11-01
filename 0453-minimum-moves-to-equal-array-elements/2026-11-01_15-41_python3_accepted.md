# 453. Minimum Moves to Equal Array Elements
  
<br>**Problem:** https://leetcode.com/problems/minimum-moves-to-equal-array-elements/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-01 15:41 local time

**Runtime:** 4 ms (beats 68.67079999999999%)
**Memory:** 20.4 MB (beats 87.2362%)


<!-- leetgit:submissionId=2186889827 codeHash=946842072c9b12380d44300318c38c83cd62163d79f5fd10a17cee57dde453ce notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minMoves(self, nums):
        mn = min(nums)
        return sum(nums) - len(nums) * mn
```
