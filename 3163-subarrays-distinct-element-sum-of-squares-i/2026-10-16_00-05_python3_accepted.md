# 3163. Subarrays Distinct Element Sum of Squares I
  
<br>**Problem:** https://leetcode.com/problems/subarrays-distinct-element-sum-of-squares-i/<br>

**Difficulty:** Easy<br>
**Topics:** Array, Hash Table, Binary Indexed Tree, Segment Tree<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-16 00:05 local time

**Runtime:** 34 ms (beats 50.46110000000004%)
**Memory:** 19.2 MB (beats 59.69230000000001%)


<!-- leetgit:submissionId=2173311783 codeHash=eecf39d42d77aacaa941c87d524f49f2f16790ba6b56a8ab8cc207b1e755b3f4 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def sumCounts(self, nums: List[int]) -> int:
        n, ans=len(nums), 0
        for l in range(n):
            seen, cnt=0, 0
            for x in nums[l:]:
                cnt+=((seen>>x)&1)==0
                seen|=(1<<x)
                ans+=cnt*cnt
        return ans
```
