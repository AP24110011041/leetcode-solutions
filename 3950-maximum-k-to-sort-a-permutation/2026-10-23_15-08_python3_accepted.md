# 3950. Maximum K to Sort a Permutation
  
<br>**Problem:** https://leetcode.com/problems/maximum-k-to-sort-a-permutation/<br>

**Difficulty:** Medium<br>
**Topics:** Array, Bit Manipulation<br>
**Language:** python3<br>
**Status:** Accepted<br>
**Submitted:** 2026-10-23 15:08 local time

**Runtime:** 23 ms (beats 89.011%)
**Memory:** 31.9 MB (beats 45.05499999999999%)


<!-- leetgit:submissionId=2179535603 codeHash=3d5254eb7e98934ce347670337fe7e00f75bc772c755bc79ed9a0c80fcf59be7 notesHash=e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 -->

## Solution

```python3
class Solution:
    def sortPermutation(self, nums: List[int]) -> int:
        k = -1  # all bits set: nothing misplaced yet
        for i, x in enumerate(nums):
            if x != i:  # this number has to move
                k &= x  # keep only the bits it shares
                if not k:  # bits only disappear, so 0 stays 0
                    return 0
        return max(k, 0)  # -1 means nothing has to move
```
