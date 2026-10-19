# 2210. Find Target Indices After Sorting Array
  
<br>**Problem:** https://leetcode.com/problems/find-target-indices-after-sorting-array/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Binary Search, Sorting<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-19 19:34 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.4 MB (beats 24.19899999999999%)


<!-- leetgit:submissionId=2176278102 codeHash=f675fadf4ade9c22ed5898a04e85f71f2187e0470b817c04bef2020873fd787c notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def targetIndices(self, nums: List[int], target: int) -> List[int]:
        left = sum(x < target for x in nums)  # bisect_left: the values that come before the targets
        right = sum(x <= target for x in nums)  # bisect_right: the values up to the last target
        return list(range(left, right))
```
