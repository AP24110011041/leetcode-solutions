# 3644. Minimum Positive Sum Subarray 
  
<br>**Problem:** https://leetcode.com/problems/minimum-positive-sum-subarray/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Sliding Window, Prefix Sum<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-11-14 10:43 local time

**Runtime:** 50 ms (beats 40.72299999999999%)
**Memory:** 19.4 MB (beats 31.527099999999997%)


<!-- leetgit:submissionId=2195700914 codeHash=0404b938957e70d93f0d5e806faa01db25aee1286fbf03b354e9bc01913fe23e notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minimumSumSubarray(self, nums: List[int], l: int, r: int) -> int:

        n, mn = len(nums), inf
        acc = list(accumulate(nums, initial = 0))
        
        for left in range(n):
            for rght in range(left+1, n+1):
                
                sm, length = acc[rght] - acc[left], rght - left
                if l <= length <= r and 0 < sm < mn: mn = sm 
        
        return -1 if mn == inf else mn
```
