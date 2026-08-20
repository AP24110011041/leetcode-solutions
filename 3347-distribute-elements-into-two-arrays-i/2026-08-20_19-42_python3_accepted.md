# 3347. Distribute Elements Into Two Arrays I
  
<br>**Problem:** https://leetcode.com/problems/distribute-elements-into-two-arrays-i/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Simulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-20 19:42 local time

**Runtime:** 0 ms (beats 100%)
**Memory:** 19.2 MB (beats 61.538500000000006%)


<!-- leetgit:submissionId=2114016247 codeHash=fa68f48c780f9a45c3908a9eef97e6ad327b2f7d5fd13acb465f6e0cc53e2430 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def resultArray(self, nums: List[int]) -> List[int]:
        arr1 = [nums[0]]
        arr2 = [nums[1]]

        for i in range(2, len(nums)):
            if arr1[-1] > arr2[-1]:
                arr1.append(nums[i])
            else:
                arr2.append(nums[i])

        return arr1 + arr2
```
