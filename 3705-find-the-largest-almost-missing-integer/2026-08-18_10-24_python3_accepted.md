# 3705. Find the Largest Almost Missing Integer
  
<br>**Problem:** https://leetcode.com/problems/find-the-largest-almost-missing-integer/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Hash Table<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-18 10:24 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 93.8524%)


<!-- leetgit:submissionId=2110909403 codeHash=80fbe780929413c391a3880a87f7d3e1229310157270480b9f3837337a3eccc0 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def largestInteger(self, nums: List[int], k: int) -> int:
        n = len(nums)
        if k == n:
            return max(nums)
        if k == 1:
            arr = [i for i in nums if nums.count(i) == 1]
        else:
            arr = [i for i in (nums[0], nums[-1]) if nums.count(i) == 1]
        return max(arr) if arr else -1
```
