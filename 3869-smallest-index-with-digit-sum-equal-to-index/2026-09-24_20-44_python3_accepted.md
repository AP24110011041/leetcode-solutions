# 3869. Smallest Index With Digit Sum Equal to Index
  
<br>**Problem:** https://leetcode.com/problems/smallest-index-with-digit-sum-equal-to-index/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Math<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-09-24 20:44 local time

**Runtime:** 3 ms (beats 58.40559999999999%)
**Memory:** 19.1 MB (beats 93.2409%)


<!-- leetgit:submissionId=2152118187 codeHash=73ceaf386d51812de63d74607833ed95329fbb9e610b1ea5cdb660a0d34fc87e notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def smallestIndex(self, nums: List[int]) -> int:
        for i in range(len(nums)):
            if sum(map(int,str(nums[i]))) == i:
                return i
        return -1        
        
```
