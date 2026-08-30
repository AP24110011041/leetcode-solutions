# 2212. Removing Minimum and Maximum From Array
  
<br>**Problem:** https://leetcode.com/problems/removing-minimum-and-maximum-from-array/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Greedy<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-08-30 22:25 local time

**Runtime:** 87 ms (beats 5.136099999999979%)
**Memory:** 34 MB (beats 11.480400000000001%)


<!-- leetgit:submissionId=2125275650 codeHash=d3521248d29057d14f9cdf230fb8d9888aae7c3d7c5e86cb7525cc1306f58dc1 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def minimumDeletions(self, nums: List[int]) -> int:
        n = len(nums)
        left = 0
        right = 0
        
        for i in range(1, n):
            if nums[i] < nums[left]:
                left = i
                
            if nums[i] > nums[right]:
                right = i
                
        if left < right:
            left, right = right, left
            
        ans = n
        
        for i in range(n + 1):
            extra = 0
            
            if right >= i:
                extra = n - right
            elif left >= i:
                extra = n - left
                
            ans = min(ans, i + extra)
            
        return ans
        
```
